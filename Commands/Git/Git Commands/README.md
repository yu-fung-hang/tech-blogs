# Git Commands

## Scenario 1: Conflict

You are about to commit a change, but you notice that someone has modified the same file, which makes you unable to proceed.   

### Solution:

1. `git stash`: stash your code locally, and return the project to the last commit.
2. `git pull`: pull commits.
3. `git stash pop`: auto-merge the conflicted files.

## Scenario 2: Return back to a historical version

You have pushed commits to the remote branch but now you want to return back to a historical version.

### Solution:

1. `git reset --hard ` + commitId.
2. `git push -f -u origin master`.

## Scenario 3: Create a new branch and push it to remote

1. `git checkout -b new-branch-name`: create a new local branch.
2. `git push origin new-branch-name`: push this branch to remote.

## Scenario 4: Ignore files in .idea directory

1. `git rm -r --cached .idea`: disable the change tracking of the files in .idea directory.
2. Create a **.gitignore** file in your project's root directory with the following content: `.idea/`

## Scenario 5: Overlap branch A from B

1. `git checkout A`;
2. `git reset --hard B`;
3. `git push A --force`;

## Scenario 6: Rebase branch1 onto branch2

It does an automatic checkout of `branch1`, and then modifies the commits in `branch1`. `branch2` remains unchanged.

## Scenario 7: Set remote origin

```
git remote set-url origin project-url
```