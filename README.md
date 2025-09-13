# GitPlayground
## How to maintain 2 git account
- https://dzone.com/articles/managing-multiple-github-accounts
- git remote set-url origin git@github.com-swsi:swsisolutions/ComposePlayGround.git
## What is Git?
- Git is a distributed version control system. This means that instead of having a central server that holds the "master" copy of your code, every developer has a complete copy of the repository, including its full history.

## Why use Git?
- Version Control: Track changes to your code over time. You can see who made what changes and when.
- Collaboration: Multiple people can work on the same project simultaneously without overwriting each other's work.
- Backup & Recovery: If something goes wrong, you can easily revert to a previous working state.
- Experimentation: Create branches to experiment with new features without affecting the main codebase.
## Core Concepts
- **Repository (Repo):** A project managed by Git. It contains all your files and the complete history of changes.
- **Working Directory:** The actual files you see and edit on your computer.
- **Staging Area (Index):** An intermediate area where you prepare changes before committing them. Think of it as a "pre-commit" area.
- **Commit:** A snapshot of your repository at a specific point in time. Each commit has a unique ID, a message describing the changes, and references to its parent commit(s).
- **Branch:** An independent line of development. You can create branches to work on new features or bug fixes without affecting the main codebase.
- **Master/Main:** The default or primary branch in most Git repositories.
- **Head:** A pointer to the tip of the current branch.
- **Remote:** A version of your repository hosted on the internet or network (e.g., GitHub, GitLab, Bitbucket).
- Let's visualize this workflow:
<img width="1024" height="1024" alt="git_workflow" src="https://github.com/user-attachments/assets/71d86d67-5d4c-4def-848f-cf5bfc4f8f78" />

## Git Basics - Getting Started
- Now, let's dive into some essential commands to get you up and running.
## 1. Installing Git
- First, make sure Git is installed on your system.
- **Windows:** Download from git-scm.com
- **macOS:** brew install git (if you have Homebrew) or install Xcode Command Line Tools (xcode-select --install).
- **Linux (Debian/Ubuntu):** sudo apt-get install git
- **Linux (Fedora):** sudo dnf install git
## 2. Initial Configuration
- After installation, you need to set your user name and email. This information will be attached to your commits.
```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
--global: Applies this configuration to all your Git repositories. You can remove it to set specific configs for a single repository.
```
## 3. Initializing a New Repository
- To start a new Git project, navigate to your project directory and initialize it:
```
cd /path/to/your/project
git init
```
- This creates a hidden .git directory, which is where Git stores all its history and configuration for that project.

## 4. Checking Status
- This command shows you the current state of your working directory and staging area.
```
  git status
```
### It will tell you:
- Which branch you're on.
- Which files are untracked (new files not yet added to Git).
- Which files have been modified but not staged.
- Which files are staged and ready for commit.
## 5. Adding Files to the Staging Area
- Once you've made changes or created new files, you need to tell Git to "stage" them for the next commit.
```
git add <filename>        # Add a specific file
git add .                 # Add all new and modified files in the current directory and subdirectories
git add -u                # Add all modified and deleted files, but not new files (useful if you only want to track changes to existing files)
```
## 6. Committing Changes
- After staging your changes, you "commit" them to the repository. Each commit should have a descriptive message.
```
git commit -m "Your commit message here"
```
- -m: Provides the commit message directly.
- If you omit -m, Git will open your default text editor (e.g., Vim, Nano) for you to write a more detailed commit message.
- Example Workflow:
- Let's say you create a new file index.html:
```
touch index.html (create the file)
git status
Output: Untracked files: index.html
git add index.html
git status
Output: Changes to be committed: new file: index.html
git commit -m "Initial commit: Add index.html"
git status
Output: nothing to commit, working tree clean
```
## 7. Viewing Commit History
- To see a list of all commits in the current branch:
```
git log
```
- This will show:
- Commit ID (SHA-1 hash)
- Author
- Date
- Commit message
## Useful git log variations:
- git log --oneline: Shows a condensed, one-line summary for each commit.
- git log --graph --oneline --decorate: Great for visualizing branch history.
- git log -p: Shows the actual changes (diff) introduced by each commit.
- git log --author="Your Name": Filter by author.
- git log --grep="bug": Filter by commit message content.
- git log --no-merges : it will display only commits not the merge commits.
- git log <start_commits>..<end_commits> --no-merges --pretty=format:"%h - %an, %ar : %s" > commit_logs.txt
- git log <start_commits>..HEAD --no-merges --pretty=format:"%h - %an, %ar : %s" > commit_logs.txt
- git log --since="YYYY-MM-DD" --until="YYYY-MM-DD" --no-merges --pretty=format:"%h - %an, %ar : %s" > commit_logs.txt
- git log --since="YYYY-MM-DD" --no-merges --pretty=format:"%h - %an, %ar : %s" > commit_logs.txt
## 8. Viewing Changes (Diff)
- To see what changes have been made:
```
git diff                  # Shows unstaged changes (changes in working directory not yet in staging area)
git diff --staged         # Shows staged changes (changes in staging area not yet committed)
git diff HEAD             # Shows all changes since the last commit (staged and unstaged)
```
## 9. Removing Files
- To remove a file from your working directory and stage its removal:
```
git rm <filename>
```
- Then commit the change: git commit -m "Remove old_file.txt"

