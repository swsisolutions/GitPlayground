# Git interview questions
## Basics
1. WHat is git and why it is used ?
2. What is the difference between git and github ?
3. What is repository in git ?
4. How do you initialize git repository ?
5. What is the difference between git clone and git fork ?
6. What is the purpose of git add, git commit, git push ?
7. What is the difference between git pull and git fetch ?
8.What is a commit in git ?
9. How do you check status of repository ?
10. How do you view a commit history
11. what is gitignore file used for ?
12.How do you undo a commit ?
Ans : git reset --soft HEA~1
13. What is staging area in git ?
14. What is the difference between HEAD, working directory and index ?


## INtermidiate level interview question
- What is branching in git and why it is useful ?
- How do you create and switch a new branch ?
- What is the difference between git merge and git rebase ?
- How do you resolve merge conflicts ?
- WHat is fast-forward merge ?
- What is a detached HEAD state ?
- How do you delete a branch locally and remote ?
  - git branch -D branch-name : to delete locally
  - git push origin --delete branch-name : delete branch remotely
- What is the difference between git reset and git revert ?
- What is the different types of git reset (soft, hard, mixed) ?
- How do you stash changes in git ?
- How do you apply the stached changes ?
- What is the difference between git stash pop, git stash appy ?
- How do you tag a commit in git ?
- What is the difference between lightweight and annotated tags ?
## Advanced git interview questions
- How does git internally store data ?
- What are git hooks and how are they used ?
- What is the reflog and how is it useful ?
- How do you recover a deleted commit ?
  - git reflog (it will list down all the commits)
  - git reset --hard <commit-hash> (Find the commit hash from the above list to recover)
  - git checkout -b recovered-branch <commit-hash>
- What is cherry-picking in git ?
- How do you squash commits ?
  - git rebase -i HEAD~n (replace n withe the number of commits you want to squash)
  - in the editor that opens, you will see a list like this
  - pick arew234 first commit
  - pick arew235 second commit  
  - pick arew236 third commit
  - Change all but first pick to squash or s
  - pick commmit-hash1 first commit
  - squash commmit-hash2 2nd commit
  - squash commmit-hash3 3rd commit
  - git push origin branch0-name --force
- What is the difference between git rebase -i and git merge ?
- How do you perform bisect to find a bug ?
- What is the difference between girt clean and git reset --hard ?
- Ho wdo you handle a large binary file in git ?
- What is git LFS (Large file storage ) ?
