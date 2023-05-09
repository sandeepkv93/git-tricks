# Table of Contents
1. [Set local feature branch exactly same as remote main branch](#set-local-feature-branch-exactly-same-as-remote-main-branch)
2. [Reset only one file same as origin main](#reset-only-one-file-same-as-origin-main)
3. [Delete all the local branches other than main](#delete-all-the-local-branches-other-than-main)

## Set local feature branch exactly same as remote main branch
Assuming the remote name is 'origin'
1. Make sure you are on your feature branch by running the following command:
```sh
git checkout feature-branch
```
2. Fetch the latest changes from the remote repository:
```sh
git fetch origin
```
3. Reset your local feature branch to match the remote main branch:
```sh
git reset --hard origin/main
```
This will reset your local feature branch to match the latest commit on the remote main branch, discarding any local changes you have made.

4. If you want to update the remote feature-branch with your local changes, you can force-push your changes to the remote repository:
```sh
git push --force origin feature-branch
```
This will update the remote feature-branch with your local changes, which now include the latest changes from the remote main branch.

## Reset only one file same as origin main
To reset only one file to match the version in the remote main branch, you can use the following command:
```sh
git checkout origin/main -- path/to/file
```
Replace path/to/file with the actual path and filename of the file you want to reset. This command will retrieve the latest version of the file from the remote main branch and overwrite your local changes.

## Delete all the local branches other than main
To delete all local branches other than main, you can use the following command:
```sh
git branch | grep -v "main" | xargs git branch -D
```
This command first lists all the local branches using git branch. Then it filters out the branch main using grep -v "main". Finally, it deletes all the remaining branches using xargs git branch -D.
