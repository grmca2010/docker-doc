# Docker

### Install Docker

1. apt-get update
2. curl -fsSL https://get.docker.com/ | sh
3. service docker start

### Pulling a images
1.  docker pull imiell/win2048
2.  docker images

### Run a container as a bash shell and Run a container as a daemon
1. docker images
2. docker run -t -i imiell/win2048 /bin/bash
3. ls /root
4. docker run -t -i imiell/win2040 /bin/bash -c "/root/start_vnc.sh && sleep infinity"
5. docker run -d debian sleep infinity => run a container as deamon

### Track our container
1. docker ps -a
### Remove container
1.docker rm <img-id>

Examine the docker
	- docker top <container-id>
	- docker logs <container-id>

remove all the container
	- docker rm -f $(docker ps -a -q)

### sharing  with docker
1. run a container => docker run -d -p 5901:5901 -p 6080:6080 imiell/win2048 /bin/bash -c '/root/start_win2048.sh && sleep infinity'
2. docker logs <container-id>
3. docker top <container-id>

### Saving state
1.  docker ps
2.  docker pause <con-id>
3.  docker commit <con-id>
4.  docker tag <new-con-id> /imiell/new-docker-img
5.  docker kill <old-con-id>
6.  docker rm <old-con-id>
7.  docker images
8.  docker run -d -p 5901:5901 -p 6080:6080 imiell/new-docker-img /bin/bash 	-c '/root/start_win2048.sh && sleep infinity'

### Building docker images
1. create Dockerfile
2. Update the files with commands
3. run the command " docker build -t simple ."
4. docker run simple

## Beginning Docker
### Foreground commands
1.  docker run ubuntu ls
2.  docker ps -a
3.  docker rm <container-id>
4.  docker run --rm ubuntu ping google.com
### Interactive commands
1.  docker run --rm -i -t ubuntu bash
2.  docker run --rm -i -t ubuntu apt-get install vim  -- Once installed the vim , the container will be deleted
3.  docker run -rm -i -t ubuntu /bin/bash -c "apt-get install -y vim && vim"

### Background commands
1.  docker run -d -p 2222:22 ubuntu /bin/bash -c "apt-get install -y openssh-server && mkdir /var/run/sshd && echo 'root:demo' | chpasswd && sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/g' /etc/ssh/sshd_config && sed -ri 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config && /usr/sbin/sshd -D"
2.  docker logs <container-id>
3.  ssh root@localhost -p 2222
4.  docker kill <container-id>
5.  docker rm <container-id>
### Managing your containers
1.  ```docker ps``` shows the currently running container
2.  ```docker ps -a```  which show all the container including the container stopped
3.  ```docker inspect <container-id>``` which give us the json data structure of the system information
4.  ```docker logs -f <container-id>``` shows container log
5.  ```docker ps -lq``` shows last running detached container id
6.  ``` docker logs 'docker ps -lq` ```  getting logs
7.  ```docker stop <container-id>``` stops the continer
8.  ```docker kill <contaiber-id>``` kill the container
9.  ```docker rm <container-id>``` which removes the exicited container
10.  ```docker -aq | xargs docker rm -f``` removes the running container

