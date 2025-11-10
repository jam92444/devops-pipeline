


# 🚀 How to Create a CI/CD Workflow with GitHub Actions

This guide walks you through setting up a **GitHub Actions workflow** to automatically build, test, and deploy your project whenever changes are pushed to your repository.

---

## 🧠 What is GitHub Actions?

**GitHub Actions** is a CI/CD (Continuous Integration and Continuous Deployment) service built into GitHub.  
It allows you to automate tasks such as:
- Running tests on every push
- Building your code automatically
- Deploying your app to servers or hosting platforms

---

## 📂 1. Create the Workflow Directory

In your repository, create the following folder structure (if it doesn’t already exist):

```bash
.github/workflows/
````

All workflow files live in this directory.

---

## 📝 2. Create a Workflow File

Inside `.github/workflows/`, create a new file, for example:

```bash
.github/workflows/ci-cd-pipeline.yml
```

---

## ⚙️ 3. Define Your Workflow

Paste the following example into your workflow file:

```yaml
name: CI CD Pipeline

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v5

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

---

## 🧩 4. Workflow Explanation

| Section   | Purpose                                                         |
| --------- | --------------------------------------------------------------- |
| `name`    | The name of your workflow (appears in GitHub Actions tab).      |
| `on`      | Defines when the workflow should run (e.g., on push to `main`). |
| `jobs`    | A collection of tasks to execute.                               |
| `runs-on` | Specifies the operating system environment.                     |
| `steps`   | Lists individual actions or commands to perform.                |
| `uses`    | Refers to reusable actions from the GitHub Marketplace.         |
| `run`     | Executes shell commands directly in the workflow.               |

---

## ▶️ 5. Trigger the Workflow

Commit and push your changes to the `main` branch:

```bash
git add .
git commit -m "Add GitHub Actions CI/CD workflow"
git push origin main
```

Go to your **GitHub repository → Actions tab**, and you’ll see your workflow running automatically!

---

## 🧪 6. Verify the Workflow

* Check the **Actions** tab for workflow runs.
* Click on a run to see detailed logs.
* Ensure all steps (build, test, deploy, etc.) pass successfully.

---

## 🚀 7. (Optional) Add Deployment Step

You can extend your workflow to include deployment steps.
For example, to deploy to **GitHub Pages**, **AWS**, or **Vercel**, add another job after the tests.

Example snippet:

```yaml
  deploy:
    needs: build
    runs-on: ubuntu-latest

    steps:
      - name: Deploy to Production
        run: echo "Deploying app..."
```

---

## 💡 Tips

* Use **secrets** for sensitive data (API keys, tokens) → set them in **Settings → Secrets and variables → Actions**.
* Keep workflows modular — one for testing, one for deployment, etc.
* Review the [GitHub Actions Marketplace](https://github.com/marketplace?type=actions) for pre-built actions.

---

## ✅ Summary

You’ve now:

1. Created a workflow directory and file.
2. Defined a build and test pipeline.
3. Learned how to trigger and monitor workflow runs.
4. (Optionally) added deployment automation.

---
