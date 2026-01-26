# MLOPS-Tutorials-DIY
# MLOps Week 1 — Git Commands

### 1. Repository setup

## Repository setup
```ruby
cd <project-folder> -- open cmd/terminal in project folder
cd C:\Users\n****\OneDrive\Desktop\mlops-week1
```
- __What it does:__ Navigate to your project folder. All Git commands must be run __inside your repo folder__.
```ruby
git init
```
- __What it does:__ Initializes Git. Creates the hidden ```.git``` folder that tracks all changes.
```ruby
git branch -m main   # rename default branch to main
```
- __What it does:__ Renames the default branch ```master``` to ```main```. This is standard in modern Git workflows.
```ruby
git status
```
- __What it does:__ Shows the current branch and lists untracked or modified files. Always run before committing.

## Folder structure
```ruby
mkdir app, data, tests   # PowerShell: mkdir app, data, tests
echo "# Project Title" > README.md
```

## First commit
```ruby
git add .
git commit -m "init: scaffold mlops project structure"
```

## Checking status
```ruby
git status
git branch
git log --oneline
```

## Feature branch workflow
```ruby
git checkout -b feature/<name>   # create and switch
git add .
git commit -m "feature: <what changed>"
git switch main                  # go back to main
git merge feature/<name>         # merge feature into main
```

## Handling merge conflicts
__1. Edit conflicting files__
__2. git add <file>__
__3. git commit -m "merge: resolve conflict"__