## 10. Renaming/Moving Files
- To rename or move a file:
```
git mv <old_filename> <new_filename>
```
- This stages the rename/move. You still need to commit it: git commit -m "Rename file"

## Git Branches - The Power of Parallel Development
- Branches are fundamental to Git and allow you to work on different features or bug fixes concurrently without affecting the main codebase.

## 1. Listing Branches
- To see all local branches and which one you're currently on:
```
git branch
```
- The current branch will be marked with an asterisk (*).
## 2. Creating a New Branch
```
git branch <new-branch-name>
```
- This creates a new branch, but you remain on your current branch.

## 3. Switching Branches
- To move to an existing branch:
```
git checkout <branch-name>
```
## 4. Creating and Switching to a New Branch (Shortcut)
- This is a common operation, so there's a shortcut:
```
git checkout -b <new-branch-name>
```
- This command creates a new branch AND immediately switches you to it.
# 5. Merging Branches
- When you've finished work on a feature branch(featureA), you'll want to integrate those changes back into another branch (e.g., main or master).
- First, switch to the branch you want to merge into (the target branch - main/master):
```
git checkout main
git pull origin main
git merge featureA
```
- example

```
git checkout main
git pull origin main
git merge feature/login-ui
git push origin main
```
- Then, merge the feature branch into the current branch:
- git merge <feature-branch-name>
- Fast-forward Merge: If the target branch hasn't diverged (no new commits on main since you created feature-branch), Git simply moves the main pointer forward.
- Three-way Merge: If both branches have new commits since the split, Git creates a new "merge commit" that combines the histories.
add image
<img width="1024" height="1024" alt="merge_branch" src="https://github.com/user-attachments/assets/299c17b3-d0ba-40a7-a44c-b2052a0719f9" />
- **NOTE**
- If there are merge conflicts, git will prompt you to resolve them manually
- If you want to squash commits before merging, you can use
```
git merge --squash feature-branch-name
```
## 6. Handling Merge Conflicts
- Conflicts happen when Git can't automatically figure out how to combine changes from two branches (e.g., the same line of code was changed differently in both branches).
- **When a conflict occurs:**
- Git will tell you which files have conflicts.
- The conflicting files will contain special markers (<<<<<<<, =======, >>>>>>>) showing the different versions.
- You need to manually edit the file, choose which changes to keep, and remove the markers.
- After resolving, git add the file and then git commit to complete the merge.
## 7. Deleting Branches
- Once a feature branch is merged and no longer needed:
```
git branch -d <branch-name>   # Delete a local branch (only if merged)
git branch -D <branch-name>   # Force delete a local branch (even if not merged, use with caution!)
Git Remotes - Collaborating with GitHub/GitLab
```
- To collaborate with others or back up your code online, you'll use "remotes."

## 1. Listing Remotes
```
git remote -v
```
- Typically, you'll see origin as the default remote, pointing to your online repository.
## 2. Adding a Remote
- When you create a repository on GitHub, it will often give you this command:
```
git remote add origin <remote-repository-url>
```
## 3. Pushing Changes to a Remote
- To send your local commits to the remote repository:
```
git push -u origin main
origin: The name of your remote (usually origin).
main: The name of the branch you want to push.
```
- -u (or --set-upstream): Sets the upstream tracking reference. The first time you push a new branch, use this. After that, you can often just use git push.
## 4. Pulling Changes from a Remote
- To fetch changes from the remote repository and merge them into your current local branch:
```
git pull origin main
```
- This is essentially git fetch followed by git merge.

## 5. Fetching Changes (Without Merging)
- To download changes from the remote but not automatically merge them into your local branches:
```
git fetch origin
```
- This updates your remote-tracking branches (e.g., origin/main), allowing you to inspect changes before merging.

