# Quick Guide: Using Git and GitHub

If you followed the main tutorial, you **initially cloned your fork of the Bioinformatics_Onboarding repo using the HTTPS link**. *But now* that you have set up your SSH key, you can (and should) use the SSH link for all future clones and remote operations for easier authentication — no more typing your GitHub password (disabled) or storing a personal access token somewhere!

To check your current remote:
```bash
git remote -v
```
You may see something like:
```
origin  https://github.com/<your-username>/Bioinformatics_Onboarding.git (fetch)
origin  https://github.com/<your-username>/Bioinformatics_Onboarding.git (push)
```

**To switch your remote to SSH (recommended for smoother authentication):**
```bash
git remote set-url origin git@github.com:<your-username>/Bioinformatics_Onboarding.git
```
*Replace `<your-username>` as appropriate. After this, all pushes and pulls will use your SSH key.*

*For any future clones, always use the SSH link (starts with `git@github.com:`) instead of HTTPS so that you don't have to switch the remote later.*

---

## 1. Check status and view files
```bash
git status
ls
```

## 2. Stage changes (additions, deletions, modifications)
```bash
git add --all
```

## 3. Commit your changes with a message
```bash
git commit -m "your descriptive commit message"
```

## 4. View commit history
```bash
git log
```

## 5. Push your local commits to GitHub
```bash
git push origin main
```
*If rejected, remote has changes you don't have.*

## (Only if step 5 was rejected, two alternatives) 
### 5.1. Force push (overwrites remote history; use with caution)
```bash
git push --force origin main
```

#### 5.2.1. Pull remote changes (rebase recommended)
```bash
git pull --rebase origin main
```

#### 5.2.2. Final push to GitHub (now that branches are synchronized)
```bash
git push origin main
```

**Done! Verify that your local and remote repositories are now synchronized.**

---

## Bonus: Practice Undoing a Mistake with Git

Let's practice making a mistake (e.g., deleting a file), committing the change, and then recovering the file by resetting to a previous commit.

### 6. Delete a file (simulate a mistake)
```bash
rm <filename>
ls
```

### 7. Stage and commit the deletion
```bash
git add --all
git commit -m "accidentally deleted <filename>"
```

### 8. View commit history and find the previous commit hash
```bash
git log
```
*Copy the hash of the commit just before your mistake.*

### 9.1. Reset your repository to the previous commit (dangerous: this will discard all changes after that commit)
```bash
git reset --hard <previous-commit-hash>
```

#### 9.2. Confirm the file is restored
```bash
ls
```

### 10.1 Alternatively, for a safer approach, you can check out the file from a previous commit without resetting the whole repo:
```bash
git checkout <previous-commit-hash> -- <filename>
```

#### 10.2 If you want to keep this state, create a new branch from here:
```bash
git checkout -b <new-branch-name>
```

# (Optional) Merge this branch into main later if desired
```bash
git checkout main
git merge <new-branch-name>
git push origin main
```

---

Now you know how to recover from mistakes using Git!

*Quick guide in GitHub_tutorial/GitHub_CheatSheet.md*

**Remember:**  
- Now that you have an SSH key on your local machine, always use the SSH link (`git@github.com:...`) for cloning to your local machine for a smoother workflow.