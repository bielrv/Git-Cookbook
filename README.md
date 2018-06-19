# git-cookbook [![Build Status](https://travis-ci.org/bielrv/git-cookbook.png?branch=master)](https://travis-ci.org/bielrv/git-cookbook)

This repository contains instructions and information on how to use github.

>Git is the open source distributed version control system that facilitates GitHub activities on your laptop or
desktop. This cheat sheet summarizes commonly used Git command line instructions for quick reference.

1. [Git schema](#1)
1. [Git files](#2)
1. [Start a new Git repository for an existing code base](#3)
1. [Removing folder from remote repository](#4)
1. [Git cheat sheet](#5)
   * [Create repositories](#5.1)
   * [Make changes](#5.2)
   * [Group Changes](#5.3)
   * [Review history](#5.4)
   * [Synchronize changes](#5.5)
1. [Useful options](#6)
1. [Git Setup](#7)
1. [Git Configuration](#8)
1. [Definitions](#9)
***

# <a id="1"></a> 1. Git schema 

![](git-schema.png?raw=true)

Note that files are not being transfered but logs of changes (commits). This is one of the most interesting things about Git. A commit is a set of changes to the code.

***

# <a id="2"></a> 2. Git files

- [x] .git -> The Git repository is stored in the same directory as the project itself, in a subdirectory called .git.
- [x] readme.md -> Generates the html summary you see at the bottom of projects
- [x] .gitignore -> Specifies intentionally untracked files to ignore 
- [x] license -> Allows an open source license in the repository to make it easier for other people to contribute

# <a id="3"></a> 3. Start a new Git repository for an existing code base
```shell
cd /path/to/my/codebase
git initk
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

# <a id="4"></a> 4. Removing folder from remote repository
*This will not remove the folder from your local repository*
```shell
git rm -r --cached FolderName
git commit -m "Removed folder from repository"
git push origin master
```
**Use** `.gitignore` **to ignore that folder in future commits**

***

# <a id="5"></a> 5. Git cheat sheet 

## Create repositories </a>
*Start a new repository or obtain one from an existing URL*\
`git init [project-name]` creates a **new local repository** with the specified name\
`git clone [url]` downloads an **existing project** and its entire version history

***

##  <a id="5.1"></a>  Make changes 
*Review edits and craf a commit transaction*\
`git status` lists all new or modified files to be commited\
`git diff` shows changes between commits\
`git add [file]` snapshots the file in preparation for versioning\
`git diff --staged` shows file differences between staging and the last file version\
`git reset [file]` unstages the file, but preserve its contents\
`git commit -m "[descriptive message]"` records file snapshots permanently in version history

***

## <a id="5.2"></a> Group Changes 
*Name a series of commits and combine completed efforts*\
`git branch` lists all local branches in the current repository\
`git branch [branch-name]` creates a new branch\
`git checkout [branch-name]` switches to the specified branch and updates the working directory\
`git merge [branch]` combines the specified branch’s history into the current branch\
`git branch -d [branch-name]` deletes the specified branch

***

## <a id="5.3"></a> Refactor filenames 
*Relocate and remove versioned files*\
`git rm [file]` deletes the file from the working directory and stages the deletion\
`git rm --cached [file]` removes the file from version control but preserves the file locally\
`git mv [file-original] [file-renamed]` changes the file name and prepares it for commit

***

## <a id="5.4"></a> Review history
*Browse and inspect the evolution of project files*\
`git log` lists version history for the current branch\
`git log --follow [file]` lists version history for a file, including renames\
`git diff [first-branch]...[second-branch]` shows content differences between two branches\
` git show [commit]` outputs metadata and content changes of the specified commit

***

## <a id="5.5"></a> Synchronize changes
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

# <a id="6"></a> 6. Usefull options

Option | Description
------------ | -------------
**--version**|Prints the Git suite version that the git program came from.
**--help**|Prints the synopsis and a list of the most commonly used commands.
**--force**|Useful when repo refuses to update a remote repo. Usually due to ref.
**--hard**|Clears staging area and rewrites working tree from a commit when used with reset.
**--verbose**|Be a little more verbose.
**--global**|Applies to all repositories.
**--local**| Write/read to the repository .git/config (default)
**--stats**|Show all commit logs with indications when used with log.
**--follow**|Shows a file changes even across renames when used with log.

[more options here](https://git-scm.com/docs/git-config)

# <a id="7"></a> 7. Git Setup
`git config --global user.name "[firstname lastname]"` sets a name that is identifiable for credit when review version history
`git config --global user.email "[valid.email]"` sets an email address that will be associated with each history marker
`git config --global color.ui auto` sets automatic command line coloring for GIt for easy reviewing

[Useful git cheat sheet PDF](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)

# <a id="8"></a> 8. Git Configuration
`--replace-all` Default behavior is to replace at most one line. This replaces all lines matching the key (and optionally the value_regex).  
`--add`  Adds a new line to the option without altering any existing values. This is the same as providing ^$ as the value_regex in `--replace-all`

# <a id="9"></a> 9. Definitions
## Branch
A branch is a parallel version of a repository. It is contained within the repository, but does not affect the primary or master branch allowing you to work freely without disrupting the "live" version. When you've made the changes you want to make, you can merge your branch back into the master branch to publish your changes.

## Clone
A clone is a copy of a repository that lives on your computer instead of on a website's server somewhere, or the act of making that copy. With your clone you can edit the files in your preferred editor and use Git to keep track of your changes without having to be online. It is, however, connected to the remote version so that changes can be synced between the two. You can push your local changes to the remote to keep them synced when you're online.

## Commit
A commit, or "revision", is an individual change to a file (or set of files). It's like when you save a file, except with Git, every time you save it creates a unique ID (a.k.a. the "SHA" or "hash") that allows you to keep record of what changes were made when and by who. Commits usually contain a commit message which is a brief description of what changes were made.

## Contributor
A contributor is someone who has contributed to a project by having a pull request merged but does not have collaborator access.

## Fetch
Fetching refers to getting the latest changes from an online repository without merging them in. Once these changes are fetched you can compare them to your local branches (the code residing on your local machine).

## Fork
A fork is a personal copy of another user's repository that lives on your account. Forks allow you to freely make changes to a project without affecting the original. Forks remain attached to the original, allowing you to submit a pull request to the original's author to update with your changes. You can also keep your fork up to date by pulling in updates from the original.

## Git
Git is an open source program for tracking changes in text files, and is the core technology that GitHub, the social and user interface, is built on top of.

## Issue
Issues are suggested improvements, tasks or questions related to the repository. Issues can be created by anyone (for public repositories), and are moderated by repository collaborators. Each issue contains its own discussion forum, can be labeled and assigned to a user.

## Markdown
Markdown is a simple semantic file format, not too dissimilar from .doc, .rtf and .txt. Markdown makes it easy for even those without a web-publishing background to write prose (including with links, lists, bullets, etc.) and have it displayed like a website. GitHub supports Markdown.

## Merge
Merging takes the changes from one branch (in the same repository or from a fork), and applies them into another. This often happens as a pull request (which can be thought of as a request to merge), or via the command line. A merge can be done automatically via a pull request via the GitHub web interface if there are no conflicting changes, or can always be done via the command line.

## Pull
Pull refers to when you are fetching in changes and merging them. For instance, if someone has edited the remote file you're both working on, you'll want to pull in those changes to your local copy so that it's up to date.

## Pull request
Pull requests are proposed changes to a repository submitted by a user and accepted or rejected by a repository's collaborators. Like issues, pull requests each have their own discussion forum.

## Push
Pushing refers to sending your committed changes to a remote repository, such as a repository hosted on GitHub. For instance, if you change something locally, you'd want to then push those changes so that others may access them.

## Remote
This is the version of something that is hosted on a server, most likely GitHub. It can be connected to local clones so that changes can be synced.

## Repository
A repository is the most basic element of GitHub. They're easiest to imagine as a project's folder. A repository contains all of the project files (including documentation), and stores each file's revision history. Repositories can have multiple collaborators and can be either public or private.

## SSH key
SSH keys are a way to identify yourself to an online server, using an encrypted message. It's as if your computer has its own unique password to another service. GitHub uses SSH keys to securely transfer information to your computer.

## Upstream
When talking about a branch or a fork, the primary branch on the original repository is often referred to as the "upstream", since that is the main place that other changes will come in from. The branch/fork you are working on is then called the "downstream".

