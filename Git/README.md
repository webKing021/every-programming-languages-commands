# Git Commands Reference

## Setup and Configuration

```bash
# Set your username
git config --global user.name "Your Name"

# Set your email
git config --global user.email "your.email@example.com"

# Set default editor
git config --global core.editor "code --wait"

# View all configurations
git config --list

# Set up SSH key
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"
```

## Repository Operations

```bash
# Initialize a new repository
git init

# Clone a repository
git clone https://github.com/username/repository.git

# Clone a specific branch
git clone -b branch-name https://github.com/username/repository.git

# Clone to a specific directory
git clone https://github.com/username/repository.git directory-name
```

## Basic Commands

```bash
# Check status of working directory
git status

# Add files to staging area
git add filename

# Add all files to staging area
git add .

# Commit changes
git commit -m "Commit message"

# Add and commit in one command
git commit -am "Commit message"

# Amend the last commit
git commit --amend -m "New commit message"
```

## Branching and Merging

```bash
# List all branches
git branch

# List all remote branches
git branch -r

# List all branches (local and remote)
git branch -a

# Create a new branch
git branch branch-name

# Switch to a branch
git checkout branch-name

# Create and switch to a new branch
git checkout -b branch-name

# Delete a branch
git branch -d branch-name

# Force delete a branch
git branch -D branch-name

# Merge a branch into current branch
git merge branch-name

# Merge with no fast forward
git merge --no-ff branch-name
```

## Remote Operations

```bash
# Add a remote repository
git remote add origin https://github.com/username/repository.git

# View remote repositories
git remote -v

# Remove a remote
git remote remove origin

# Fetch from remote
git fetch origin

# Pull from remote (fetch + merge)
git pull origin branch-name

# Pull with rebase
git pull --rebase origin branch-name

# Push to remote
git push origin branch-name

# Push and set upstream
git push -u origin branch-name

# Force push
git push -f origin branch-name
```

## Viewing Changes

```bash
# View commit history
git log

# View commit history with graph
git log --graph --oneline --decorate

# View changes in working directory
git diff

# View changes in staging area
git diff --staged

# View changes between branches
git diff branch1..branch2

# View changes in a file
git diff -- filename
```

## Undoing Changes

```bash
# Discard changes in working directory
git checkout -- filename

# Unstage a file
git reset HEAD filename

# Reset to a specific commit (soft - keep changes staged)
git reset --soft commit-hash

# Reset to a specific commit (mixed - default, keep changes unstaged)
git reset commit-hash

# Reset to a specific commit (hard - discard all changes)
git reset --hard commit-hash

# Revert a commit
git revert commit-hash
```

## Stashing

```bash
# Stash changes
git stash

# Stash with a message
git stash save "Stash message"

# List stashes
git stash list

# Apply most recent stash
git stash apply

# Apply specific stash
git stash apply stash@{n}

# Apply and remove most recent stash
git stash pop

# Remove most recent stash
git stash drop

# Remove specific stash
git stash drop stash@{n}

# Clear all stashes
git stash clear
```

## Tagging

```bash
# List all tags
git tag

# Create a lightweight tag
git tag tag-name

# Create an annotated tag
git tag -a tag-name -m "Tag message"

# Tag a specific commit
git tag -a tag-name commit-hash -m "Tag message"

# Push tags to remote
git push origin --tags

# Delete a tag
git tag -d tag-name

# Delete a remote tag
git push origin --delete tag-name
```

## Advanced Operations

```bash
# Interactive rebase
git rebase -i HEAD~n

# Cherry-pick a commit
git cherry-pick commit-hash

# Squash last n commits
git reset --soft HEAD~n && git commit

# Clean untracked files
git clean -f

# Clean untracked files and directories
git clean -fd

# Show who changed each line in a file
git blame filename

# Search commit history
git log -S"search term"

# Search commit messages
git log --grep="search term"
```

## Git Submodules

```bash
# Add a submodule
git submodule add https://github.com/username/repository.git path/to/submodule

# Initialize submodules
git submodule init

# Update submodules
git submodule update

# Clone repository with submodules
git clone --recurse-submodules https://github.com/username/repository.git
```

## Git Hooks

```bash
# Location of hooks
cd .git/hooks

# Make a hook executable
chmod +x pre-commit
```

## Git LFS (Large File Storage)

```bash
# Install Git LFS
git lfs install

# Track large files
git lfs track "*.psd"

# List tracked files
git lfs ls-files
```

## Git Flow

```bash
# Initialize Git Flow
git flow init

# Start a feature
git flow feature start feature-name

# Finish a feature
git flow feature finish feature-name

# Start a release
git flow release start release-name

# Finish a release
git flow release finish release-name

# Start a hotfix
git flow hotfix start hotfix-name

# Finish a hotfix
git flow hotfix finish hotfix-name
```

## Troubleshooting

```bash
# Check repository integrity
git fsck

# Garbage collection
git gc

# Prune unreachable objects
git prune

# Verify objects in database
git fsck --full
```