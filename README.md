# Daily Activity Tracker

This repository automatically tracks daily activity through automated commits. It's designed to maintain a consistent commit history for demonstration purposes.

## How It Works

- **Daily Commits**: GitHub Actions workflow runs daily at 5 AM UTC (10:30 AM IST)
- **Random Activity**: Each day generates 3-12 random commits with timestamps
- **Activity Log**: All commits are logged in `activity_log.txt`

## Workflows

### 🔄 Daily Random Commits (`main.yml`)
- **Schedule**: Daily at 5 AM UTC
- **Purpose**: Creates random commits to maintain activity
- **Trigger**: Also manually triggerable via `workflow_dispatch`

### 🔒 CodeQL Security Analysis (`codeql.yml`)  
- **Schedule**: Weekly on Mondays at 6 AM UTC
- **Purpose**: Analyzes GitHub Actions workflows for security issues
- **Language**: GitHub Actions only (no application code to scan)

### 🛡️ Security Scan (`security-scan.yml`)
- **Schedule**: Weekly on Sundays at 4 AM UTC  
- **Purpose**: Scans for configuration vulnerabilities and secrets
- **Tools**: Trivy scanner with focus on config and secret detection

### 🔧 Dependabot (`dependabot.yml`)
- **Schedule**: Weekly updates
- **Purpose**: Keeps GitHub Actions up to date
- **Scope**: Only GitHub Actions dependencies (no app dependencies)

## Repository Structure

```
├── .github/
│   ├── workflows/          # GitHub Actions workflows
│   ├── dependabot/         # Dependabot configuration  
│   └── WORKFLOW_TROUBLESHOOTING.md  # Troubleshooting guide
├── LICENSE                 # MIT License
├── README.md              # This file
└── activity_log.txt       # Daily commit log
```

## Troubleshooting

For workflow issues, see [`.github/WORKFLOW_TROUBLESHOOTING.md`](.github/WORKFLOW_TROUBLESHOOTING.md).

## Status

[![CodeQL Security Analysis](https://github.com/Rahuljoshi07/daily-activity/actions/workflows/codeql.yml/badge.svg)](https://github.com/Rahuljoshi07/daily-activity/actions/workflows/codeql.yml)
[![Security Scan](https://github.com/Rahuljoshi07/daily-activity/actions/workflows/security-scan.yml/badge.svg)](https://github.com/Rahuljoshi07/daily-activity/actions/workflows/security-scan.yml)
[![Daily Random Commits](https://github.com/Rahuljoshi07/daily-activity/actions/workflows/main.yml/badge.svg)](https://github.com/Rahuljoshi07/daily-activity/actions/workflows/main.yml)