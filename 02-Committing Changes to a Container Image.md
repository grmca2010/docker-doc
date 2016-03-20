### Committings changes to a Docker
1.  ```docker images```
2.  ``` docker run -i -t ubuntu bash```
3.  ```apt-get update``` update your linux system with latest pkgs
4.  Install ssh server ```apt-get install -y openssh-server```
5.  Create a directory if a container don't have ```mkdir /var/run/sshd```
6.  Update the ssh config files ```sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/g' /etc/ssh/sshd_config```
7.  ```sed -ri 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config```
4.  ```exit`` exit from ssh of the container
5.  ```docker diff `docker ps -lq``` which shows the differnce inside the container after installing the sshd server
6.  Commit your Container ```docker commit `docker ps -lq` donaldsimpson/sshd```
7.  Run your committed container ```docker run -d -p 2222:22 donaldsimpson/sshd /usr/sbin/sshd -D``` 
8.  check your ssh connection from your local machine ``` ssh root@localhost -p 2222```
9.  clean up container ``` docker rm -f `docker ps -lq` ```
