# 🚀 Daily Commit

> Automate your GitHub contribution streak using GitHub Actions.

![GitHub last commit](https://img.shields.io/github/last-commit/way2masoom/daily-commit)
![GitHub repo size](https://img.shields.io/github/repo-size/way2masoom/daily-commit)
![GitHub stars](https://img.shields.io/github/stars/way2masoom/daily-commit?style=social)

---

## 📖 About

This repository uses **GitHub Actions** to automatically create a commit every day.

The workflow updates a file called `activity.txt` with the current timestamp, commits the changes, and pushes them back to the repository.

This helps maintain a consistent GitHub contribution graph while also demonstrating workflow automation using GitHub Actions.

---

# ⚙️ Workflow Overview

## Process

### 1️⃣ Checkout Repository

The workflow starts by cloning the repository to the GitHub Actions runner.

### 2️⃣ Update Activity File

The workflow updates:

```text
activity.txt
```

with the current date and time.

Example:

```text
Last update: Sat Jun 13 01:20:33 UTC 2026
```

### 3️⃣ Git Configuration

GitHub Actions configures Git credentials automatically.

```bash
git config user.name "github-actions"
git config user.email "github-actions@github.com"
```

### 4️⃣ Commit Changes

The updated file is staged and committed.

```bash
git add .
git commit -m "Daily commit"
```

### 5️⃣ Push Changes

The commit is pushed back to the repository automatically.

```bash
git push
```

---

# 📂 Repository Structure

```text
daily-commit
│
├── .github
│   └── workflows
│       └── daily-commit.yml
│
├── activity.txt
│
└── README.md
```

---

# 📄 File Details

## activity.txt

This file stores the latest workflow execution timestamp.

### Example Output

```text
Last update: Sat Jun 13 01:20:33 UTC 2026
```

After the next run:

```text
Last update: Sun Jun 14 01:20:33 UTC 2026
```

---

# 🚀 How To Implement In Your Own Repository

### Step 1: Create a Repository

Create a repository named:

```text
daily-commit
```

### Step 2: Create activity.txt

Create:

```text
activity.txt
```

Add any content and commit it.

### Step 3: Create Workflow File

Create:

```text
.github/workflows/daily-commit.yml
```

Paste:

```yaml
name: Daily Commit

on:
  schedule:
    - cron: '30 18 * * *'
  workflow_dispatch:

jobs:
  commit:
    runs-on: ubuntu-latest

    permissions:
      contents: write

    steps:
      - uses: actions/checkout@v4

      - name: Update file
        run: |
          echo "Last update: $(date)" > activity.txt

      - name: Commit changes
        run: |
          git config user.name "github-actions"
          git config user.email "github-actions@github.com"

          git add .
          git commit -m "Daily commit $(date)" || exit 0
          git push
```

### Step 4: Enable Workflow Permissions

Navigate to:

```text
Settings
 └── Actions
      └── General
```

Enable:

```text
Read and write permissions
```

Save changes.

### Step 5: Run The Workflow

Navigate to:

```text
Actions
 └── Daily Commit
      └── Run Workflow
```

A successful run will automatically create a commit.

---

# 🎯 Why This Project Exists

* Learn GitHub Actions
* Explore workflow automation
* Understand CI/CD basics
* Maintain GitHub consistency
* Experiment with scheduled workflows

---

# 👨‍💻 Author

**MD Masoom Alam**

💻 Web Developer
🎨 UI/UX Designer
🤖 Exploring AI/ML

GitHub: https://github.com/way2masoom

---

# ❤️ Made With Love

Made with ❤️ by **MD Masoom Alam**

If this project helped you, consider giving it a ⭐.

> **"Consistency is more important than perfection."** 🚀
