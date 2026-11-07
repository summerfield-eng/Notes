# GIT

## GIT

- Git is a version control system that can track changes we do in our code.
- Github is the program that stores all our changes

## Git commands

- `git status`
  - this allows us to see the status of the files.
- `git log`
  - this allows us to see all our commits
- `git add <file to add>`
  - this command allows us to push our files into the staging phase.
  - if we have multiple files, `git add -A` allows us to push it all to the staging phase.
- `git commit -m "<message goes here>"`
  - this will commit our code changes. Although this will not put it on the main code yet. Think of it like a draft.
- `git push origin "<branch>"`
  - this will push our code into the codebase of the branch we want.
  - `git checkout -b <branch name>` allows us to create a branch and switch to the new branch
- `git clone <SSH Link goes here>`
  - this will allow us to download the repository.
- `git branch`
  - this allows us to see all the current branch in the repository. The branch where the asterisk(\*) is appended is where we are currently.
- `git branch <branch name>`
  - this allows us to create a branch.
- `git checkout <branch name>` or `git switch <branch name>`
  - this command allows us to change to any branch.
- `git merge <branch name>`
  - this merges the `branch name` into the branch we are currently in.
- `git branch -d <branch name>`
  - this allows us to delete the branch when we dont need it anymore.
- `git push origin --delete <branch name>`
  - this will delete the branch on the remote repository on github since `git branch -d <branch name>` only deletes the local one.

## Forking

- Sometimes we saw a repository and we want to copy it our own repository. We can do that by forking that repository. Although you can directly use `git clone` for it, if we made changes on the code, it would not be directly update that repository since that does not belong to us. So we need to fork the repository first then we clone it.

## Merging Branch

- If we want to merge into the original branc. We first need to switch to that branch before doing `git merge <branch name>`. The branch name is the one we want to merge into our original branch.

## Notes

- We can combine the commands using `&&`. This tells the terminal to do the next command after initiating the first one.
  - example: `git add -A && git commit -m "<message>" && git push origin <branch name>`
