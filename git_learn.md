## Git Add And Reset And Commit
git init => init local .git repo
git add => add files to the staging area(start traking files)
git commit -m => move your staged files to the local repo with a message
git reset head filename => unstage the specified file, remove it from the staging area
git status => git local status

NOTE => you can do multiple commits before push:
eg => 
git add .
git commit -m "msg"
touch somefile.txt
// we need to include the newly created somefile.txt to the local-repo before push, fix:
git add somefile.txt
git commit -m "created somefile.txt"
// then
git push

## Git Push Local Changes To Remote Repo
git branch => list all the local branches
git remote -v => show the the remote repo url
git push origin branchname => push from loca repo to remote repo
git push -u origin branchname => pull from remote to local then push from local to remote, this saves you from causing confilcts in the remote repo, but it may cause conflicts in the local repo[fix the conflicts and push a clean push]
git push --force => force push to the remote branch you are in, whethere you have conflicts or not

## Git Pull Changes From Remote Repository
git clone remoteurl => clone remote repo to local
git pull origign => pull remote changes to the local, this do two things (git fetch and git remge[remote changes with local changes])

## Git Configurations
NOTE: there are two types of config: [local and global]
git config --list => list all the .git configurations
git help config => opens git config manual page
git config user.name => show the current git username
git config --local user.name => show the current git username for the current local repo you are in
git config --global user.name => show the current git username globally for all the user's projects
git config user.name "name" => set the current git username
NOTE: you can get|set email in this logic
git config [--local | --global | or leave empty] --unset user[.name | .email] => unset the stored value for the specified properity
git config [--local | --global | or leave empty] --edit => opens the config file in your editor

## Git Branching And Merging
git branch => list all the local branches
git branch brnachname => create new local branch
git checkout branchname => switches to the given branch
git checkout -b branchname => create and switches to the given branch
git branch -d branchname => delete the given branch, safe delete
git branch -D branchname => delete the given branch, force[unsafe] delete
git branch -m newbranchname => rename the current branch

## Git Stash[lifo => last in first out]
NOTE => if you don't specify the stash id then it will pop, push, drop, ... in lifo manner
git stash => stores your changes in a stash
git stash list => list the all the stashed changes, with there ids
git stash pop => pop the stashed changes from stash and move them to the staging area, removing the changes from the stash list
git stash pop stash@{id} => pop stash with the specified id
git stash apply => move the stashed change to the staging area, leaving a copy in the stahing area
git stash push "msg" => stores your changes in a stash with a stash message
git stash drop => drop the last stashed change
git stash drop stash@{id} => drop stash with the specified id
NOTE: git stash drop, drops the changes completly[it can not be restored]
git stash show => show the details for the stash, eg: stash contents, like [git log]
git stash clear => clear the stash files completly

## Git Restore And Clean
git restore --staged filename => unstage the specified file, restore from staging area[untrak file]
git restore --staged . => unstage all the staged files
git clean -n => preview the untracked files and directories that would be removed without actually deleting them.
git clean -f => force removes untracked files from the working directory.

## Git Resetting The Head [you can replace the HEAD~1 with the commit hash]
git reset --soft HEAD~1 => Undo the last commit, keep changes staged
git reset --mixed HEAD~1 => Undo the last commit, keep changes unstaged
git reset --hard HEAD~1 => Undo the last commit, discard changes entirely
NOTE: if you want to discard HEAD~2 changes and Moves the HEAD pointer to HEAD~1, use one of the three commands above

## Git Ignoring Files And Directories(.gitignore)
Descbrtion: a file under the name of .gitignore and all the file paths, dirs, ... you mention in this file can't be traked by git
NOTE: check [git igone patterns] to learn more about git ignore
git add --force filename => force add the specified file to the staging area(start traking) if the specified file is ignored

## Git Tagging And Releasing(used for versioning, eg: beta version[v1.0.0])
NOTE: there are two types of tags:
- light weight tag => takes it's infos from the commit, eg: message
- annotated tag => you can use it to specify the tag infos, eg: message => git tag -a tagname -m "msg"
git tag tagname => create a new tag with the specified named and the associated commit
git tag => show the available tags
git push origin tagname => push the newly created tag to the remote repo
git tag -l tagname => list all the tag in specified tagname, eg: git tag -l "v1.*" => this will list all first the versions[v1.0 - v1.9]
git tag -d tagname => deletes the specified tag locally
git push origin --delete tagname => deletes the specified tag remotly





the course online material(written) => https://elzero.org/learn-git-and-github/