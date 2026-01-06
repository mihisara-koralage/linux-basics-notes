## What is CI?
CI means:

Automatically testing and validating code whenever someone pushes to Git.

Example:
- You push a script
- Pipeline runs:
  - Lint checks
  - Script tests
  - Safety checks

Purpose:
- Catch errors early
- Keep main branch stable

## What is CD?
CD means:

Automatically delivering code after CI passes.

Two types:
- Continuous Delivery → ready to deploy (manual approval)
- Continuous Deployment → auto-deploy to server

## What is a pipeline?
A pipeline is a sequence of steps:
1. Code pushed to GitHub
2. CI runs tests
3. Build or package
4. Deploy or prepare deployment

You already wrote:
- Scripts 
- Automation

Pipeline just runs them automatically.

## How your scripts fit into CI/CD
| Your Skill         | CI/CD Use              |
| ------------------ | ---------------------- |
| Shell scripts      | Pipeline steps         |
| Git branches       | Trigger pipelines      |
| Automation         | Setup jobs             |
| Monitoring scripts | Post-deployment checks |

## Why CI/CD matters in DevOps
- Faster and reliable releases – Automation reduces manual errors and speeds up deployments.
- Early bug detection – Continuous testing finds issues before they reach production.
- Consistent deployments – Same process every time across environments (dev, staging, prod).
