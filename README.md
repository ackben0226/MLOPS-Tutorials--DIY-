# MLOPS-Tutorials-DIY
# MLOps Week 1 — Git Commands

## Repository setup
```ruby
cd <project-folder> -- open cmd/terminal in project folder
git init
git branch -m main   # rename default branch to main
```

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
# 1. Edit conflicting files
# 2. git add <file>
# 3. git commit -m "merge: resolve conflict"
