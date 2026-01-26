# MLOps Week 1 — Git Commands

## 1. Repository setup
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

## 2. Create folder structure
```ruby
mkdir app, data, tests   # PowerShell: mkdir app, data, tests
````
- __What it does:__ Creates project subfolders for code, raw data, and tests.
```ruby
echo "# Project Title" > README.md
```
- __What it does:__ Creates a README file with a project title. Git will track this file.
```ruby
dir
```
- __What it does:__ Lists files in your folder so you can confirm the structure.

## 3. First commit
```ruby
git add .
```
-  __What it does:__ Stages all files in the folder for the first commit.
```ruby
git commit -m "init: scaffold mlops project structure"
```
- __What it does:__ Saves the staged files as a snapshot in the repository. The message explains why this commit exists.
```ruby
git log --oneline
```
- __What it does:__ Shows the commit history in a concise format. Should show your first commit.

## 4. Checking status
```ruby
git status
git branch
```

## 4. Feature branch workflow
```ruby
git checkout -b feature/<name>   # create and switch
```
- __What it does:__ Creates a new branch called feature/<name> and switches you to it.
- __Use case:__ Isolate work for a new feature (e.g., new data validation pipeline or API endpoint).
```ruby
git branch
```

## 5. Working on the feature branch
```ruby
gitstatus
```
- __What it does:__ Shows which files changed and are ready to stage.
```ruby
git add <file>
```
- __What it does:__ Stage a single file for commit. Use ```git add .``` for all changes.
```ruby
git commit -m "feature: add healthcheck API endpoint"
```
- __What it does:__ Commits your staged changes with a meaningful message explaining the feature.

## 6. Merge feature back into main
```ruby
git switch main
```
- **What it does:** Switches back to main. Always merge into main, never work on it directly.
```ruby
git merge feature/<name>
```
__What it does:__ Combines the feature branch changes into main.

## 7. Resolving merge conflicts
- __Git will mark conflicts in files like this:__
```ruby
___Text___
<<<<<<< HEAD
main branch code
=======
feature branch code
>>>>>>> feature/<name>
```

- __How to resolve:__
  1. Edit the file to keep the correct version.
  2. Stage the fixed file: ```git add <file>```
  3. Complete merge: ```git commit -m "merge: resolve <feature> conflict"```

## 8. Checking history and status
```ruby
git log --oneline --graph --decorate
```
- __What it does:__ Shows a visual history of branches, merges, and commits. Crucial for understanding project evolution.

```ruby
git status
```
- __Always run__ before committing or merging to avoid mistakes.

## Pro tip (Week 1 MLOps mindset)
- Always branch from ```main```
- Keep commits small and descriptive
- Never commit broken code to ```main```
- Use ```git log``` to verify history before merging
- Treat ```main``` as deployable at all times

git commit -m "feature: <what changed>"
git switch main                  # go back to main
git merge feature/<name>         # merge feature into main
```

## Handling merge conflicts
__1. Edit conflicting files__
__2. git add <file>__
__3. git commit -m "merge: resolve conflict"__
