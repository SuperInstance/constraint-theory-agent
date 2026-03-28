# Contributing to Constraint Theory Implementation Agent

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Making Changes](#making-changes)
- [Testing](#testing)
- [Pull Request Process](#pull-request-process)
- [Style Guidelines](#style-guidelines)

## Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). By participating, you are expected to uphold this code.

## Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/YOUR_USERNAME/constraint-theory-agent.git`
3. Create a branch: `git checkout -b feature/my-feature`

## Development Setup

### Prerequisites

- Node.js 18+ (20 recommended)
- npm 9+
- TypeScript 5+

### Installation

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/constraint-theory-agent.git
cd constraint-theory-agent

# Install dependencies
npm install

# Build the project
npm run build

# Verify installation
npm test
```

### Project Structure

```
constraint-theory-agent/
├── packages/
│   ├── core/           # Core agent logic
│   ├── analyzer/       # Code analysis engine
│   ├── refactorer/     # Code transformation engine
│   ├── explainer/      # Human-readable explanations
│   └── cli/            # Command-line interface
├── prompts/
│   ├── audit.md        # Code audit prompt
│   ├── refactor.md     # Refactoring prompt
│   └── explain.md      # Explanation prompt
├── extensions/
│   ├── typescript/     # TypeScript-specific patterns
│   ├── python/         # Python-specific patterns
│   ├── rust/           # Rust-specific patterns
│   └── cpp/            # C++-specific patterns
└── templates/
    ├── game-dev/       # Game dev refactoring templates
    ├── scientific/     # Scientific computing templates
    └── cad/            # CAD/engineering templates
```

## Making Changes

### Branch Naming

- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation changes
- `refactor/` - Code refactoring
- `test/` - Adding or modifying tests

### Commit Messages

Follow conventional commits:

```
feat: add new floating-point pattern detector
fix: correct analysis of NaN comparisons
docs: update installation instructions
test: add tests for IEEE 754 edge cases
refactor: simplify pattern matching logic
```

## Testing

### Running Tests

```bash
# Run all tests
npm test

# Run with coverage
npm run test:coverage

# Run specific test file
npm test -- packages/analyzer/tests/drift-detector.test.ts
```

### Writing Tests

- Place tests in the `tests/` directory alongside source files
- Name test files with `.test.ts` suffix
- Use descriptive test function names

```typescript
describe('FloatingPointDetector', () => {
  it('should detect cumulative error in loop', () => {
    const code = `
      for (let i = 0; i < 1000; i++) {
        total += 0.1;
      }
    `;
    const issues = detector.analyze(code);
    expect(issues).toContainEqual(
      expect.objectContaining({ type: 'cumulative-error' })
    );
  });
});
```

## Pull Request Process

1. **Update Documentation**: Ensure README.md and JSDoc comments are updated
2. **Add Tests**: New features need tests
3. **Run Tests**: All tests must pass
4. **Check Examples**: Ensure example scripts still work
5. **Submit PR**: Use the PR template

### PR Checklist

- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex logic
- [ ] Documentation updated
- [ ] Tests added and passing
- [ ] No new warnings introduced

## Style Guidelines

### TypeScript Code

- Follow strict mode
- Use type hints for all function parameters and returns
- Write JSDoc comments for public APIs

```typescript
/**
 * Analyzes code for floating-point drift patterns.
 * 
 * @param code - The source code to analyze
 * @param options - Analysis options
 * @returns Array of detected issues with locations
 */
function analyzeDriftPatterns(
  code: string,
  options: AnalysisOptions
): DriftIssue[] {
  // Implementation
}
```

### Adding New Pattern Detectors

1. Create detector in `packages/analyzer/patterns/`
2. Add corresponding tests
3. Register in `packages/analyzer/index.ts`
4. Add documentation in README.md

## Questions?

- Open a [Discussion](https://github.com/SuperInstance/constraint-theory-agent/discussions)
- Check existing [Issues](https://github.com/SuperInstance/constraint-theory-agent/issues)

Thank you for contributing!
