Git Cheatsheet
===============

# Table of Contents
- [Branch Management](#Branch-Management)
- [Git Push/Pull Errors](Git-pull-and-push-errors)

# Branch Management

## Create a new branch

```
git branch branch_name
```

Replace `branch_name` with the name of your branch.

## Delete/remove a branch

```
git branch -d branch_name
```

Replace `branch_name` with the name of your branch.

## Push a new branch

```
git push --set-upstream origin branch_name
```

Replace `branch_name` with the name of your branch.

## Rename a branch

```
git branch -M oldbranch_name newbranch_name
```

Replace `oldbranch_name` and `newbranch_name` with the old and new names of your branch.

# Git pull and push errors

Sometimes when attempting to push or pull to or from a remote repository you might run into an error indicating that there are issues between the local commits and the remote commits.  This can be frustrating.  However, there is an easy fix to merge the most current commits.

## Step 1

The first thing we are going to do is run:

```
git fetch --all
```

What this command does is fetch all of the changes on the remote branch to your local machine.
When you view a file it will show you your changes and the remote changes.
So then we need to run this command:

```
git reset --hard origin/branch_name
```

This will bring the branch you are working in up to date to the state of the remote branch.
Simply change `branch_name` to the name of your branch.


