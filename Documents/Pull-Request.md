# Pull Requsets

## 1. Why Pull Requests?

Notes from Kate: https://github.com/reboottime/WebDevelopment/issues/15

Small files, large amount, so that we can update and finish PR quickly.

## 2. Update my local repo
  
  ```bash
  # clone remote repo to local
  git clone <remote repo url>
  ```

  ```bash
  # check remote repo
  git remote -v

  - origin  https://consentify@dev.azure.com/consentify/Main/_git/Main (fetch)
  - origin  https://consentify@dev.azure.com/consentify/Main/_git/Main (push)
  ```

  git branch -M main

  ```bash
  # other people may have updated the remote repo
  # use fetch + merge (or pull) to update local repo
  git fetch

  git merge origin/master
  ```

  ```bash
  # before making a PR, make sure update teammate commits under same branch
  # 1. switch to the branch:
  git checkout branchA

  # 2. downloads all the changes from the remote repository 
  # but doesn't integrate them into my local branches yet:
  git fetch origin

  # 3. git will try to replay branchA's commits on top of the latest origin/main.
  git rebase origin/main
  # If there are no conflicts: Git will automatically apply your commits.
  # If there are conflicts: Git will pause the rebase and tell you which files have conflicts. You'll need to:
    # Open the conflicted files in your editor.
    # Manually resolve the conflicts.
    # Stage the resolved files: git add <conflicted_file>
    # Continue the rebase: git rebase --continue
    # Repeat steps 2-4 for any further conflicts.

  # 4. Once the rebase is complete, you'll need to force-push your changes to the remote repository:
  git push --force-with-lease origin branchA
  ```

```bash
  # once PR is approved, I need to update my local repo and branches:
  git checkout main
  git fetch origin
  git merge origin/main
  # This makes your local main the official, up-to-date version on the remote.
  git push origin main

  # also need to update the local branches worked on and other branches:
  git checkout branchA
  git rebase origin/main
  git push --force-with-lease origin branchA
  git checkout branchB
  git rebase origin/main
  git push --force-with-lease origin branchB
```

## 3. Update remote repo
  
  ```bash
  # commit changes to a branch other than Main
  # it is recommended to create a new branch for each feature
  git checkout -b <branch name>
  ```

  ```bash
  # then normal git workflow
  git add <file name>
  git commit -m "<commit message>"
  git push origin <branch name>
  ```


## 4. git ignore

https://stackoverflow.com/questions/107701/how-can-i-remove-ds-store-files-from-a-git-repository

step1: Remove existing .DS_Store files from the repository:

```bash
find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
```

step2: Add .DS_Store to your .gitignore file:
add this line: .DS_Store
or 
```bash
echo .DS_Store >> .gitignore
```
this will also create the .gitignore file if it doesn't exist already.

step3: commit the changes to remote repo
git add .
git commit -m "removed .DS_Store files"
git push origin <branch name>