# Git Cheat Sheet Manual

---

## Table of Contents
1. [Git Add, Reset, and Commit](#git-add-reset-and-commit)
2. [Push Local Changes to Remote Repository](#git-push-local-changes-to-remote-repo)
3. [Pull Changes from Remote Repository](#git-pull-changes-from-remote-repository)
4. [Git Configurations](#git-configurations)
5. [Git Branching and Merging](#git-branching-and-merging)
6. [Git Stash](#git-stash)
7. [Restore and Clean](#git-restore-and-clean)
8. [Resetting the Head](#git-resetting-the-head)
9. [Ignoring Files and Directories](#git-ignoring-files-and-directories-gitignore)
10. [Tagging and Releasing](#git-tagging-and-releasing)

---

## Git Add, Reset, and Commit

- **`git init`**: Initialize a local `.git` repository.
- **`git add`**: Add files to the staging area (start tracking files).
- **`git commit -m`**: Move your staged files to the local repository with a message.
- **`git reset HEAD <filename>`**: Unstage the specified file, removing it from the staging area.
- **`git status`**: Check the current local Git status.

> **Tip**: You can commit multiple times before pushing:
> ```bash
> git add .
> git commit -m "Commit 1"
> touch newfile.txt
> git add newfile.txt
> git commit -m "Add newfile.txt"
> git push
> ```

---

## Push Local Changes to Remote Repo

- **`git branch`**: List all local branches.
- **`git remote -v`**: Display the remote repository URLs.
- **`git push origin <branchname>`**: Push local changes to the remote repository.
- **`git push -u origin <branchname>`**: Pull remote changes first, then push to avoid remote conflicts.
- **`git push --force`**: Force push to the current branch, overriding conflicts (use cautiously).

---

## Pull Changes from Remote Repository

- **`git clone <remote-url>`**: Clone a remote repository to your local machine.
- **`git pull origin`**: Pull remote changes to your local repository (combines `git fetch` and `git merge`).

---

## Git Configurations

- **Types of Configurations**: Local and Global.
- **Commands**:
  - `git config --list`: Show all configurations.
  - `git config user.name`: Display the current Git username.
  - `git config [--local | --global] --unset user.name`: Remove the stored username.
  - `git config [--local | --global] --edit`: Open the config file in an editor.

---

## Git Branching and Merging

- **Branch Commands**:
  - `git branch`: List all local branches.
  - `git branch <branchname>`: Create a new branch.
  - `git checkout <branchname>`: Switch to the specified branch.
  - `git branch -d <branchname>`: Safely delete a branch.
  - `git branch -D <branchname>`: Force delete a branch.
  - `git merge <source-branch>`: After checkout from source-branch, this merge source-branch with the curret-branch
  - `git rebase <source-branch>`: After checkout from source-branch, incorporate the latest updates from source-branch into your current-branch without creating a merge commit.

---

## Git Stash

- **Commands**:
  - `git stash`: Save uncommitted changes in a stash.
  - `git stash list`: Show all stashes.
  - `git stash pop`: Restore and remove the latest stash.
  - `git stash apply`: Apply stash without removing it.
  - `git stash drop`: Delete a stash (cannot be restored).

> **Note**: Operations like `pop`, `drop`, etc., follow a Last In, First Out (LIFO) approach.

---

## Restore and Clean

- **Restore Commands**:
  - `git restore <filename>`: modifies or restores changes in your working directory, eg: reverting edits or restoring a deleted file(without unstaging).
  - `git restore --staged <filename>`: Unstage the specified file.
  - `git restore --staged`: Unstage all files.

- **Clean Commands**:
  - `git clean -n`: Preview untracked files/directories to be removed.
  - `git clean -f`: Force remove untracked files.

---

## Resetting the Head

- **Reset Types**:
  - `git reset --soft HEAD~1`: Undo the last commit; keep changes staged.
  - `git reset --mixed HEAD~1`: Undo the last commit; keep changes unstaged.
  - `git reset --hard HEAD~1`: Undo the last commit; discard all changes.

---

## Ignoring Files and Directories (.gitignore)

- **Description**: Add untrackable files or directories in a `.gitignore` file.
- **Example**:
  - To ignore `node_modules/`:
    ```
    node_modules/
    ```

---

## Tagging and Releasing

- **Tag Types**:
  - **Lightweight Tags**: Directly associate a tag with a commit (simple).
  - **Annotated Tags**: Add a message with the tag for more details.
- **Commands**:
  - `git tag <tagname>`: Create a lightweight tag.
  - `git tag -a <tagname> -m "Tag message"`: Create an annotated tag.
  - `git tag`: List available tags.
  - `git push origin <tagname>`: Push a tag to the remote repository.
  - `git tag -l <tagname>`: list all the tag in specified tagname, eg: git tag -l "v1.*" => this will list all first the versions[v1.0 - v1.9].
  - `git tag -d <tagname>`: deletes the specified tag locally.
  - `git push origin --delete <tagname>`: deletes the specified tag remotly.

---

[For more details, refer to the online course material.](https://elzero.org/learn-git-and-github/)
