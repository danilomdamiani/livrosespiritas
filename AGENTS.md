# Agent Instructions

Guidelines for AI agents working in this repository.

## Build/Lint/Test Commands

**Always run these commands after making changes:**

| Task | Command | Notes |
|------|---------|-------|
| Build | `npm run build` or `cargo build` or `make` | Use the appropriate tool for this project |
| Lint | `npm run lint` or `cargo clippy` or `ruff check .` | Fix all lint errors before committing |
| Type Check | `npm run typecheck` or `mypy .` or `cargo check` | Ensure type safety |
| Test All | `npm test` or `cargo test` or `pytest` | Run full test suite |
| Test Single | `npm test -- <test-name>` or `cargo test <test-name>` or `pytest -k <test-name>` | Run specific test by name or pattern |

**When no explicit command is found:**
- Look in `package.json` scripts for npm projects
- Check `Cargo.toml` for Rust projects
- Check `pyproject.toml` or `setup.py` for Python projects
- Check `Makefile` for make-based projects
- Check `.github/workflows/` for CI configuration

**Test Command Examples by Language:**

```bash
# JavaScript/TypeScript (Jest)
npm test -- MyComponent.test.tsx

# Python (pytest)
pytest tests/test_my_module.py::test_function_name

# Rust
cargo test test_function_name

# Go
go test -run TestFunctionName ./pkg/mypackage
```

## Code Style Guidelines

### Imports & Organization
- Group imports: stdlib → third-party → local modules
- Sort imports alphabetically within groups
- Use absolute imports for cross-module references
- Avoid circular dependencies

### Formatting
- Use the project's configured formatter (Prettier, rustfmt, Black, etc.)
- Match existing indentation (spaces vs tabs, width)
- Keep line length reasonable (80-120 characters)
- Use trailing commas where the project does

### Naming Conventions
- **Variables/Functions**: `camelCase` (JS/TS), `snake_case` (Python/Rust)
- **Constants**: `UPPER_SNAKE_CASE`
- **Classes/Types**: `PascalCase`
- **Private members**: `_prefix` or `m_` prefix as per project convention

### Types & Documentation
- Add types to all function signatures (TypeScript, Python type hints, etc.)
- Document public APIs with docstrings/comments
- Keep functions small and focused (<50 lines)
- Avoid `any` or `unknown` without justification

### Error Handling
- Use explicit error types, not generic exceptions
- Handle errors at appropriate abstraction levels
- Log errors with context (but never log secrets/PII)
- Prefer early returns to reduce nesting

### Logging & Debugging
- Use appropriate log levels (debug, info, warn, error)
- Include contextual information in log messages
- Never log sensitive data (passwords, tokens, PII)
- Remove or disable debug logging before committing

### Testing
- Write tests for new functionality
- Use descriptive test names explaining the "why"
- Follow Arrange-Act-Assert pattern
- Mock external dependencies appropriately

### Security
- Never commit secrets, API keys, or credentials
- Validate all inputs at system boundaries
- Use parameterized queries for database access
- Sanitize user-generated content

## General Principles

1. **Follow existing patterns** - Match the style of surrounding code
2. **Be conservative** - Don't introduce new dependencies without need
3. **Write clear code** - Optimize for readability over cleverness
4. **Test your changes** - Verify manually if automated tests don't exist
5. **Document decisions** - Add comments for non-obvious logic
6. **Commit hygiene** - Make focused, atomic commits with clear messages

## Project-Specific Notes

- **Language/Framework**: Static HTML/CSS/JavaScript (vanilla)
- **Project Type**: Single-page website for bookstore landing page
- **No build system**: Direct file editing, no compilation step
- **No tests configured**: Manual testing by opening index.html in browser
- **Deployment**: Static file hosting (upload HTML file directly)

## HTML/CSS Specific Guidelines

- Use semantic HTML5 elements (`<header>`, `<section>`, `<footer>`)
- Maintain mobile-first responsive design approach
- Use CSS custom properties for theme colors and consistent values
- Keep CSS organized by component/section
- Ensure accessibility with proper ARIA labels and alt text
- Test on multiple browsers and screen sizes

## Code Review Checklist

Before submitting changes, verify:
- [ ] All tests pass (run full test suite)
- [ ] Lint checks pass with no errors
- [ ] Type checking passes (if applicable)
- [ ] Code follows project conventions
- [ ] Documentation updated (if needed)
- [ ] No secrets or credentials committed
- [ ] Changes are focused and atomic
- [ ] Edge cases are handled appropriately

## Communication Guidelines

### Commit Messages
- Use present tense ("Add feature" not "Added feature")
- Use imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit first line to 72 characters or less
- Reference issues and pull requests liberally after first line

### Code Comments
- Explain why, not what (code should explain itself)
- Keep comments current - update when code changes
- Remove commented-out code before committing
- Use TODO comments sparingly and track them in issues
