Branching in-flight
================================

### Create a branch "qyuckfix" and move to that branch
    
    $ git checkout -b quikcfix

### Stage the changes

    $ git add *

### Commit the changes in the quickfix branch

    $ git commit -m "start of changes for quickfix"

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

### example

    git checkout master

    git merge ticket1





