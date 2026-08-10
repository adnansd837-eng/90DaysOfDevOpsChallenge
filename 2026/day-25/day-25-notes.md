# Day 25 – Git Reset, Revert & Branching Strategies

Today I learned how to undo changes in Git and how different teams manage their branches.

I practiced **reset, revert, reflog**, and learned about **GitFlow, GitHub Flow, and Trunk-Based Development**.

---

## 1. Git Reset

I practiced three types of reset.

### Soft Reset

```bash
git reset --soft HEAD~1
```

It removes the last commit but keeps the changes **staged**.

I can check the changes using:

```bash
git status
```

### Mixed Reset

```bash
git reset --mixed HEAD~1
```

It removes the last commit and keeps the changes in my working directory, but the changes become **unstaged**.

### Hard Reset

```bash
git reset --hard HEAD~1
```

It removes the last commit and also removes the changes from the working directory.

I learned that `--hard` should be used carefully because it can delete changes.

### Simple Difference

| Reset     | What I understood                     |
| --------- | ------------------------------------- |
| `--soft`  | Commit removed, changes stay staged   |
| `--mixed` | Commit removed, changes stay unstaged |
| `--hard`  | Commit and changes are removed        |

I would normally use reset for my **local/unpushed commits**.

I should avoid resetting commits that are already pushed and being used by other developers.

---

## 2. Git Revert

I also practiced `git revert`.

First, I checked my commits:

```bash
git log --oneline
```

Then I reverted a particular commit:

```bash
git revert <commit-id>
```

Git creates a **new commit** that reverses the changes from the old commit.

### What I understood

The old commit is still present in the history.

This makes `git revert` safer for shared branches because it does not rewrite the existing history.

---

## 3. Reset vs Revert

|                                      | `git reset`                       | `git revert`                         |
| ------------------------------------ | --------------------------------- | ------------------------------------ |
| What it does                         | Moves the branch back             | Creates a new commit to undo changes |
| Removes commit from current history? | Can remove it from branch history | No                                   |
| Safe for shared branches?            | Usually no                        | Yes, generally safer                 |
| When to use                          | Local/unpushed changes            | Changes already pushed/shared        |

### Easy way to remember

**Reset → move the branch back**

**Revert → make a new commit to undo a change**

---

## 4. Git Reflog

I learned that `git reflog` keeps a record of where my `HEAD` and branches have pointed.

```bash
git reflog
```

It can be useful if I accidentally reset or lose a commit and want to find it again.

---

# 5. Branching Strategies

## GitFlow

GitFlow uses different branches for different types of work.

```text
main
  |
develop
  |
feature
  |
develop
  |
release
  |
main
```

It can be useful for projects that have planned and scheduled releases.

### Pros

* Clear separation of development and releases
* Useful for release-based projects

### Cons

* More branches
* More complicated to manage

---

## GitHub Flow

GitHub Flow is simpler.

```text
main
  |
feature branch
  |
Pull Request
  |
main
```

Developers create a feature branch, make changes, create a Pull Request, and merge it into `main`.

### Pros

* Simple to understand
* Good for continuous development
* Works well with CI/CD

### Cons

* Needs good testing before merging
* May not be ideal for complex release processes

---

## Trunk-Based Development

In this approach, developers work with the main branch and use short-lived branches when needed.

```text
        feature
           |
main ------+------ main
           |
        feature
```

Changes are integrated into the main branch frequently.

### Pros

* Fast development
* Works well with CI/CD
* Keeps branches short-lived

### Cons

* Requires good automated testing
* Developers need to integrate changes frequently

---

## Which Strategy Would I Choose?

### Startup

For a startup that needs to move quickly, I would choose **GitHub Flow** because it is simple and works well with fast development and CI/CD.

### Large Team

For a large team with scheduled releases, I would consider **GitFlow** because it provides separate branches for features, releases, and hotfixes.

### Fast CI/CD

For teams that deploy frequently, **Trunk-Based Development** can be a good choice.

---

# 6. Git Commands I Practiced

```bash
# Basic
git status
git add .
git commit -m "message"
git log --oneline
git diff

# Branching
git branch
git switch main
git switch -c feature-name

# Remote
git push
git pull
git fetch
git clone

# Merge and Rebase
git merge feature-name
git rebase main

# Stash
git stash
git stash list
git stash pop

# Cherry-pick
git cherry-pick <commit-id>

# Reset
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1

# Revert
git revert <commit-id>

# Recovery
git reflog
```

---

# What I Learned

* I learned three types of `git reset`.
* I understood why `git revert` is safer for shared branches.
* I learned how `git reflog` can help recover from mistakes.
* I understood GitFlow, GitHub Flow, and Trunk-Based Development.
* I learned that the right branching strategy depends on the team's workflow.


## My Takeaway

Today I learned that making mistakes in Git is normal, but knowing how to safely recover from them is important.

I also understood that Git branching strategies help teams work together without disturbing the main code.
