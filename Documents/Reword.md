# How to Modify a Previously Pushed Commit Message (Safe Scenario)

## Scenario

- Branch is NOT merged to `main`
- No open PR
- No one else has pulled the branch
- Commits are already pushed to remote
- You need to change the message of an earlier commit (not the latest one)

This is safe to do using interactive rebase + force push.

---

## Example Commit History

```
A --- B
      ↑
   branch-a (HEAD)
```

- `A` = first commit (needs message change)
- `B` = second commit

We want to edit commit `A`.

---

## Step 1 — Start Interactive Rebase

If there are 2 commits total:

```bash
git rebase -i HEAD~2
```

---

## Step 2 — Mark Commit for Editing

You will see something like:

```
pick abc123 first commit message
pick def456 second commit message
```

Change `pick` to `reword` (or `r`) for the commit you want to edit:

```
reword abc123 first commit message
pick def456 second commit message
```

Save and close the editor.

---

## Step 3 — Edit the Commit Message

Git will now open your editor.

- Modify the commit message
- Save and exit

Rebase will complete automatically.

---

## Step 4 — Push Changes to Remote

Because you rewrote history, you must force push:

```bash
git push --force-with-lease
```

### Why `--force-with-lease`?

It is safer than `--force` because it:
- Prevents overwriting others' work
- Fails if someone pushed new commits meanwhile

---

## Final Result

Your branch history is rewritten with the corrected commit message.

Safe because:

- No PR exists
- Not merged to main
- No one else pulled the branch

---

## If You Were Editing the Latest Commit Only

You could instead run:

```bash
git commit --amend
git push --force-with-lease
```

---

## Best Practice

Only rewrite history when:

- Branch is private or unused
- No one else has based work on it
- Not merged into main

Otherwise, avoid force pushing.