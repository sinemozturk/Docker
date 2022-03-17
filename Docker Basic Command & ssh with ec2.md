 # Hands-on Docker : Installing Docker on Amazon Linux 2 AWS EC2 Instance & Hands-on
 
 - installing Docker on AWS ec2 instance
 -  Launch an EC2 instance using the Amazon Linux 2 AMI t2.micro with security group allowing SSH connections.

 ``` bash command
 ssh -i /path/my-key-pair.pem my-instance-user-name@my-instance-public-dns-name # select ec2 instance from console  and connect & copy ssh connection
 ssh -i .ssh/newkey.pem ec2-user@ec2-3-133-106-98.us-east-2.compute.amazonaws.com  
 ```

# Update packages in EC2 instance & Install Docker into EC2 
- each command will be execute separately

``` bash command
sudo yum update -y # update packeges

sudo amazon-linux-extras install docker -y  #install latest Docker community edition version

sudo systemctl start docker # before starting container init system should be informed. 

sudo systemctl enable docker #docker service can restart automatically after reboots.

sudo systemctl status docker #check the docker is up or running

sudo usermod -a -G docker ec2-user # Add the `ec2-user` to the `docker` group to run docker commands without using `sudo`.

newgrp docker # to run docker commands without "sudo" 

docker version # check it out of version of docker without "sudo" command

docker info #detailed information about docker where you are working? with how many docker containers?

```

# Basic container commands of Docker

``` bash commands

docker help | less     # detailed information about all docker commands  to close the screen press -> q 

docker (specific command) --help | less  
docker run --help | less # detailed information about 'run' command to close -> q

docker –version  # to get the currently installed version of docker

docker pull <image name>  # to pull images from the docker repository(hub.docker.com)

docker run -it -d  <image name>  #to create a container from an image
docker run -i -t ubuntu     # download and run `ubuntu` os with interactive shell open

docker ps   # to list the running containers

docker ps -a # to show all the running and exited containers

docker container ls # same work docker ps "to list the running containers" 
docker container ls -a # to show all the running and exited containers

docker exec -it <container id> bash # to access the running container

docker stop <container id or name> #stops a running container
docker stop 4e4ds46u56
docker stop angry_bird

docker kill <container id> # kills the container by stopping its execution immediately. 

docker commit <conatainer id> <username/imagename>  # creates a new image of an edited container on the local system
docker commit  4e4ds46u56 sinem/ubuntunew


docker login # login to the docker hub repository

docker push <username/image name> #to push an image to the docker hub repository
docker push sinem/ubuntunew

docker images #lists all the locally stored docker images

docker rmi <image-id/name> # to delete an image from local storage
docker rmi 4e4ds46u56 or docker rmi sinem

docker build <path to docker file> # to build an image from a specified docker file

docker inspect <container id/name> | less  # get more information about container to close screen press 'q'

docker attach <container id/name> # go into the container for exit write 'exit' 
docker attach sinem # to the interactive shell of running `sinem` container and `exit` afterwards.

```

