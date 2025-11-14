# Contributing to ChatGuard

Thank you for your interest in contributing! We welcome contributions from everyone.

## Code of Conduct

Be respectful and constructive in all interactions.

## How to Contribute

### Reporting Bugs

1. Check if the bug has already been reported in [Issues](https://github.com/sharkgitz/chatguard/issues)
2. If not, create a new issue with:
   - Clear title and description
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots/logs if applicable
   - Your environment (OS, Python version, Node version)

### Suggesting Features

1. Open an issue with the `enhancement` label
2. Describe the feature and why it would be useful
3. Provide examples of how it would be used

### Submitting Pull Requests

1. **Fork** the repository
2. **Create a branch** for your feature:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following the code style guidelines
4. **Test** your changes thoroughly
5. **Commit** with clear messages:
   ```bash
   git commit -m "Add: Brief description of changes"
   ```
6. **Push** to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
7. **Create a Pull Request** with:
   - Clear description of changes
   - Reference to related issues
   - Screenshots for UI changes

## Development Setup

```bash
# Backend
cd server
python -m venv venv
venv\Scripts\Activate
pip install -r requirements.txt

# Frontend
cd ../client
npm install
```

## Code Style

### Frontend (JavaScript/React)
- Use ESLint rules in `.eslintrc`
- Follow Airbnb style guide
- Use functional components with hooks
- Add comments for complex logic

### Backend (Python)
- Follow PEP 8 standards
- Use type hints where possible
- Write docstrings for functions
- Keep functions small and focused

## Testing

```bash
# Frontend
cd client
npm run lint

# Backend
cd server
python -m pytest  # if tests exist
```

## Commit Message Guidelines

```
<type>: <subject>

<body>

<footer>
```

**Types:**
- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation
- `style:` Code style changes
- `refactor:` Code refactoring
- `perf:` Performance improvements
- `test:` Adding tests

**Example:**
```
feat: Add message search functionality

Add ability to search through chat history with filters for date and sender.

Closes #123
```

## Review Process

1. Maintainers will review your PR
2. You may be asked to make changes
3. Once approved, your PR will be merged

## Questions?

Feel free to open an issue or reach out to the maintainers.

---

**Thank you for contributing to ChatGuard! 🎉**
