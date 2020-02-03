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
#### Create git ignore 
``` touch .gitignore ```
#### Add File(s) to stage 
``` git add <file1> <file2> <file3>  ```   or ``` git add . ``` to add all files.
#### Commit 
``` git commit -m "commit message" ```
#### Status of working tree 
``` git status ```
#### Create Branch 
``` git branch <branch_name> ```
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

