## Account 
#### Change to Root 
`su` or `su root`
#### Change to specific `<user>`
`sudo su <user>`
#### Add user 
```
sudo useradd <user> -m -e <date>
-m : creates home folder for this user 
-e : specifies expiration date
```
#### Add user to sudo list 
``` adduser <user> sudo ```
#### Change password 
```
sudo passwd <user> [OPTIONS]

-x value : expire in <value> days 
-w vlaue : remind if <value> days remain 
```
#### Set File/Directory Permission 
`chmod XXX file`

## Drives
#### List connected drives 
`fdisk -l`

## Directory/Folder
#### Go to root dir 
`cd /`
#### Copy folder and its subfolder from src to dst 
`cp -rf <src_dir> <dst_dir> `
#### Move/Rename Directory 
`mv <old> <new>`

## Files 
#### Move/Rename Directory 
`mv <old> <new>`
#### Remove file that starts with <file_name>
`rm <file_name>*`
#### Remove file that ends with .txt
`rm *.txt`
#### Remove file 
```
rm <file_name> [OPTIONS]

-f  : force remove
```
#### Copy all .txt from src to dst 
`cp <src_dir>/*.txt <dst_dir>`



## SCP and SSH 
### SSH Connect 
``` ssh username@hostname ```
### Exit SSH 
``` Ctrl+D ``` or ``` exit ```
#### Copy from remote server 
```
scp <src> <dst>
scp username@athena.ecs.csus.edu:/gaia/class/student/username/test.txt /home/diao
```
#### Upload to remote server 
```
scp <file> <dst>
```


## Tar 
#### Compress file 
`tar -cvf <output_name>.tar <src>`
#### UnCompress file 
` TODO `
