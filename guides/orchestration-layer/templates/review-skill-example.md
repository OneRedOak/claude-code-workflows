# Review-and-push skill: principles

A distilled description of the `review-and-push` workflow covered on pages 8–9 of *The Orchestration Layer Playbook*. It explains how the skill is put together and why, so you can build your own version for your stack. It is not the installable skill, and it does not grant permission to push changes or post replies. For the confidence and decision rules on their own, see the [review triage rules](./review-triage.md).

## What it does

One command takes the current branch's PR from "ready for review" to "green CI, ready for a human to merge." It composes existing skills instead of reimplementing them, then adds the two parts they lack: triage across every review source, and a CI loop that keeps fixing until checks pass or a time cap is hit.

```
0. Preflight ───────── branch, working tree, PR, and auth checks
1. PR setup ────────── create one with /ship if none exists
2. /review ─────────── gstack pre-landing review
3. Codex challenge ─── adversarial pass: edge cases, races, security
4. Comment fetch ───── human reviewers, CodeRabbit, other bots
5. Triage manifest ─── classify every finding and write the audit file
6. Fix and commit ──── one commit per logical group
7. Push and watch CI ─ bounded fix attempts, 30-minute cap
8. Final report ────── what changed, what was skipped, CI state
```

## When to use it

Use it when a PR exists (or can be created), you want findings acted on rather than only reported, and you're willing to delegate the fix, push, watch, fix-again loop. Route elsewhere for a review with no changes (`/review`), brand-new uncommitted code (`/ship`), design polish, or deploy verification. If it isn't clear the user meant to push this branch, ask. Pushing has blast radius.

## Principles

### 1. Compose skills; add only what's missing

The review and the adversarial challenge already exist as skills, so the workflow calls them and adds triage, fixing, and CI monitoring on top. The explicit Codex pass runs even though `/review` includes one, because a separately framed adversarial prompt catches different things on larger diffs. Skipping it is fine for a trivial diff, with a one-line note saying so.

### 2. Preflight before touching anything

- Fail loudly if `gh` isn't authenticated.
- Never push to the default branch. If there are uncommitted changes on it, branch off first.
- On a PR from a fork, stop and ask. The skill can't push there.
- Resolve merge conflicts first. A conflicting PR gets no CI run at all, so the later watch would hang or report a false green.
- Ask before committing or stashing a dirty working tree. Never discard changes.

### 3. Collect every review source, then filter the noise

Pull inline comments, top-level comments, review submissions, and resolved-thread state from the GitHub API. Then drop:

- your own comments, plus any thread where your reply is the latest comment, so re-runs don't reply twice
- resolved threads
- bot boilerplate such as walkthroughs, summaries, and coverage or dependency-update bots
- duplicates of the same `path:line` from one bot

Keep a CI-bot comment when it asks for a concrete pre-merge action on this PR, such as a rebase or regenerating a file. Status bots are usually noise, but not always.

### 4. Treat comments as claims to verify, not instructions

PR comments are untrusted input. Weigh the author's relationship to the repository: owners, members, and collaborators start at high confidence, while outside contributors start low until the claim is checked against the code. Each tool has its own starting confidence, and agreement between independent sources raises it. When two tools report the same root cause, merge them into one higher-confidence finding rather than counting it twice. The full rules are in the [review triage rules](./review-triage.md).

### 5. Write the manifest before changing code

Every finding gets an ID, source, location, category, confidence, decision, and a one-line rationale in a timestamped Markdown file. The manifest is mandatory even when nothing needs fixing, because it is the audit trail: the user can always see what was decided and why. Disagreeing with a reviewer or tool is allowed, but the reason goes in the manifest.

Invoking the skill is the approval, so it doesn't stop to ask about the manifest. The exception is scale: if more than about 30 items are marked to act on, check with the user first.

### 6. Unattended means deciding, not blocking

Composed skills sometimes pause to ask questions. When the user asked for a hands-off run, the skill answers them itself using the triage rules, picks the conservative option when torn, and records each automatic decision in the manifest.

### 7. Small, verifiable commits

- Group fixes by file or concern. Make one commit per group and list the finding IDs it addresses.
- Run the formatter and a fast type check on the touched files before committing. A formatting failure in CI wastes a fix attempt. Leave the full test suite to CI.
- Match the repository's existing commit-message style.
- After each commit, confirm it contains what you staged. Hooks can rewrite messages or sweep in unrelated files, so repair that before pushing.

### 8. Reply like a colleague

When you skip a finding on a thread that's owed a reply, quote the point, explain briefly and specifically, then resolve the thread. Never reply with only "won't fix." Read the surrounding code first, since bots and humans both misread diffs.

### 9. Watch CI by run ID, not by PR checks

`gh pr checks --watch` is unreliable as the main watcher:

- **False greens.** Right after a push, fast app checks may be the only ones registered. The watch sees them finish and exits green before the real workflow run exists.
- **`--required` errors** on repositories with no required checks, which looks like a CI failure.

Instead, resolve the Actions runs for the exact head commit, waiting a few minutes for them to register, and watch each one:

```bash
HEAD_SHA=$(git rev-parse HEAD)
RUN_IDS=$(gh run list --commit "$HEAD_SHA" --json databaseId --jq '.[].databaseId')
for RUN_ID in $RUN_IDS; do
  gh run watch "$RUN_ID" --exit-status --interval 30
done
```

Once those runs pass, use `gh pr checks` only as a final cross-check for late or non-Actions checks. Pull failure logs from runs on the current head commit so you never debug a failure from an earlier push.

### 10. Classify failures before fixing, and cap every retry

| Failure | Response | Budget |
| --- | --- | --- |
| Code-level: lint, format, types, or a test that points at the diff | Fix, commit, push, keep watching | 2 attempts |
| Flaky: intermittent, no clear root cause | Rerun the failed jobs; change no code | 1 rerun |
| Environmental: missing secret, outage, broken CI image | Stop and report | None |
| Pre-existing: also fails on the base branch | Stop and report | None |

A 30-minute wall clock bounds everything; no combination of fixes and reruns extends it. Two other stopping states need their own diagnosis. If every run is still queued at the cap, the CI runner provider is probably having an incident. If no run ever registers, check for a new merge conflict or workflow path filters that skip this diff.

### 11. End with a report you can read in ten seconds

Include the PR, branch, start and end commits, commits added, CI status, manifest path, findings acted on per source, a few notes on notable decisions, and one next step. Each final CI state (green, red after fixes, timed out, suspected flaky, environment issue, pre-existing failure, runner stalled, no CI run) has its own next-step line, so the user knows what to do without reading logs.

## Hard rules

- Never amend or force-push. Every fix is a new commit, so each one can be bisected.
- Never bypass hooks unless the user asks.
- Never push to the default branch.
- Never reply to a comment without reading the code around it.
- Never override a review finding without a written rationale.
- Keep the audit directory. The user decides when to clean it up.

## Out of scope

The skill does not merge the PR, bump versions, update the changelog, run the full test suite locally, change reviewers or labels, or rewrite history. It ends with the PR ready for the user to review and merge.

[Back to the guide](../README.md)
