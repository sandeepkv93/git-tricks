# Table of Contents
1. [Set local feature branch exactly same as remote main branch](#set-local-feature-branch-exactly-same-as-remote-main-branch)
2. [Reset only one file same as origin main](#reset-only-one-file-same-as-origin-main)
3. [Delete all the local branches other than main](#delete-all-the-local-branches-other-than-main)
4. [Move a file from staging area to working copy](#move-a-file-from-staging-area-to-working-copy)
5. [Uncommit the last commit](#)
6. [git clean command variations](#git-clean-command-variations)

# Set local feature branch exactly same as remote main branch
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

# Reset only one file same as origin main
To reset only one file to match the version in the remote main branch, you can use the following command:
```sh
git checkout origin/main -- path/to/file
```
Replace path/to/file with the actual path and filename of the file you want to reset. This command will retrieve the latest version of the file from the remote main branch and overwrite your local changes.

# Delete all the local branches other than main
To delete all local branches other than main, you can use the following command:
```sh
git branch | grep -v "main" | xargs git branch -D
```
This command first lists all the local branches using git branch. Then it filters out the branch main using grep -v "main". Finally, it deletes all the remaining branches using xargs git branch -D.

# Move a file from staging area to working copy
To move a file from the staging area to the working directory in Git, you can use the git restore command with the --staged option. Here are the steps:

1. Check the status of your working directory using the git status command. This will show you the files that have been modified or staged.

2. Identify the file that you want to move from the staging area to the working directory.

3. Use the git restore command with the --staged option and the path to the file you want to move:
```sh
git restore --staged path/to/file
```
This command will remove the file from the staging area and copy it back to the working directory.

4. Verify that the file has been moved to the working directory by running the git status command again. You should see that the file is now listed as "not staged for commit".

# Uncommit the last commit
To uncommit the last commit in Git, you can use the git reset command with the --soft or --mixed option. Here are the steps:

1. Open your terminal and navigate to the local repository where you want to uncommit the last commit.

2. Run the following command to undo the last commit:
```sh
git reset HEAD~
```
This will move the HEAD pointer back one commit, effectively "uncommitting" the last commit.

3. If you want to keep the changes you made in the last commit, use the --soft option:
```sh
git reset --soft HEAD~
```
This will move the HEAD pointer back one commit and leave the changes from the last commit in the staging area.

4. If you want to remove the changes you made in the last commit completely, use the --mixed option:
```sh
git reset --mixed HEAD~
```
This will move the HEAD pointer back one commit and remove the changes from the last commit from the staging area.

5. Verify that the last commit has been undone by running the git log command. You should see that the last commit is no longer in the commit history.

# git clean command variations
The git clean command is used to remove untracked files from your working directory. Here are some variations of the git clean command:
1. Clean untracked files:
```sh
git clean
```
This command removes all untracked files from the working directory.

2. Clean untracked files and directories recursively:
```sh
git clean -d
```
This command removes all untracked files and directories from the working directory, including empty directories.

3. Preview files to be cleaned:
```sh
git clean -n
```
This command shows a preview of the files and directories that would be removed if the git clean command were run without the -n flag.

4. Force clean untracked files:
```sh
git clean -f
```
This command forces the removal of untracked files from the working directory without prompting for confirmation.

5. Clean untracked files and ignored files:
```sh
git clean -x
```
This command removes all untracked files and directories, including those that are ignored by Git.

6. Clean untracked files and directories interactively:
```sh
git clean -i
```
This command interactively prompts you to confirm which files and directories you want to remove.

7. Clean untracked files and directories from a specific path:
```sh
git clean -d path/to/directory/
```
This command removes all untracked files and directories recursively from the specified directory.
