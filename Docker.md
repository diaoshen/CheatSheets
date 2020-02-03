### General 
* #### Remove all stopped all stopped container, all dangling images, and all unused networks
>docker system prune [OPTION]
```
--volumes : to remove all unused volume as well
```
<!--  END OF GENERAL -------------------------------------------------------------->



### Image

* #### Pull image from DockerHub 
> docker pull `<NAME>`

* #### Build an image from Dockerfile 
>docker build [OPTIONS]
```
--file  : specific file 
```

* #### List Images 
>docker image ls  
OR  
>docker images [OPTIONS]
```
--all , -a  : show all images 
```

* #### Remove one or more images 
>docker image rm 
* #### Remove unused/dangling images 
>docker image prune 
* #### Remove all unused images 
>docker image prune -a

<!--  END OF IMAGE -------------------------------------------------------------->
 
 
 
### Containers 
* #### List Containers 
>docker container ls  
```
 -a  : List all container 
```
* #### Remove one or more stopped containers 
>docker container `<ID>`
* #### Remove all stopped containers 
>docker container prune 
* #### Stop and remove all containers 
>`docker container stop $(docker container ls -sq)` follow by `docker container rm $(docker container ls -aq)`


<!--  END OF CONTAINER -------------------------------------------------------------->


### Volumes 
* #### List volumes  
>docker volume ls
* #### Remove one or more volumes 
>docker volume rm `<volume_name>`
* #### Remove all unused volumnes 
>docker volume prune 


<!--  END OF VOLUME -------------------------------------------------------------->


### Networks 
* #### List network
>docker network ls 
* #### Remove one or more networks 
>docker network rm `<network_name>`
* #### Remove all unused network 
>docker network prune
