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

// local branch
git branch -d branch-name

// remote branch
git push origin --delete branch-name
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