## Undoing Things - Git Rewind
- Git's power also comes from its ability to undo mistakes.

## 1. Unstaging a File
- If you git add a file but then decide you don't want to include it in the next commit:
```
git reset HEAD <filename>
```
- HEAD refers to the latest commit. This command essentially moves the file from the staging area back to the working directory.
## 2. Discarding Unstaged Changes
- If you've made changes to a file but want to revert it to its last committed state (discard all your recent edits):
```
git checkout -- <filename>
```
- Warning: This is destructive! Your changes will be lost.
## 3. Amending the Last Commit
- If you forgot to add a file, or made a typo in your last commit message, and haven't pushed it yet:
```
git add <forgotten-file>
git commit --amend -m "Updated commit message"
```
- This rewrites the last commit. Don't use this on commits that have already been pushed to a shared remote, as it can cause problems for collaborators.
## 4. Reverting a Commit
- To create a new commit that undoes the changes introduced by a previous commit:
```
git revert <commit-hash>
```
- This is a "safe" way to undo changes, as it preserves the history. It's preferred for undoing commits that have already been pushed.
## 5. Resetting to a Previous State (Use with Caution!)
- This command is powerful and can rewrite history. It moves the HEAD pointer and often your current branch pointer to a specified commit.
```
git reset --soft <commit-hash>    # Moves HEAD, but keeps changes staged
git reset --mixed <commit-hash>   # Moves HEAD, unstages changes (default)
git reset --hard <commit-hash>    # Moves HEAD, discards all changes (working directory and staging area are wiped clean to match the commit)
```
- --hard is very destructive. Only use it if you are absolutely sure you want to lose all subsequent changes.
- This is usually used for local cleanups and should be avoided on shared branches or commits that have been pushed.
- Git Rebase - Advanced History Rewriting
- Rebase is another powerful way to integrate changes, often used to keep a clean, linear project history.

## What Rebase Does:
- Instead of creating a merge commit, git rebase takes your commits from your feature branch, "rewinds" them, applies them on top of the target branch's latest commit, and then fast-forwards your feature branch's pointer.
## When to Use It:
- To keep your feature branch up-to-date with main before merging, leading to a cleaner merge (often a fast-forward merge).
- To squash (combine) multiple small commits into one cleaner commit before merging.
## How to Use It:
- Let's say you're on your feature-branch and want to rebase it onto main:
```
git checkout feature-branch
git rebase main
```
## Common Rebase Workflow:
```
git checkout feature-branch
git pull origin feature-branch (ensure your feature branch is up-to-date)
git checkout main
git pull origin main (ensure your main branch is up-to-date)
git checkout feature-branch
git rebase main (Apply your feature branch commits on top of the latest main)
Resolve any conflicts during the rebase.
git push -f origin feature-branch (You'll need to force push because rebase rewrites history for your feature branch. Use with caution, especially if others are working on the same feature branch!)
```

## Add Image
<img width="1024" height="1024" alt="rebase_flow" src="https://github.com/user-attachments/assets/1c3a7508-64ff-4153-8281-9ad4cf23c08c" />
### Interactive Rebase (git rebase -i)
- This is an even more powerful version of rebase, allowing you to rewrite history in a very granular way. You can:

## Squash multiple commits into one.
- Reorder commits.
- Edit commit messages.
- Delete commits.
- Split a commit into multiple commits.
```
git rebase -i HEAD~<number-of-commits>
```
- For example, git rebase -i HEAD~3 will open an editor with the last 3 commits, allowing you to choose actions for each.

