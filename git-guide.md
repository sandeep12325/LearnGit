# Git Guide: Reverting and Undoing Changes

This guide outlines common Git commands used to undo mistakes at different stages of development.

---

## 1. Undoing Uncommitted Changes (Working Directory)
If you made changes to a file but haven't committed them yet, and you want to discard them:

### Using `git restore` (Recommended for modern Git)
```bash
git restore <filename>
```
* **What it does:** Discards changes in your working directory for the specified file, returning it to the state of the last commit.

### Using `git checkout` (Older method)
```bash
git checkout -- <filename>
```
* **What it does:** Same as `git restore`.

---

## 2. Undoing Staged Changes (Before Commit)
If you ran `git add <filename>` but decided you don't want to include it in the next commit:

### Using `git restore --staged`
```bash
git restore --staged <filename>
```
* **What it does:** Unstages the file, but keeps your modifications in the working directory.

---

## 3. Amending the Last Commit
If you just committed but forgot to add a file, or made a typo in the commit message:

```bash
git commit --amend -m "Your new commit message"
```
* **What it does:** Replaces the very last commit with a new one containing any new staged changes and/or the new message.
* **WARNING:** Only do this if you haven't pushed the commit to a shared repository yet.

---

## 4. Reverting a Published Commit (Safe Undo)
If you have committed (and possibly pushed) a change, but want to undo its effects without rewriting history:

```bash
git revert <commit-hash>
```
* **What it does:** Creates a **new commit** that does the exact opposite of the target commit. If the target commit added a line, the revert commit removes it.
* **Why it's safe:** It does not change existing history, making it perfectly safe for shared branches.

---

## 5. Resetting History (Advanced / Rewriting History)
If you want to completely move your branch back to a previous commit:

### Soft Reset (Keep your changes)
```bash
git reset --soft <commit-hash>
```
* **What it does:** Moves the branch pointer back to the target commit, but keeps all your changes staged.

### Mixed Reset (Keep changes, but unstage them)
```bash
git reset <commit-hash>
```
* **What it does:** This is the default. Moves the branch back to the target commit, keeping changes in your working directory but unstaging them.

### Hard Reset (Discard ALL changes - CAUTION!)
```bash
git reset --hard <commit-hash>
```
* **What it does:** Moves the branch back to the target commit and **permanently discards** all uncommitted changes and subsequent commits.
* **WARNING:** You will lose any uncommitted work.


Add git command ---
git reset --hard Head~1

