# Workflow Troubleshooting Guide

## CodeQL Security Analysis

### Common Issues

#### Language Detection Errors
- **Issue**: CodeQL fails with "CodeQL detected code written in X, but not any written in Y"
- **Solution**: Ensure the `languages` configuration in `.github/workflows/codeql.yml` matches the actual code languages in the repository
- **This Repository**: Only contains GitHub Actions workflows, so only `actions` language should be configured

#### Timeout Issues
- **Issue**: Workflow runs indefinitely or times out
- **Solution**: Add `timeout-minutes` to job configuration
- **This Repository**: Set to 10 minutes for CodeQL analysis

### Current Configuration
This repository only contains:
- GitHub Actions workflow files (`.yml` in `.github/workflows/`)
- Text files (README.md, LICENSE, activity_log.txt)
- No Python, JavaScript, or other application code

Therefore, CodeQL is configured to analyze only:
- `languages: actions`

## Security Scan

### Configuration
- Uses Trivy scanner for configuration and secret scanning
- Scans GitHub Actions workflows for hardcoded tokens
- Pinned to specific version for stability

### Common Issues
- **Issue**: Scanner reports false positives
- **Solution**: Configure scanners parameter to focus on relevant scan types
- **This Repository**: Uses `scanners: 'config,secret'`

## Dependabot

### Configuration
Only monitors GitHub Actions dependencies since this repository contains no:
- npm packages (package.json)
- Python packages (requirements.txt, setup.py)
- Docker files

### Adding New Languages
If you add source code in new languages to this repository:

1. Update `.github/workflows/codeql.yml`:
   ```yaml
   languages: ['actions', 'python', 'javascript']  # Add as needed
   ```

2. Update `.github/dependabot/dependabot.yml`:
   ```yaml
   - package-ecosystem: "pip"  # For Python
   - package-ecosystem: "npm"  # For JavaScript
   ```

3. Update `.github/workflows/security-scan.yml` to include language-specific scans

## Testing Workflow Changes

To validate YAML syntax locally:
```bash
python3 -c "
import yaml
with open('.github/workflows/codeql.yml', 'r') as f:
    yaml.safe_load(f)
print('Valid YAML')
"
```

## Monitoring

- CodeQL runs weekly on Mondays at 6 AM UTC
- Security scan runs weekly on Sundays at 4 AM UTC  
- Dependabot checks weekly for GitHub Actions updates