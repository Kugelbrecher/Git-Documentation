# Pull Requsets

## 1. Why Pull Requests?

Notes from Kate: https://github.com/reboottime/WebDevelopment/issues/15

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
