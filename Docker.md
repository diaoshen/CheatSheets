# General 
* #### Show docker status 
``` 
docker info
```
* #### Remove all stopped all stopped container, all dangling images, and all unused networks
```
docker system prune [OPTION]

--volumes : to remove all unused volume as well
```

<!--  END OF GENERAL -------------------------------------------------------------->



# Image

* #### Pull image from DockerHub 
```
docker pull <image_name>
```

* #### Build an image from Dockerfile 
```
docker build [OPTIONS] <image_name>

--file  : specific file 
```

* #### List Images 
```
docker image ls  
```
OR  
```
docker images [OPTIONS]

--all , -a  : show all images 
```

* #### Remove one or more images 
```
docker image rm 
```
* #### Remove unused/dangling images 
```
docker image prune 
```
* #### Remove all unused images 
```
docker image prune -a
```

<!--  END OF IMAGE -------------------------------------------------------------->
 
 
 
# Containers 
* #### List Containers 
```
docker container ls  

 -a  : List all container 
```
* #### Start a container from an image 
```
docker container run [OPTIONAL] <image_name>

-it  :  Foreground Mode 
-d   :  Background Mode
-publish , p : publish 
--name : Naming of container 
--rm  : Remove container upon exit 
HOST_PORT:CONTAINER_PORT   : Ports 

Ex:

NGINX:
docker container run -d -p 80:80 --name my_nginx nginx

APACHE:
docker container run -d -p 8080:80 --name my_apache httpd 

MONGODB:
docker container run -d -p 27017:27017 --name my_mongo mongo 

MYSQL:
docker container run -d -p 3306:3306 --name my_mysql --env MYSQL_ROOT_PASSWORD=123456 mysql 
```
* #### Stop a container 
```
docker container stop <container_id>
```
* #### Remove one or more stopped containers 
```
docker container rm <ID> [ -f ]
```
* #### Remove all stopped containers 
```
docker container prune 
```
* #### Stop and remove all containers 
>`docker container stop $(docker container ls -sq)` follow by `docker container rm $(docker container ls -aq)`


<!--  END OF CONTAINER -------------------------------------------------------------->


# Volumes 
* #### List volumes  
```
docker volume ls
```
* #### Remove one or more volumes 
```
docker volume rm <volume_name>
```
* #### Remove all unused volumnes 
```
docker volume prune 
```


<!--  END OF VOLUME -------------------------------------------------------------->


# Networks 
* #### List network
```
docker network ls 
```
* #### Remove one or more networks 
```
docker network rm <network_name>
```
* #### Remove all unused network 
```
docker network prune
```