# Rebase vs. Merge:
- Merge: Preserves history exactly as it happened. Creates a merge commit. History can look "messier" with many branches merging.
- Rebase: Rewrites history to be linear. No merge commits (unless conflicts occur). Creates a cleaner history, but can be dangerous if applied to shared branches.
## Rule of Thumb:
- Do not rebase commits that have already been pushed to a public/shared branch. If you do, it will cause headaches for anyone who has pulled those original commits.
- Rebase your private, local feature branches onto main before merging to keep a clean history.
# More Advanced Git Concepts & Commands
## 1. Git Stash
- Ever been working on something, then a critical bug comes in, and you need to switch branches quickly without committing your half-finished work? That's what git stash is for.
- It temporarily saves your uncommitted changes (both staged and unstaged).
```
git stash save "message" or git stash: Saves your current changes.
git stash list: Shows all stashed changes.
git stash pop: Applies the most recent stash and removes it from the stash list.
git stash apply: Applies the most recent stash but leaves it in the stash list.
git stash drop: Deletes the most recent stash.
git stash clear: Deletes all stashes.
git stash show -p: Shows the diff of the most recent stash.
```
## 2. Git Tags
- Tags are used to mark specific points in your repository's history as important. They are often used to mark release versions (e.g., v1.0, v2.0-beta).
```
git tag: List all tags.
git tag -l "v1.*": List tags matching a pattern.
git tag -a v1.0 -m "Version 1.0 Release": Create an annotated tag (recommended, includes message, author, date).
git tag v1.0: Create a lightweight tag (just a pointer to a commit).
git show v1.0: Show information about a tag.
git push origin v1.0: Push a specific tag to the remote.
git push origin --tags: Push all tags to the remote.
git tag -d v1.0: Delete a local tag.
git push origin :refs/tags/v1.0: Delete a remote tag.
```
## GIT REST
- git reset --soft HEAD~4
- git reset --hard HEAD~4

## 3. Git Reflog
- The reflog (reference log) records almost every change to your HEAD pointer. It's a lifesaver if you accidentally git reset --hard or mess up a rebase, as it allows you to find lost commits.
- git reflog: Shows a history of where HEAD has been.
- You can then use git reset --hard <reflog-entry> to go back to a specific state. For example, if you see HEAD@{5} was a good state, you could git reset --hard HEAD@{5}.

## 4. Git Ignore
- You often have files or directories in your project that you don't want Git to track (e.g., compiled code, node_modules, .env files, .DS_Store).
- You can tell Git to ignore these by creating a .gitignore file in your repository's root.
- Example .gitignore:

## Ignore compiled files
*.o
*.class

# Ignore editor config files
.idea/
.vscode/

# Ignore node_modules directory
node_modules/

# Ignore log files
*.log
npm-debug.log*

# Ignore environment variables
.env
You can also specify patterns (e.g., *.log to ignore all .log files).
Lines starting with # are comments.
## 5. Git Cherry-pick
```
git cherry-pick allows you to apply a single commit from one branch onto another branch.
git cherry-pick <commit-hash>
```
- This creates a new commit on your current branch that has the same changes as the original commit. Useful for:
- Backporting a hotfix from a development branch to a release branch.
- Taking a single feature commit from a long-lived feature branch.
## 6. Git Bisect
- If you have a bug and you know it was introduced somewhere between a "good" commit and a "bad" commit, git bisect can help you find the exact commit that introduced the bug through a binary search.
```
git bisect start
git bisect bad   # Mark the current commit as bad
git bisect good <good-commit-hash> # Mark a known good commit
```
- Git will then checkout a commit in the middle. You test it:
- git bisect good if it's good.
- git bisect bad if it's bad.
- Repeat until Git tells you which commit was the first bad one.
- git bisect reset to end the bisect session and return to your original branch.
## 7. Git Submodules
- Submodules allow you to embed one Git repository inside another as a subdirectory. This is useful for managing dependencies where the dependency is also a Git repository.
```
git submodule add <repository-url> <path>: Add a submodule.
git submodule init: Initialize submodules in a new clone.
git submodule update: Fetch and update submodules.
git submodule update --remote: Update submodules to their latest remote commit.
```
## 8. Git Hooks
- Git hooks are scripts that Git executes automatically before or after events like commit, push, and receive.
- They are located in the .git/hooks directory (they are local to each repository and not usually committed).
- **Common hooks:**
- pre-commit: Run before a commit is created (e.g., to lint code, run tests).
- pre-push: Run before pushing commits (e.g., to run tests, ensure merge conflicts are resolved).
- post-commit: Run after a commit.
- You write these scripts in bash, python, or any language executable on your system.
## Best Practices
- Commit Frequently, Commit Early: Smaller, more focused commits are easier to understand and revert.
- Write Clear Commit Messages: Explain what changes you made and why.
- First line: concise summary (under 50-72 chars).
- Detailed explanation if needed.
- Branch for Features/Bug Fixes: Don't work directly on main/master.
- Keep Branches Short-Lived: Merge feature branches back into main frequently.
- Pull Before You Push: Always git pull before starting work and before git push to avoid unnecessary conflicts.
- Use .gitignore: Keep your repository clean by ignoring unnecessary files.
- Understand HEAD: It's your current location.
- Be Careful with History Rewriting: reset --hard, rebase, and amend rewrite history.
- Avoid using them on commits that have already been pushed and shared with others unless absolutely necessary and you know what you're doing.

