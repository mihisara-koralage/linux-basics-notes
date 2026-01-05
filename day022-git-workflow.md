# Day 22: Git & GitHub for DevOps
## What branches are
Think of branches as:
Parallel versions of your project
- main → stable, working code
- feature/* → experiments, new work

## Why DevOps uses branches
- Protects the main branch from breaking changes
- Allows safe experimentation without affecting production code
- Enables parallel work by multiple team members

## Commands I practiced
```
git branch
git checkout -b feature/day22-git-practice
nano day22-git-workflow.md
git add .
git commit -m "Add day 22 Git workflow notes"
git checkout main
git merge feature/day22-git-practice
git branch -d feature/day22-git-practice
```

## Short workflow explanation
Typical DevOps flow:
1. Create branch
2. Make changes
3. Test scripts
4. Merge into main
5. Deploy via CI/CD

