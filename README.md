# Core Cloud Workflow Node npm build

A GitHub Actions workflow for running npm build on Node.js projects to build Node applications.

## Overview

This workflow automates code building of Node.js projects within the core-cloud ecosystem.

## Features

- Automated npm builds

## Requirements

- Valid `package.json`, `package-lock.json` and valid `npm run build` command

## Usage

Reference this workflow in your GitHub Actions pipeline:

```yaml
jobs:
    build:
        uses: UKHomeOffice/core-cloud-workflow-node-npm-build
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `working_directory` | Directory to run npm build in | No | `.` |
| `node_version` | Node version | No | `24` |


## Outputs

| Output | Description |
|--------|-------------|
| `npm_build_exit_code` | Exit code from npm build (0 = success) |

## Support

For issues or questions:
- Create an issue in this repository
- Contact the Sauron Team on Slack: #core-cloud-team-sauron
- For tag enforcement questions, contact the Checkov workflow maintainers: #core-cloud-team-sauron

---

## Updated Repository Structure
```
core-cloud-workflow-node-npm-build/
.github
├── workflows
|    └── self-test.yaml
|
├── action.yaml
├── CODEOWNERS
├── README.md
└── tests
    ├── test-build-invalid/
    └── test-build-valid/
```

### 📘 SonarQube Configuration 
– `sonar-project.properties`

```
sonar.exclusions=tests/**

```

This removes all test fixtures and example IaC from SonarQube analysis, ensuring the Quality Gate only evaluates the actual workflow, action code, and scripts.

| Directory           | Purpose                                               | Excluded From SAST? |
| ------------------- | ----------------------------------------------------- | ------------------- |
| `tests/**`          | Local npm build test harness (intentionally invalid code) | ✅ Yes               |
| `action.yaml`       | Composite action logic                                | ❌ No                |

This setup ensures clean SAST results without blocking PRs due to intentionally invalid IaC.

## Contributing

Please read [CONTRIBUTING.md](./CONTRIBUTING.md)

## Security

Please read [SECURITY.md](./SECURITY.md)