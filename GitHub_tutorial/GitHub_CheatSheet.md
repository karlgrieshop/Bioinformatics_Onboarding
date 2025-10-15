# Git & GitHub Cheat Sheet

# Create new repo and add files
mkdir <project>
cd <project>
git init
touch <file1> <file2>
git add --all
git commit -m "Initial commit"

# Rename default branch to main (recommended)
git branch -M main

# Add remote and push to GitHub
git remote add origin git@github.com:<username>/<repo>.git
git push -u origin main

# Common workflow
git status
git add --all
git commit -m "Describe your changes"
git push origin main

# If push is rejected (remote has new commits)
git pull --rebase origin main
# ...resolve any conflicts...
git push origin main

# View history
git log

# Undo changes (dangerous: resets to specific commit)
git reset --hard <commit-hash>

# Safer: Checkout a previous commit and make it permanent

# Checkout a previous commit (detached HEAD state)
git checkout <commit-hash>

# If you want to keep this state, create a new branch from here
git checkout -b <new-branch-name>

# (Optional) Merge this branch into main later if desired
git checkout main
git merge <new-branch-name>
git push origin main
