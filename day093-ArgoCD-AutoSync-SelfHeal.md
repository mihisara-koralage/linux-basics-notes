# ArgoCD Auto Sync & Self Heal

Auto Sync:
Git changes → automatic deployment

Self Heal:
Manual changes → reverted to Git state

Config:
syncPolicy:
  automated:
    prune: true
    selfHeal: true

Git is source of truth
