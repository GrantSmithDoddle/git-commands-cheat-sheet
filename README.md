# Git Commands Cheat Sheet

A list of useful commands and some examples use cases at the end.

## Basic

### Initialise a new Git repository:

    $ git init

### Set configuration for values for username and email:

    $ git config --global user.name <your-name>
    $ git config --global user.email <email>

### Clone a repository:

    $ git clone <repository-url>

### Add a file to the staging area:

    $ git add <file>

### Add all files changes to the staging area:

    $ git add .

### Check the un-staged changes:

    $ git diff

### Commit the staged changes:

    $ git commit -m "<commit-message>"

### Reset staging area to the last commit:

    $ git reset

### Check the state of the working directory:

    $ git status

### Remove a file from the index and working directory:

    $ git rm <file>

### List the commit history:

    $ git log

### List the last two items from commit history (change number to suit):

    $ git log -2

### Check the metadata and content changes of the commit:

    $ git show <commit-hash>

## Branches

### List all local branches:

    $ git branch

### Create new branch:

    $ git branch <branch-name>

### Rename the current branch:

    $ git branch -m <new-branch-name>

### Delete a branch:

    $ git branch -d <branch-name>

### Switch branch:

    $ git checkout <branch-name>

### Merge specified branch into current branch:

    $ git merge <branch-name>

## Push and Pull

### Create new connection to a remote repository:

    $ git remote add <name> <repository-url>

### Push the committed changes to a remote repository:

    $ git push <remote> <branch>

### Download the content from a remote repository:

    $ git pull <remote>

### Clean-up unnecessary files and optimise the local repository:

    $ git gt

## Stash

### Temporarily remove uncommitted changes and save them for later:

    $ git stash

### Reapply previously stashed changes

    $ git stash apply

## Example use cases

### A new repo from scratch on local machine:

    $ git init
    $ git add .
    $ git commit -m "<commit-message>"

### Merge from develop into main branch and tag the release:

In this example I have two branches, `main`, this is the production area we wish to protect. `develop` is our working branch that we are coding on.

On your development repo, ensure that all changes in `develop` have been committed and pushed.

Merge `develop` into your local `main` branch and tag with the version number:

    $ git checkout main
    $ git pull -v
    $ git merge --no-ff --no-edit develop
    $ git tag -a v1.3.1 -m "Release 1.3.1"

Now push these changes to Github:

    $ git push
    $ git push origin v1.3.1
