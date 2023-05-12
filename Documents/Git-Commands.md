# Git Commands


## **1. git init, git clone**
ducumentation [here](https://github.com/git-guides/git-init), [here](https://git-scm.com/docs/git-init)

### 1.1 git init vs git clone

| git init | git clone |
|  | the remote already exists |

Remove git:
```bash
rm -rf .git*
```







## 2. [git branch](https://git-scm.com/docs/git-branch), [git checkout](https://git-scm.com/docs/git-checkout), [git switch](https://git-scm.com/docs/git-switch)




## 3. [git fetch](https://git-scm.com/docs/git-fetch), [git merge](https://git-scm.com/docs/git-merge), [git pull](https://git-scm.com/docs/git-pull)

Fetch: 
- When no remote is specified, by default the `origin` remote will be used, unless there’s an upstream branch configured for the current branch.
- Q: why fatal error when `git fetch origin/main` to local main branch? (fatal: 'origin/main' does not appear to be a git repository fatal: Could not read from remote repository.)
- <img src="../sources/fetch.jpg" width="500">

Merge: 
- usually merge origin/main branch to local main branch. 
- Confirm message is 'Already up to date.'
- <img src="../sources/merge.jpg" width="500">

Difference between `git fetch` and `git pull`:
- `git fetch` asks git if the remote has any updates that the local work directory doesn't have. It does not involve in file transferring from remote to local git work repository.
- `git pull` pull remote changes if there are any. `git pull` command involve in file transferring from remote repo to local git repository