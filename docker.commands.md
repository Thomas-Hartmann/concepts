# Docker commands
- docker pull <image name>
    - downloads an image from docker hub
- docker build -t <some image name> <location of Dockerfile (just use . if its in current location)>
    - Creates a new docker Image.
    - 'Dockerfile' must be written exactly like 
- docker run -it <image name> --name <desired container name (optional)> <command(optional): like /bin/bash>
    - starts a new docker container based on an image (if it does not exist locally - it will be pulled from docker hub)
    - the -it option is to run interactively (and in TTY: pseudo terminal)
    - we can use -p to assign ports like: 80:80 (host port: container port) - then from the host machine http://localhost:80 will point to the container machines port 80.
    - we can use -v to mount a volume from the local machines folder to the docker container machine folder
        - ```docker run -it --name testcointainer -v <~/my/local/folder>:</local/folder/on/container>```
        - This is great when we work on local files in ide and when ever we save the container server will reflect the changes immidiately.
    - we can also use -v to create a docker volume (little different)
        - ```docker run -it --name testcon -v data:/data ubuntu bash```
            - this is not a bind mount since there is no absolute path to local folder. Instead it is a 'docker volume' called 'data'. In this way lots of containers can share the same volume. It can be seen with comman ``docker volume ls```
            In this way we detach data from container.
            - another docker run command with -v can attach the volume and thus it can be shared between many containers.
            - the option -v can be used more times within the docker run command.
            - an option exists called: `--volumes-from` <other container> if this is used when creating new container - it will get the same volumes that the other container has.
- docker start <container name>
    - starts an existing container
- docker exec <container name> <command>
    - e.g: docker exec eq34terr34 /bin/bash
    - lets us execute a command (in this case start a bash prompt) inside a running container
    - we can use option: -u <username> to execute as a different user from root. e.g: docker exec <container name> -u tha /bin/bash
- docker ps -a
    - shows all docker containers
- docker images
    - shows all docker images
- docker stop <container id> (or container name(s) space separated)
- docker rm <container id> 
    - removes a container
- docker search <options> <search term>
    - docker search tomcat (shows all images on docker hub related to tomcat)
- docker cp <container name>:/path/to/file/on/container /path/to/local (or just use . to copy to current local folder)   
    - moves file from container to local location
- docker cp ./file.txt <container name>:/path/to/folder/and/file
    - copies from local pc to container path.
- docker inspect <container name> will provide a json display of the container configuration.

## Docker compose
Here we can configure a file with all our containers starting up at the same time. The file is called `docker-compose.yml`
- `docker-compose up` is the command to start up from the directory in which we have the docker-compose file located. This will start up all the containers along with volumes etc.

## Docker cloud
Can essentially do the same as Docker compose - just in the cloud. 
    - Docker compose deploys microservices into seperate containers running locally
    - Docker cloud does the same just deploying it to a production server.
    - Sign up/in at cloud.docker.com
    - Turn swarm mode off on the front page (why??).
    

## Rules of thumb
- There should be only óne process pr. container. Like micro services.
- 
    
