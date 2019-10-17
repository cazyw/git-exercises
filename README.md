# Git Exercises

Resources:

- https://dev.to/unseenwizzard/learn-git-concepts-not-commands-4gjc

- https://explainshell.com (e.g. https://explainshell.com/explain?cmd=git+log+--all+--graph+--decorate+--oneline)

## Commands

### Clone

```
git clone https://github.com/cazyw/git-exercises
```

### Adding Files

```
// add all changes in working directory whether files are tracked or untracked
git add .
git add -A (or --All)

// only add changes to files that are tracked, ignore untracked files
git add -u (--update)

// for changes in tracked files in the working directory,
// iterate through chunks to add or ignore
git add -A -p (--patch)
```

### Committing files

```
// commit and also add a message
git commit -m "50 character subject

and additional text to explain why changes are required
if necessary"

// amend a commit
git commit --amend

// to force push an amended commit to the remote (WARNING)
git push -f
```

### Discarding changes

```
// discard changes to an unstaged file
git checkout -- <file>

// discard changes to a staged file
git reset HEAD <file>

// discard all changes in staged area
git reset HEAD
```

### Checking difference

```
// for tracked files, show changes in the working directory not yet staged
git diff

// show changes in staged area (this may be different to what is in the working directory)
git diff --staged
or
git diff --cached

// compare the differences between two commits
git diff commitA commitB
```

### Logs

```
// show previous commit messages
git log

// show each commit in one line
git log --oneline

// show branch lines
git log --graph

// show refs e.g origin/master or refs/remotes/origin/master)
git log --decorate (--decorate=short [default] --decorate=full)

git log --all --graph --decorate --oneline
```

### Tracking Files

```
// show files git is tracking
git ls-files

// show files git is not tracking
 git ls-files -o

```

### Branches

```
// list all branchs (local and remote)
git branch -a

// create branch
git branch branch-name

// create branch and switch to it
git checkout -b branch-name

// switch between branches
git checkout branch-name

// delete local branch
git branch -d branch-name

// delete remote branch
git push origin -d branch-name

// pull down a remote branch
// this creates a local branch that tracks the remote branch specified
git checkout -t origin/remote-branch

```

### Aliases

```
// adding alias commands
git config --global alias.lg "log --oneline --graph --all"
```

# Rebase

Use this if you have been working locally and have not already pushed up your branch

```
// rewind back to the base (point where branch started)
// moves to the tip of the master branch
// add the feature branch commits
git rebase master
```

### Undos

Roll back any changes in working tree

```
// discard any changes for a file or pattern
// (roll back to last commit state for this file)
git checkout -- file.txt
git checkout -- file*
```

Unstage files

```
// unstage all the files
git reset HEAD

// unstage one file
git reset HEAD file.txt

// roll back to the state as at previous commit
// not only unstages but deletes changes and new files that are tracked
// any untracked changes remain as is
git reset HEAD --hard
```

Roll back committed changes (that have been pushed) and do not change history

```
// roll back the last change
// (inverse the changes and create a new commit)
git revert HEAD

// if there are issues with reverting
git revert --abort

// roll back the last 2 commits
// inverse the changes one at a time and commit the changes one at a time
git revert HEAD~2..

// roll back the last 3 commits
// this will leave the changes in the working tree
// you will then be able to lummp these changes into the one change commit
git revert --no-commit HEAD~3..
git revert --continue

```
