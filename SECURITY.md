# Security Policy

## Protecting Personal Information

This repository has been sanitized to remove personal identifiable information (PII). When contributing to this project, please ensure:

### Configuration Files

1. **Never commit personal paths**: Use relative paths or environment variables instead of absolute paths that may contain usernames.
   - ❌ Bad: `C:\Users\YourName\projects\...`
   - ✅ Good: `${workspaceFolder}/...` or `/usr/bin/...`

2. **Avoid exposing registry/repository URLs**: Use placeholder examples instead of personal repository URLs.
   - ❌ Bad: `registry.gitlab.com/myusername/myproject`
   - ✅ Good: `registry.example.com/<your-org>/<your-project>`

3. **Remove timezone information**: Use UTC instead of local timezones that might reveal your location.
   - ❌ Bad: `BRT`, `EST`, `PST`
   - ✅ Good: `UTC`

### Git Configuration

4. **Use GitHub's anonymized email**: Configure git to use your GitHub no-reply email address.
   ```bash
   git config user.email "your-id+username@users.noreply.github.com"
   ```

5. **Review before committing**: Always review your changes before committing to ensure no personal information is included.
   ```bash
   git diff
   ```

### IDE Settings

The `.vscode/` directory is tracked in this repository with sanitized settings. When making changes:
- Use generic compiler paths that work across different environments
- Avoid committing workspace-specific settings
- Consider using `.vscode/*.code-workspace` in `.gitignore` for personal workspaces

## Reporting Security Issues

If you discover any personal information or security vulnerabilities in this repository, please report them by:
1. Opening a private security advisory on GitHub
2. Contacting the repository maintainers directly

Do not open public issues for security concerns.

## Best Practices

- Keep dependencies up to date
- Use the devcontainer for consistent development environments
- Regularly audit configuration files for sensitive information
- Use secrets management tools for any credentials needed in CI/CD
