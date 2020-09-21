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
#### Fix git ignore not detecting files 
``` 
git rm -r --cached .
git add .
git commit -m ".gitignore is now working"
```
#### Add File(s) to stage 
``` git add <file1> <file2> <file3>  ```   or ``` git add . ``` to add all files.
#### Commit 
``` git commit -m "commit message" ```
#### Status of working tree 
``` git status ```
#### Create new local Branch 
``` git branch <branch_name> ```
#### Delete a local branch 
``` git branch -d branch_name ```
#### Delete all local branch except master
``` git branch | grep -v "master" | xargs git branch -D ```
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
#### Update Remote 
``` git remote update [origin] ```
#### Show remote branch
``` git branch -r ```
#### Show all local+remote branch with last commit info  
``` git branch -a -v ```
#### Show remote push/pull tracking info 
``` git remote show origin ```
#### Fetch list of branches on remote and remove local remote tracking that doesn't exist anymore on remote.
``` git remote update --prune ```
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
#### Remove from local filesystem and remote repo 
``` 
git rm file1.txt
git commit -m "remove file1.txt"
```
#### Remove from remote repo but keep in local filesystem 
```
git rm --cached file1.txt
git commit -m "remove file1.txt"
```

