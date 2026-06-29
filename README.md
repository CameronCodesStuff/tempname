# Git Push from CMD (Windows) — Upload Only a Selected Folder

This guide shows how to upload a **specific folder** to a GitHub repository using **Command Prompt (CMD)**.

> **Note:** Git tracks files inside a repository. If you only want one folder, either:
> - Create a new repository containing only that folder (recommended), or
> - Use Git from the folder you want to upload.

---

# Step 1: Open Command Prompt

Press:

```text
Win + R
```

Type:

```text
cmd
```

Press **Enter**.

---

# Step 2: Navigate to Your Folder

Use the `cd` command.

Example:

```cmd
cd C:\Users\YourName\Documents\MyProject
```

Example with spaces:

```cmd
cd "C:\Users\YourName\Desktop\My Folder"
```

Verify you're in the correct location:

```cmd
dir
```

---

# Step 3: Initialize Git

If the folder is **not already a Git repository**:

```cmd
git init
```

---

# Step 4: Connect to GitHub

Add your GitHub repository as the remote.

HTTPS:

```cmd
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

SSH:

```cmd
git remote add origin git@github.com:USERNAME/REPOSITORY.git
```

Check it:

```cmd
git remote -v
```

---

# Step 5: Stage Only the Files You Want

## Option A — Stage Everything in This Folder

```cmd
git add .
```

---

## Option B — Stage One Specific Folder

Example:

```cmd
git add Assets/
```

or

```cmd
git add src/
```

You can stage multiple folders:

```cmd
git add Assets src Docs
```

---

## Option C — Stage Individual Files

```cmd
git add README.md
git add main.py
```

---

# Step 6: Commit

```cmd
git commit -m "Initial upload"
```

Example:

```cmd
git commit -m "Added Assets folder"
```

---

# Step 7: Set the Branch

For modern Git:

```cmd
git branch -M main
```

---

# Step 8: Push to GitHub

First push:

```cmd
git push -u origin main
```

Future pushes:

```cmd
git push
```

---

# Uploading Only One Folder from a Larger Project

Suppose your project looks like this:

```text
Project/
│
├── Assets/
├── Scripts/
├── Docs/
└── README.md
```

To upload **only `Assets`**:

```cmd
git add Assets/
git commit -m "Upload Assets folder"
git push
```

Only the staged changes in `Assets` will be included in that commit.

---

# Check What Will Be Committed

See staged files:

```cmd
git status
```

Example output:

```text
Changes to be committed:

    new file: Assets/logo.png
    new file: Assets/config.json
```

---

# Useful Commands

## View Status

```cmd
git status
```

---

## View Commit History

```cmd
git log --oneline
```

---

## See Remote Repository

```cmd
git remote -v
```

---

## Remove a File from the Staging Area

```cmd
git restore --staged filename
```

Example:

```cmd
git restore --staged Assets/logo.png
```

---

## Stage Everything Again

```cmd
git add .
```

---

## Push New Changes

```cmd
git add .
git commit -m "Updated files"
git push
```

---

# Complete Example

```cmd
cd "C:\Projects\MyFolder"

git init

git remote add origin https://github.com/USERNAME/REPOSITORY.git

git add Assets/

git commit -m "Upload Assets folder"

git branch -M main

git push -u origin main
```

---

# Common Errors

## `fatal: not a git repository`

Run:

```cmd
git init
```

or navigate to the correct folder.

---

## `remote origin already exists`

Remove it:

```cmd
git remote remove origin
```

Then add it again:

```cmd
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

---

## `nothing to commit`

Check:

```cmd
git status
```

If nothing is staged, add files:

```cmd
git add Assets/
```

or

```cmd
git add .
```

---

## Authentication Failed

If using HTTPS:

- Make sure you're signed into GitHub.
- Use a Personal Access Token (PAT) instead of your password if prompted.

If using SSH:

```cmd
ssh -T git@github.com
```

---

# Quick Reference

```cmd
cd "C:\Path\To\Folder"

git init

git remote add origin https://github.com/USERNAME/REPOSITORY.git

git add Assets/

git commit -m "Upload Assets"

git branch -M main

git push -u origin main
```
