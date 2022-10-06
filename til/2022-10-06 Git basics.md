# Git basics

## Adding more changes to last commit

Reference: https://medium.com/@igor_marques/git-basics-adding-more-changes-to-your-last-commit-1629344cb9a8

- Add the modified file(s):

  ```bash
  git add [file name]
  // or add all changed files
  git add .
  ```

- Then commit with new message or the same message as the last commit:

  - New message:

  ```bash
  git commit --amend
  ```

  - Same message:

  ```bash
  git commit --amend --no-edit
  ```

- Push to git:
  - If the commit only stays at local:
  ```bash
  git push
  ```
  - If the last commit was pushed to git:
  ```bash
  git push -f origin some_branch
  ```

## Rebase local branch onto remote master

Reference: https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master

- Fetch the remote master branch:
  ```bash
  git fetch origin master		# Updates origin/master
  ```
- Rebase the local branch onto the remote master branch:
  ```bash
  git rebase origin/master    # Rebases current branch onto origin/master
  ```
  Or
  ```bash
  git pull --rebase origin master
  ```
- Push to git: add -f as the local branch has been rebased
  (Reference: https://stackoverflow.com/questions/39399804/updates-were-rejected-because-the-tip-of-your-current-branch-is-behind-its-remot)
