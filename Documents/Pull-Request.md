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
  ```
  
  - origin  https://consentify@dev.azure.com/consentify/Main/_git/Main (fetch)
  - origin  https://consentify@dev.azure.com/consentify/Main/_git/Main (push)


  ```bash
  # other people may have updated the remote repo
  # use fetch + merge (or pull) to update local repo
  git fetch origin master

  git merge origin/master
  ```



## 3. Update remote repo