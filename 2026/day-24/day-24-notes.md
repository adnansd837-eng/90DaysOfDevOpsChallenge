# Day 24 – Advanced Git

Today I practiced some advanced Git commands that are useful when working with branches and multiple developers.

I learned about **merge, rebase, squash, stash, and cherry-pick**.

---

## 1. Git Merge

I used `git merge` to combine changes from one branch into another branch.

### Commands I used

```bash
git switch main
git merge feature-login
```

### What I understood

* **Fast-forward merge:** Happens when there are no new commits on `main`. Git simply moves `main` forward.
* **Merge commit:** Happens when both branches have different commits and Git needs to combine them.
* **Merge conflict:** Happens when two branches change the same part of a file. I need to fix the conflict manually and then commit the changes.

To check the conflict:

```bash
git status
```

After fixing:

```bash
git add .
git commit
```

---

## 2. Git Rebase

I practiced `rebase` to put my branch changes on top of the latest `main`.

```bash
git switch feature-dashboard
git rebase main
```

### What I understood

Rebase changes the position of my commits and creates a cleaner, straight Git history.

### Merge vs Rebase

* Merge keeps the branch history.
* Rebase creates a more linear history.
* I should be careful with rebase when commits are already pushed and shared with others.

---

## 3. Squash Merge

I learned that squash can combine multiple small commits into one commit.

```bash
git switch main
git merge --squash feature-profile
git commit -m "Add profile feature"
```

For example, instead of having many commits like:

```text
fix typo
change format
fix again
update file
```

I can combine them into one meaningful commit.

This helps keep the main branch clean.

---

## 4. Git Stash

Sometimes I may have unfinished changes but need to switch to another branch.

For this situation, I can use `git stash`.

```bash
git stash
git switch main
```

Later, I can get my changes back:

```bash
git stash pop
```

### Commands I practiced

```bash
git stash
git stash list
git stash push -m "my work"
git stash pop
git stash apply
```

### `pop` vs `apply`

* `git stash pop` → applies the changes and removes the stash.
* `git stash apply` → applies the changes but keeps the stash.

---

## 5. Git Cherry-Pick

Cherry-pick is used when I want to take **one particular commit** from another branch.

First I find the commit:

```bash
git log --oneline
```

Then I use:

```bash
git cherry-pick <commit-id>
```

I understood that cherry-pick can be useful for applying a specific bug fix or change without merging the complete branch.

---

## Git History

To see my branches and commits in a visual way:

```bash
git log --oneline --graph --all
```

This helped me understand how branches and commits are connected.

---

## Commands I Practiced

```bash
git merge
git rebase
git merge --squash
git stash
git stash list
git stash pop
git stash apply
git cherry-pick
git log --oneline --graph --all
git status
```

---

## What I Learned

* I learned how to merge changes from different branches.
* I understood the basic difference between merge and rebase.
* I learned how to temporarily save work using stash.
* I learned how to combine small commits using squash.
* I learned how to take a specific commit using cherry-pick.
* I also understood how merge conflicts can happen and how to resolve them.


## My Takeaway

Today I understood that Git is not only about `add`, `commit`, and `push`. Branch management is very important when working on real projects with multiple developers.