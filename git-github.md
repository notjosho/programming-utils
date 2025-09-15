# Git & GitHub Basics

**Resources:**
- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Git Handbook](https://guides.github.com/introduction/git-handbook/)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)

## Initial Setup (not required if using ssh)
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## GitHub SSH Setup

**Resources:**
- [GitHub SSH Key Setup Guide - linux](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux)
- [SSH Key Generation Tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account#adding-a-new-ssh-key-to-your-account)

### Generate SSH Key
```bash
# Generate new SSH key (replace with your GitHub email)
ssh-keygen -t ed25519 -C "your.email@example.com"

# When prompted:
# - Press Enter to save in default location (~/.ssh/id_ed25519)
# - Enter a passphrase (recommended) or press Enter for no passphrase

# Start SSH agent and add your key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Add SSH Key to GitHub
```bash
# Copy your public key to clipboard
cat ~/.ssh/id_ed25519.pub

# Or use xclip if available:
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

**Then on GitHub:**
1. Go to GitHub → Settings → SSH and GPG keys
2. Click "New SSH key"
3. Paste your public key and give it a title
4. Click "Add SSH key"

### Test SSH Connection
```bash
# Test your SSH connection to GitHub
ssh -T git@github.com

# Should show: "Hi username! You've successfully authenticated..."
```

### Clone URLs
```bash
# HTTPS (requires username/password or token)
git clone https://github.com/username/repository.git

# SSH (requires SSH key setup)
git clone git@github.com:username/repository.git

# Change existing repo from HTTPS to SSH
git remote set-url origin git@github.com:username/repository.git
```

## Repository Operations
```bash
git init            # Initialize new repository
git clone url       # Clone remote repository
git status          # Check repository status
git log             # View commit history
```

## Working with Changes
```bash
git add file.txt    # Stage specific file
git add .           # Stage all changes
git commit -m "message"  # Commit changes
git diff            # Show unstaged changes
git diff --staged   # Show staged changes
```

## Branching

**Resources:**
- [Git Branching Guide](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
```bash
git branch          # List branches
git branch name     # Create new branch
git checkout name   # Switch to branch
git checkout -b name # Create and switch to branch
git merge branch    # Merge branch into current
git branch -d name  # Delete branch
```

## Remote Operations
```bash
git remote add origin url    # Add remote repository
git push origin main         # Push to remote
git pull origin main         # Pull from remote
git fetch                    # Fetch changes without merging
```

## Regular Development Workflow
```bash
# Start working on a new feature
git pull origin main              # Get latest changes from main
git checkout -b feature-branch    # Create and switch to new branch

# Make your changes, then:
git add .                         # Stage all changes
git commit -m "Add new feature"   # Commit with descriptive message
git push -u origin feature-branch # Push and set upstream tracking

# After first push, subsequent pushes:
git push                          # No need for -u flag anymore
```

## GitHub Workflow
```bash
# Fork repository on GitHub
git clone your-fork-url
git remote add upstream original-repo-url

# Create feature branch
git checkout -b feature-name

# Make changes, commit, push
git add .
git commit -m "Add feature"
git push -u origin feature-name

# Create Pull Request on GitHub
```

## Useful Git Commands
```bash
git stash           # Temporarily store changes
git stash pop       # Restore stashed changes
git reset --hard    # Reset to last commit (dangerous)
git revert commit   # Create new commit that undoes changes
git tag v1.0        # Create tag
```

## Common Workflow
```bash
# Daily workflow
git pull main        # Get latest changes
git checkout -b new-feature # Create feature branch
# Make changes
git add .
git commit -m "Implement new feature"
git push origin new-feature
# Create Pull Request on GitHub
```

## Handling Merge Conflicts
```bash
# When you encounter conflicts during pull/merge
git pull origin main
# Conflict appears: "CONFLICT (content): Merge conflict in file.py"

# 1. Check which files have conflicts
git status

# 2. Open conflicted files and look for conflict markers:
#    <<<<<<< HEAD
#    Your changes
#    =======
#    Their changes
#    >>>>>>> branch-name

# 3. Edit the file to resolve conflicts
# Remove conflict markers and keep the code you want

# 4. After resolving all conflicts:
git add .                    # Stage resolved files
git commit -m "Resolve merge conflicts"  # Commit the resolution
git push origin your-branch  # Push the resolved changes

# Alternative: Abort the merge if you want to start over
git merge --abort
```

## Conflict Prevention Workflow
```bash
# Before starting work, always sync with main
git checkout main
git pull origin main
git checkout your-branch
git merge main               # Merge latest main into your branch

# If conflicts occur, resolve them now before continuing work
# This prevents larger conflicts later
```

## Git Ignore
```bash
# Create .gitignore file
echo "*.log" >> .gitignore
echo "node_modules/" >> .gitignore
echo "__pycache__/" >> .gitignore
```

## Fixing Mistakes
```bash
git commit --amend -m "Fixed commit message"  # Fix last commit message
git reset HEAD~1            # Undo last commit (keep changes)
git checkout -- file.txt    # Discard changes to file
```

