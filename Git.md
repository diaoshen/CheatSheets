## Account Related

#### Show git config 
``` git config --list ```
#### Show git username 
``` git config user.name ```

## Common 

#### Create local Repo 
``` git init ```
#### Remove local Repo 
``` rm -r .git ```
or
``` git branch -d <branch_name> ```
#### Create git ignore 
``` touch .gitignore ```
#### Add File(s) to stage 
``` git add <file1> <file2> <file3>  ```   or ``` git add . ``` to add all files.
#### Commit 
``` git commit -m "commit message" ```
#### Status of working tree 
``` git status ```
#### Create new local Branch 
``` git branch <branch_name> ```
#### Create branch from current branch 
``` git checkout -b <new_branch_name> ```
#### Switch Branch 
``` git checkout <branch_name> ```
#### Merge Branch 
``` git merge <branch_name> ```

## Remote Repo 
#### Clone Repo 
``` git clone <link> ```
#### Add Remote repo to local repo / Add remote reference 
``` git remote add origin <link> ```
#### Set remote as the upstream branch 
``` git push --set-upstream origin master ```
#### Show remote branch
``` git branch -a -r ```
#### Show remote tracking info 
``` git remote show origin ```
#### Show current branch with last commit 
``` git remote -av ```
#### Fetch list of branches on remote and remove local remote tracking that doesn't exist anymore on remote.
``` git remote update --prune ```
#### Current remote push/pull setting 
``` git remote -v ```
#### Pull current branch
``` git pull ```
#### Pull all branch 
``` git pull --all ```
#### Pull origin master 
``` git pull origin master ```
#### Push 
``` git push ```
#### Push origin master 
``` git push origin master ```
#### Undo Tracked Files (Restore to state that HEAD points to) 
``` git reset HEAD --hard ```
#### Restore to certain remote branch (origin/master) for example 
``` git fetch origin ```
``` git reset --hard origin/master ```
#### List what untracked files will be removed 
``` git clean -n -f ```
#### Remove Untracked Files 
``` git clean -f ```
#### Remove Untracked Files and Directories (Cannot undo changes!!)
``` git clean -fd ```
#### Remove Untracked and Ignore and directories (Cannot undo changes!!)
``` git clean -fdx ```

