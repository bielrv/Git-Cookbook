# git-cookbook
This repository contains instructions and information on how to use github.

>Git is the open source distributed version control system that facilitates GitHub activities on your laptop or
desktop. This cheat sheet summarizes commonly used Git command line instructions for quick reference.

1. Git schema
1. Start a new Git repository for an existing code base
1. Git cheat sheet
   * Create repositories
   * Make changes
   * Group Changes
   * Review history
   * Synchronize changes

# 1. Git schema

![](git-schema.png?raw=true)

# 2. Start a new Git repository for an existing code base
```shell
cd /path/to/my/codebase
git init
git add .
git commit
```
Creates an empty .git file in current repository or reinitialize an existing one.
```shell
git init
```
Add all existing files to the index.
```shell
git add .
```
Record the pristine state as the first commit in the history.
```shell
git commit -m "First commit"
```

Add remote repository to local repository.
```shell
git remote add origin remote repository URL
# Sets the new remote
git remote -v
# Verifies the new remote URL
```

***
# 3. Git cheat sheet

## Create repositories
*Start a new repository or obtain one from an existing URL*\
`git init [project-name]` creates a **new local repository** with the specified name\
`git clone [url]` downloads an **existing project** and its entire version history

***

## Make changes
*Review edits and craf a commit transaction*\
`git status` lists all new or modified files to be commited\
`git diff` shows changes between commits\
`git add [file]` snapshots the file in preparation for versioning\
`git diff --staged` shows file differences between staging and the last file version\
`git reset [file]` unstages the file, but preserve its contents\
`git commit -m "[descriptive message]"` records file snapshots permanently in version history

***

## Group Changes
*Name a series of commits and combine completed efforts*\
`git branch` lists all local branches in the current repository\
`git branch [branch-name]` creates a new branch\
`git checkout [branch-name]` switches to the specified branch and updates the working directory\
`git merge [branch]` combines the specified branch’s history into the current branch\
`git branch -d [branch-name]` deletes the specified branch

***

## Refactor filenames
*Relocate and remove versioned files*\
`git rm [file]` deletes the file from the working directory and stages the deletion\
`git rm --cached [file]` removes the file from version control but preserves the file locally\
`git mv [file-original] [file-renamed]` changes the file name and prepares it for commit

***

## Review history
*Browse and inspect the evolution of project files*\
`git log` lists version history for the current branch\
`git log --follow [file]` lists version history for a file, including renames\
`git diff [first-branch]...[second-branch]` shows content differences between two branches\
` git show [commit]` outputs metadata and content changes of the specified commit

***

# Synchronize changes
*Register a repository bookmark and exchange version history*\
`git fetch [bookmark]` downloads all history from the repository bookmark\
`git merge [bookmark]/[branch]` combines bookmark’s branch into current local branch\ 
`git push [alias] [branch]` uploads all local branch commits to GitHub\
`git pull` downloads bookmark history and incorporates changes

***

`git-clean` removes untracked files from the working tree\
`git-gc` cleans up unnecessary files and optimize the local repository\
`git-gui` is a portable graphical interface to Git\
`git-merge` joins two or more development histories together\
`git-rm` removes files from the working tree and from the index\
`git-worktree` manages multiple working trees

***

# Usefull options

Option | Description
------------ | -------------
**--version** | Prints the Git suite version that the git program came from.
**--help**| Prints the synopsis and a list of the most commonly used commands.

[Useful git cheat sheet PDF](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
