# Git Commands Cheat Sheet

A list of useful commands and some examples use cases at the end.

## Content

[Initialise a new Git repository](#initialise-a-new-git-repository)  
[Set configuration for values for username and email](#set-configuration-for-values-for-username-and-email)  
[Clone a repository](#clone-a-repository)  
[Add a file to the staging area](#add-a-file-to-the-staging-area)  
[Check the un-staged changes](#check-the-un-staged-changes)  
[Commit the staged changes](#commit-the-staged-changes)  
[Reset staging area to the last commit](#reset-staging-area-to-the-last-commit)  
[Check the state of the working directory](#check-the-state-of-the-working-directory)  
[Remove a file from the index and working directory](#remove-a-file-from-the-index-and-working-directory)  
[List the commit history](#list-the-commit-history)  
[List the last two items from commit history](#list-the-last-two-items-from-commit-history)  
[Check the metadata and content changes of the commit](#check-the-metadata-and-content-changes-of-the-commit)  
[List all local branches](#list-all-local-branches)  
[Create new branch](#create-new-branch)  
[Rename the current branch](#rename-the-current-branch)  
[Delete a branch](#delete-a-branch)  
[Switch branch](#switch-branch)  
[Merge specified branch into current branch](#merge-specified-branch-into-current-branch)  
[Create new connection to a remote repository](#create-new-connection-to-a-remote-repository)  
[Push the committed changes to a remote repository](#push-the-committed-changes-to-a-remote-repository)  
[Download the content from a remote repository](#download-the-content-from-a-remote-repository)  
[Clean-up unnecessary files and optimise the local repository](#clean-up-unnecessary-files-and-optimise-the-local-repository)  
[Temporarily remove uncommitted changes and save them for later](#temporarily-remove-uncommitted-changes-and-save-them-for-later)  
[Reapply previously stashed changes]#reapply-previously-stashed-changes  
[A new repo from scratch on local machine](#a-new-repo-from-scratch-on-local-machine)  
[Merge from develop into main branch and tag the release](#merge-from-develop-into-main-branch-and-tag-the-release)

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
    $ gh repo create

Take note of your repository name as this will form the URL required in the next steps.

Now we need to connect our local directory with the newly created git repository.

    $ git remote add origin <git-url-repository-name>
    $ git branch -M <branch>
    $ git push -u origin <branch>

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
