Branching in-flight
================================

### Create a branch "qyuckfix" and move to that branch
    
    $ git checkout -b quikcfix

### Stage the changes

    $ git add *    

### Commit the changes in the quickfix branch

    $ git commit -m "start of changes for quickfix"

### stage and commit changes in single command

    $ git commit -a -m "start of changes for quickfix"

### Master is now clean and changes are saved in "quickfix" branch

    $ git checkout master

### Switch back to the quickfix branch

    $ git checkout quickfix


Moving from Branch to Branch
====================================

### List your branches

    $ git branch

### Switch to work in a different branch

    $ git checkout <branch-name>

### Renaming a Brach 

    $ git branch -m <oldbranch> <newbranch>

### delete a branch

    $ git branch -d <branchname>

- error message if unmerged commits

    $ git branch -D <branchname>

- force delete the branch

Merging Made Easy
====================

- target branch - master
- source branch - solution branch

### First Switch to target branch

    git checkout <target-branch>

### merge surce branch

    git merge <source-branch>

### merge example

    git checkout master

    git merge ticket1

### Compare branches

    git diff <branch1> <branch2>

    git diff master ticket1

## Rebase and Squash
    
### See the branch history

    git log --oneline

### Get the original base of the "ticket1" branch created from master

    git merge-base ticket1 master

### Start the rebase from the commit sha

    git rebase -i <commit-sha>

## Using Cherry Pick

### Find the commit you want

    git log --oneline

    git log <branch-name> --oneline

### Where do you want to put the commit? Checkout that branch

    git checkout <branch-name>

### Perform the cherry-pick to append the commit to HEAD

    git cherry-pick <sha-from-othwe-branch-commit>

    git cherry-pick <commit>

## git branches with Team

### Remote URL

    https://service.com/project/a.git

### pull code and set up local branch

    git clone <remote-url>

### Default name for remote server

    origin

### Provide the name for a remote server

    git remote add <name> <remote-url>

### List remotes and URLs

    git remote -v

### check status with remote 

    git status

### pushing changes to remote

    git push

### pulling from remote repo

    git pull

- git pull is a fetch and merge all in one
    
### abort merge

    git merge --abort

## Remotes with branches

### push local branch to remote

    git push -u origin feature4

### To see the branches that are in remote

    git ls-remote

### to fetch feaure4 from master

    git fetch origin feature4

### to list all branches from remote

    git branch -a

 ### to setup a branch in local repository that will track the remote repo

    git checkout --track origin/feature4   

## Git Diff

### changed and not staged for commit

    git diff

### What is changed and staged for commit

    git diff --cached   (git commit)

### What is changed since last commit

    git diff Head       (git commit -a)

Commit diff
===================

### Specific Commit and current

    git diff <commit>

### Specific Commit and staged

    git diff --cached <commit>

### Difference between two commits

    git diff <commit> <commit>

Branch diff
===============

### Difference between tips of branches

    git diff feature master

### Chnaged in master since feature was started off of it

    git diff feature...master

### Difference in file.txt on two branches

    git diff feature master file.txt












    


     





