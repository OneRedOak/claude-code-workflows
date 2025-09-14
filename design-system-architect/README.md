# Design System Architect Workflow

A Claude Code workflow that creates comprehensive design systems, component libraries, and style guides that integrate seamlessly with the [design-review workflow](../design-review/).

## Overview

The Design System Architect transforms design requirements into production-ready design systems by:

- **Analyzing brand guidelines** and creating comprehensive design tokens
- **Generating component libraries** with consistent patterns and standards
- **Creating style guides** that enforce design consistency
- **Building design documentation** that teams can follow
- **Ensuring accessibility compliance** from the ground up

This workflow complements the design-review workflow by creating the design standards that the review process validates against.

## How It Works

The Design System Architect workflow operates in five phases:

### Phase 1: Discovery & Analysis
- Analyzes existing brand assets, colors, typography, and design patterns
- Reviews competitor designs and industry best practices
- Identifies design gaps and opportunities for systematization

### Phase 2: Design Token Creation
- Generates comprehensive design tokens (colors, typography, spacing, shadows)
- Creates semantic naming conventions and token hierarchies
- Establishes design scales and proportional systems

### Phase 3: Component Architecture
- Designs reusable component specifications with props and variants
- Creates component hierarchies and composition patterns
- Defines interaction states and accessibility requirements

### Phase 4: Implementation Generation
- Generates production-ready CSS/SCSS/Tailwind configurations
- Creates React/Vue/Angular component boilerplates
- Produces Storybook stories and component documentation

### Phase 5: Documentation & Guidelines
- Creates comprehensive style guides and usage documentation
- Generates design system websites with interactive examples
- Produces team onboarding guides and contribution workflows

## Integration with Design Review

This workflow creates the foundation that the design-review workflow validates:

- **Design tokens** become the standards checked during review
- **Component specifications** define the patterns validated in code
- **Style guides** provide the criteria for design consistency checks
- **Documentation** serves as the reference for automated reviews

## Getting Started

### Prerequisites
- Claude Code with MCP support
- Access to design assets (Figma files, brand guidelines, etc.)
- Target framework/styling system (React, Vue, Tailwind, etc.)

### Installation
1. Clone this workflow to your `.claude/workflows/` directory
2. Configure the agent with your project's design requirements
3. Run the workflow to generate your design system

### Basic Usage

```bash
# Generate a complete design system
claude /design-system create --brand-guide="./assets/brand.pdf" --framework="react"

# Create component specifications
claude /design-system components --input="./designs/components/" --output="./src/components/"

# Generate design tokens
claude /design-system tokens --colors="./assets/colors.json" --output="./tokens/"

# Create style guide
claude /design-system docs --output="./design-system/"
```

## Agent Configuration

The workflow uses the `@design-system-architect` agent with these capabilities:

- **Brand Analysis**: Extracts design patterns from existing assets
- **Token Generation**: Creates comprehensive design token systems
- **Component Design**: Architects reusable component specifications
- **Code Generation**: Produces production-ready implementation files
- **Documentation**: Creates comprehensive design system documentation

## Examples

### Generating Design Tokens
```typescript
// Generated tokens/colors.ts
export const colors = {
  primary: {
    50: '#f0f9ff',
    100: '#e0f2fe',
    500: '#0ea5e9',
    900: '#0c4a6e',
  },
  semantic: {
    success: '#10b981',
    warning: '#f59e0b',
    error: '#ef4444',
  }
} as const;
```

### Component Specifications
```typescript
// Generated specs/Button.md
export interface ButtonProps {
  variant: 'primary' | 'secondary' | 'outline' | 'ghost';
  size: 'sm' | 'md' | 'lg';
  disabled?: boolean;
  loading?: boolean;
  children: React.ReactNode;
}
```

### Style Guide Generation
Creates comprehensive documentation including:
- Color palettes with accessibility ratings
- Typography scales and usage guidelines
- Component libraries with interactive examples
- Spacing and layout principles
- Animation and interaction guidelines

## Advanced Features

### Multi-Framework Support
- Generates design systems for React, Vue, Angular, and vanilla CSS
- Creates platform-specific implementations (iOS, Android, Flutter)
- Supports multiple styling approaches (CSS-in-JS, Tailwind, SCSS)

### Accessibility First
- Ensures WCAG 2.1 AA compliance by default
- Generates color contrast reports
- Creates accessible component patterns
- Includes screen reader and keyboard navigation support

### Design Tool Integration
- Imports from Figma, Sketch, Adobe XD
- Syncs with design token platforms (Tokens Studio, Style Dictionary)
- Exports to various formats (JSON, YAML, CSS Custom Properties)

## Workflow Templates

The workflow includes templates for common scenarios:

- **Startup Design System**: Rapid MVP design system creation
- **Enterprise Migration**: Converting legacy designs to modern systems
- **Multi-Brand System**: Creating flexible systems for multiple brands
- **Component Library**: Building comprehensive component libraries

## Resources

- [Design System Best Practices](./docs/best-practices.md)
- [Token Architecture Guide](./docs/tokens.md)
- [Component Design Patterns](./docs/components.md)
- [Implementation Examples](./examples/)

## Contributing

This workflow is part of the OneRedOak claude-code-workflows collection. To contribute:

1. Fork the repository
2. Create your improvements
3. Test with the design-review workflow
4. Submit a pull request

## License

MIT License - see [LICENSE](../LICENSE) for details.

---

*Part of the [Claude Code Workflows](https://github.com/OneRedOak/claude-code-workflows) collection by Patrick Ellis and the community.*