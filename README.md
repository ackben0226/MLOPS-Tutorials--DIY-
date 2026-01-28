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
<br/> __MLOps reason__
- main represents ___production-ready, deployable ML systems__.
```ruby
git status
```
- __What it does:__ Shows the current branch and lists untracked or modified files. Always run before committing.
<br/> __MLOps rule:__ Run this __before every commit or merge__ to avoid mistakes.

## 2. Create integration branch (```develop```) — CRITICAL STEP
```ruby
git checkout -b develop
```
__What it does:__ Creates and switches to the ```develop``` branch.
<br/>**MLOps reason**
- ```main``` = production
- ```develop``` = integration / pre-production
- All feature work merges into ```develop```, __not directly into__ ```main```
This prevents breaking production ML systems.

## 2. Create project folder structure
```ruby
mkdir app pipelines src tests
````
- __What it does:__ Creates folders for inference, training pipelines, shared logic, and tests.
<br/> __MLOps reason__
- Enforces system-level thinking, not notebook-based experimentation.
```ruby
echo "# MLOps Project Title" > README.md
```
- __What it does:__ Creates a README file with a project title. Git will track this file.
<br/> __MLOps reason__
<br/> Every production ML system must be explainable to:
- reviewers
- future teammates
- auditors
```ruby
dir
```
- __What it does:__ Lists files in your folder so you can confirm the structure. 

## 4. First commit ((baseline snapshot))
```ruby
git add .
```
-  __What it does:__ Stages all files in the folder for the first commit.
```ruby
git commit -m "init: scaffold mlops project structure"
```
- __What it does:__ Saves the staged files as a snapshot in the repository. The message explains why this commit exists.
<br/> __MLOps reason:__ Establishes a clean, stable baseline for all future changes.
```ruby
git log --oneline
```
- __What it does:__ Shows the commit history in a concise format. Should show your first commit.

## 5. Checking status
```ruby
git status
git branch
```
__What it does:__
Confirms: your current branch working tree state
<br/> __MLOps rule:__
Never commit without checking where you are.

## 6. Feature branch workflow 
```ruby
git checkout develop
git pull
git checkout -b feature/<feature-name>  # create and switch
```
- __What it does:__ Creates a new or feature branch called feature/<name> from ```develop```, not ```main``` and switches you to it.
- __Use case:__ Isolate work for a new feature (e.g., new data validation pipeline or API endpoint).
<br/> __MLOps reason:__
<br/> Feature branches isolate risk:
- new pipelines
- model changes
- API updates
__🚫 Never branch from main__

## 7. Working on the feature branch
```ruby
git status
```
- __What it does:__ Shows which files changed and are ready to stage./Shows modified and untracked files.
```ruby
git add <file>
```
- __What it does:__ Stage a single file for commit. Use ```git add .``` only for all changes.
```ruby
git commit -m "feature: add healthcheck API endpoint"
```
- __What it does:__ Commits your staged changes with a meaningful message explaining the feature.
Commits a single, well-scoped change.

<br/> __MLOps rule__
<br/> One commit = one system behavior change.

## 8. Push feature branch & open Pull Request
```ruby
git push -u origin feature/<feature-name>
```
**What it does:** Pushes your feature branch to the remote repository.
**Next step (conceptual)**
<br/>Open a Pull Request:
```
# php template
feature/<feature-name> → develop
```
__MLOps reason__
- PRs are quality gates.
- They prevent silent failures and enforce review discipline.

## 9. Merge feature into ```develop``` not ```main```
```ruby
git switch main
```
- **What it does:** Switches back to main. Always merge into main, never work on it directly.
```ruby
git checkout develop
git merge feature/<feature-name>
```
__What it does:__ Integrates/combines the feature into the integration branch.
```ruby
git branch -d feature/<feature-name>
```
__What it does:__ Deletes the feature branch after merge.
__MLOps rule:__ Feature branches are disposable.

## 10. Release to production (main) — deliberate step
```ruby
git checkout main
git merge develop
```
__What it does:__
Promotes tested code to production.
```ruby
git tag v0.1.0
```
__What it does:__ Creates a release tag.
<br/> __MLOps reason__
<br/> Tags link:
- deployed code
- pipelines
- models
  for audit and rollback.

## 11. Resolving merge conflicts
```
text
<<<<<<< HEAD
develop branch code
=======
feature branch code
>>>>>>> feature/<name>
```
__How to resolve__
1. Edit the file and keep the correct version
2. Stage the fix:
```ruby
git add <file>
```
3. Complete the merge
```ruby
git commit -m "merge: resolve <feature> conflict"
```
__MLOps Rule__
<br/> Resolve conflicts in `develop`, never directly in `main`.

## 12. Checking/Inspectig history and status
```ruby
git log --oneline --graph --decorate
```
- __What it does:__ Shows branch structure (visuals), merges, and commits. Crucial for understanding project evolution.
__MLOps reason__
<br/>Used to trace:
- pipeline changes
- training logic evolution
- production releases

```ruby
git status
```
- __Always run__ before committing or merging to avoid mistakes.

## 13. Correct Week-1 MLOps Mindset (Fixed)

### ✅ Do
- Always branch from `develop`  
- Keep commits small and descriptive  
- Never commit broken code  
- Use pull requests (PRs), even when working solo  
- Treat `main` as production-ready at all times  

### 🚫 Don’t
- Never work directly on `main`  
- Never merge feature branches straight into `main`  

