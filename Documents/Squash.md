
Squashing commits before making a PR is a pretty common practice — it cleans up history and makes your pull request easier to review. You can do it with an **interactive rebase** in Git. Here’s the usual process:

---

### 1. Make sure your branch is up to date

```bash
git fetch origin
git checkout your-branch
git rebase origin/main   # or origin/master, depending on your base branch
```

---

### 2. Start an interactive rebase

If you want to squash the **last N commits** into one:

```bash
git rebase -i HEAD~N
```

Example: If you have 5 commits you want to squash into one, run:

```bash
git rebase -i HEAD~5
```

default editor is vim (based on the ~/.git/rebase-merge/git-rebase-todo path). To save and exit in vim:

- Press Esc
- Type :wq
- Press Enter


---

### 3. Mark commits for squashing

Git will open your default editor with a list like:

```
pick a1b2c3 First commit
pick d4e5f6 Second commit
pick g7h8i9 Third commit
pick j1k2l3 Fourth commit
pick m4n5o6 Fifth commit
```

* Keep the first commit as `pick`
* Change the others to `squash` (or just `s`):

```
pick a1b2c3 First commit
squash d4e5f6 Second commit
squash g7h8i9 Third commit
squash j1k2l3 Fourth commit
squash m4n5o6 Fifth commit
```

---

### 4. Edit the commit message

Git will then prompt you to combine commit messages. Keep or clean up what you want (usually one clear message).

---

### 5. Push changes

Since you rewrote history, you need to **force push**:

```bash
git push origin your-branch --force
```

---

### Edge Case: Unstaged changes block the rebase

If you run `git rebase -i HEAD~N` and see:

```
error: cannot rebase: You have unstaged changes.
error: Please commit or stash them.
```

Git won't start the rebase with a dirty working directory. Fix it first:

**Option A — Stash your changes temporarily:**

```bash
git stash push -m "WIP before squash"
git rebase -i HEAD~N
# ... complete the squash ...
git stash pop
```

**Option B — Stage and commit them first:**

```bash
git add .
git commit -m "WIP: save before squash"
git rebase -i HEAD~N   # now squash this commit in too if needed
```

After the rebase completes, force push as normal.

