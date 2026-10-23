# Detect Large Files Action 🚀

A custom GitHub Action to scan your repository workspace for large files and automatically fail the CI/CD pipeline if any files exceed a specified size limit. 

In modern DevOps and Cloud Engineering, keeping repositories lightweight is crucial. This action helps enforce repository hygiene by preventing large binaries, database dumps, or unwanted large assets from bloating your Git history.

## 📋 Prerequisites

Before running this action, you **must** use the `actions/checkout` step. This ensures that your repository's code is actually downloaded into the GitHub runner's workspace for the `find` command to scan.

## 💻 Usage

To use this action in your workflow, add it as a step in your `.github/workflows/` YAML file. 

By default, the action checks for files larger than `500k`.

```yaml
name: Enforce Repo Hygiene
on: [push, pull_request]

jobs:
  large-files-check:
    runs-on: ubuntu-latest
    steps:
      # Step 1: Checkout the code (Required)
      - name: Checkout code
        uses: actions/checkout@v4

      # Step 2: Run the custom action (Default 500k)
      - name: Run large file check
        uses: DevSecOps-Automation-Projects/action-detect-large-files@v2
