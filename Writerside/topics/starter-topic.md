# Overview

|            |                                                                                                                                                                                        |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Platform   | <https://kurocado-studio.github.io/platform>                                                                                                                                           |
| Repository | <https://github.com/Kurocado-Studio/dev-ops>                                                                                                                                           |
| Main       | [![CI/CD Main Pipeline](https://github.com/Kurocado-Studio/dev-ops/actions/workflows/ci.push.yml/badge.svg)](https://github.com/Kurocado-Studio/dev-ops/actions/workflows/ci.push.yml) |

## Workflow Execution Flow Overview

This outlines how workflows get triggered and executed. The key steps:

- A consuming repository pushes code (e.g., push or pull_request event).
- It calls a reusable workflow from the central workflow repository.
- The central workflow executes defined CI/CD steps (build, test, deploy, etc.).
- The result (success/failure) is returned to the consuming repository.

```mermaid
sequenceDiagram
    Dev ->> Repo: Push Code / Create PR
    Repo ->> GitHub Actions: Triggers GitHub Actions Workflow
    GitHub Actions ->> Reusable Workflow Repo: Fetches Reusable Workflow
    Reusable Workflow Repo ->> GitHub Actions: Provides Workflow Logic
    GitHub Actions ->> GitHub Actions Runner: Executes Workflow within GitHub Context
    GitHub Actions Runner ->> GitHub Actions: Sends Execution Logs
    GitHub Actions ->> Repo: Reports Execution Status
    Repo ->> Dev: Notifies Success/Failure
```
