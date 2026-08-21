# Day 26 – GitHub CLI

## What I Learned

Today I learned about **GitHub CLI (`gh`)**. It allows me to manage GitHub directly from the terminal without opening the browser.

## Authentication

Check GitHub CLI:

```bash
gh --version
```

Login:

```bash
gh auth login
```

Check logged-in account:

```bash
gh auth status
```

`gh` supports browser login, personal access token and SSH authentication.

## Repository Commands

Create repo:

```bash
gh repo create my-test-repo --public --add-readme
```

Clone repo:

```bash
gh repo clone owner/repo
```

View repo:

```bash
gh repo view
```

List repos:

```bash
gh repo list
```

Open repo in browser:

```bash
gh repo view --web
```

Delete repo:

```bash
gh repo delete owner/repo
```

## Issue Commands

Create issue:

```bash
gh issue create --title "Bug" --body "Found a bug" --label bug
```

List issues:

```bash
gh issue list
```

View issue:

```bash
gh issue view 1
```

Close issue:

```bash
gh issue close 1
```

`gh issue` can be used in scripts to automatically create and manage issues.

## Pull Request Commands

Create PR:

```bash
gh pr create --fill
```

List PRs:

```bash
gh pr list
```

View PR:

```bash
gh pr view 1
```

Check PR:

```bash
gh pr checks 1
```

Merge PR:

```bash
gh pr merge 1
```

Merge methods:

* Merge
* Squash
* Rebase

I can review another person's PR using `gh pr view`, `gh pr diff` and `gh pr checks`.

## GitHub Actions

List workflow runs:

```bash
gh run list
```

View a run:

```bash
gh run view <run-id>
```

List workflows:

```bash
gh workflow list
```

These commands are useful for checking CI/CD pipeline status directly from the terminal.

## Useful Commands

```bash
gh api
gh gist
gh release
gh alias
gh search repos
```

## My Key Learning

GitHub CLI makes GitHub management easier from the terminal. It is especially useful for **DevOps, scripting and CI/CD automation**.

**Day 26 Completed ✅**
