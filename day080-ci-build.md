# Day 080 – Build Docker Image using GitHub Actions

## 🎯 Objective

Create CI pipeline to build Docker image automatically.

---

## 🧠 CI Flow

Git push
↓
GitHub Actions triggered
↓
Docker image built

---

## 🛠 Workflow

Created:

.github/workflows/ci.yml

Pipeline:

- Checkout code
- Build Docker image

---

## 🛠 Commands

git add .
git commit -m "Add CI"
git push

---

## 🧠 Key Takeaway

CI pipeline automatically builds Docker image on git push.
