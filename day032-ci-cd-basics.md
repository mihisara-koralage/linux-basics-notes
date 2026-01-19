# Day 32 – CI/CD Basics with GitHub Actions
## CI vs CD
CI – Continuous Integration
- Code pushed to GitHub
- Tests / checks run automatically

CD – Continuous Delivery/Deployment
- Code automatically prepared or deployed

Goal: Catch problems early, deploy safely
## What is GitHub Actions?
- GitHub’s built-in CI/CD tool
- Runs workflows on events (push, PR)
- Uses YAML files
## Workflow structure
```bash
.github/workflows/
```
## Your example
```bash
mkdir -p .github/workflows
nano .github/workflows/ci.yml
```
paste:
```yaml
name: Basic CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Run a simple script
        run: echo "CI pipeline running successfully!"
```
Push and Trigger CI:
```bash
git add .
git commit -m "Day 32: Add basic GitHub Actions CI pipeline"
git push
```
## Why CI matters
- CI runs automatically
- YAML defines pipelines
- GitHub Actions = free + powerful
- DevOps = automation, not manual work
