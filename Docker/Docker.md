# Docker :

## What is Container ?
* Container is an Isolated environment used for running an application or group of process.
* To build the container we need to have `Image` of that `container`.
* Ex : to build Ubuntu Container, we need to have Ubuntu Image. 

## What is Image ?

* Image is a file which is made-up of `Docker_file` and used to create a `Container`. 
* Images are made up into layers.

## What is Docker_file ?

* Docker_File is a file that contain instruction to create image file.
* As we know that Image file is in the Layers, So Here in Docker_Files we are adding the requirements to build the images.
* It's Like a text file where we are specifying the requirements to build the Image file.

## What is Docker ?

* Docker is a Container Engine to run an application in Isolated Environment.
* It's more like a virtual machine, but without OS, It's having their own OS kernel with is linux.
* With Docker file we can create docker images, and with images we can create the Docker Container
* `Docker_File` **>** `Docker_Images` **>** `Docker_Container`
* `Docker Container` is actually we use, In order to run the Application or Group of process.



## Docker CLI :

* `Docker CLI` is Command line Interface which helps us to interact with `Containers` by `Docker Demon`.

### Download the Docker Images :

* Suppose we want to download ubuntu.

```sh
rio@0xveil:~$ sudo docker pull ubuntu   
Using default tag: latest
latest: Pulling from library/ubuntu
6b851dcae6ca: Pull complete 
Digest: sha256:6120be6a2b7ce665d0cbddc3ce6eae60fe94637c6a66985312d1f02f63cc0bcd
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest


#  We are downloading the hello-world
rio@0xveil:~$ sudo docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
719385e32844: Pull complete 
Digest: sha256:c2e23624975516c7e27b1b25be3682a8c6c4c0cea011b791ce98aa423b5040a0
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest
```

* During the downloading there is hash `6b851dcae6ca` like value, these are the required file to download the images. 

### Start, Stop, & remove the Container & images.

```sh
# list the the Images
rio@0xveil:~$ sudo docker images        
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
ubuntu        latest    99284ca6cea0   12 days ago   77.8MB
hello-world   latest    9c7a54a9a43c   6 weeks ago   13.3kB

# Start the Images with name
rio@0xveil:~$ sudo docker run -it ubuntu 
root@c67b058d6226:/# 

# or with Image ID we can run it.
rio@0xveil:~$ sudo docker run -it 99284ca6cea0
root@8bb8a7556fbf:/# 

# or we can run the container in background or detached mode.
                                                             
rio@0xveil:~/docker$ sudo docker run -d ubuntu  
df29f61b406ad341a47e169ad3589086c79d6cdbec59f4cf6f656c1a0adc6a23

# List the Container 
rio@0xveil:~$ sudo docker ps
CONTAINER ID   IMAGE          COMMAND       CREATED          STATUS          PORTS     NAMES
db08533683c7   99284ca6cea0   "/bin/bash"   26 seconds ago   Up 25 seconds             competent_dirac

# Stop the container
rio@0xveil:~$ sudo docker stop db08533683c7
db08533683c7

#  Check the status of Container.
rio@0xveil:~$ sudo docker ps -a              
CONTAINER ID   IMAGE          COMMAND       CREATED              STATUS                           PORTS     NAMES
879c678d978c   99284ca6cea0   "/bin/bash"   About a minute ago   Up About a minute                          relaxed_cohen
db08533683c7   99284ca6cea0   "/bin/bash"   About an hour ago    Exited (137) About an hour ago             competent_dirac
8bb8a7556fbf   99284ca6cea0   "/bin/bash"   About an hour ago    Exited (0) About an hour ago               unruffled_shaw
c67b058d6226   ubuntu         "/bin/bash"   About an hour ago    Exited (0) About an hour ago               laughing_moore
5bba7febe87d   ubuntu         "/bin/bash"   About an hour ago    Exited (0) About an hour ago               cool_sanderson
4d5c14dfbe21   ubuntu         "/bin/bash"   About an hour ago    Exited (130) About an hour ago             relaxed_rubin
fcf9bcf3d587   ubuntu         "/bin/bash"   About an hour ago    Exited (0) About an hour ago               ecstatic_greider
32e155e84154   ubuntu         "/bin/bash"   2 hours ago          Exited (0) 2 hours ago                     cranky_swirles
58d8ab334a19   ubuntu         "/bin/bash"   3 hours ago          Exited (0) 2 hours ago                     gracious_lovelace
366fb888d7e6   ubuntu         "/bin/bash"   3 hours ago          Exited (0) 3 hours ago                     hardcore_hawking
dfdccdca95fa   ubuntu         "/bin/bash"   3 hours ago          Exited (0) 3 hours ago                     peaceful_torvalds
918ec7d62074   ubuntu         "/bin/bash"   3 hours ago          Exited (0) 3 hours ago                     frosty_satoshi
131519c60127   ubuntu         "/bin/bash"   3 hours ago          Exited (0) 3 hours ago                     optimistic_lamport
0cba92cda82a   hello-world    "/hello"      3 hours ago          Exited (0) 3 hours ago                     nice_jennings
a02e219921cb   hello-world    "/hello"      3 hours ago          Exited (0) 3 hours ago                     epic_driscoll

# To Check all the container "-a" will provide all the container, where "-q" will show only id.  
rio@0xveil:~$ sudo docker ps -q -a
db08533683c7
8bb8a7556fbf
c67b058d6226
5bba7febe87d
4d5c14dfbe21
fcf9bcf3d587
32e155e84154
58d8ab334a19
366fb888d7e6
dfdccdca95fa
918ec7d62074
131519c60127
0cba92cda82a
a02e219921cb

# To remove all the container at once.  
rio@0xveil:~$ sudo docker rm $(sudo docker ps -q -a)
db08533683c7
8bb8a7556fbf
c67b058d6226
5bba7febe87d
4d5c14dfbe21
fcf9bcf3d587
32e155e84154
58d8ab334a19
366fb888d7e6
dfdccdca95fa
918ec7d62074
131519c60127
0cba92cda82a
a02e219921cb

# This command will show all the running container images.
rio@0xveil:~$ sudo docker stats


# This command will show the images list.
rio@0xveil:~$ sudo docker images               
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
ubuntu        latest    99284ca6cea0   12 days ago   77.8MB
hello-world   latest    9c7a54a9a43c   6 weeks ago   13.3kB

# This command will show the images id only.   
rio@0xveil:~$ sudo docker images -q
99284ca6cea0
9c7a54a9a43c

# To remove we have to use "rmi" command in docker.
# This command will remove all the images.
rio@0xveil:~$ sudo docker rmi $(sudo docker images -q)
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:6120be6a2b7ce665d0cbddc3ce6eae60fe94637c6a66985312d1f02f63cc0bcd
Deleted: sha256:99284ca6cea039c7784d1414608c6e846dd56830c2a13e1341be681c3ffcc8ac
Deleted: sha256:cdd7c73923174e45ea648d66996665c288e1b17a0f45efdbeca860f6dafdf731
Untagged: hello-world:latest
Untagged: hello-world@sha256:c2e23624975516c7e27b1b25be3682a8c6c4c0cea011b791ce98aa423b5040a0
Deleted: sha256:9c7a54a9a43cca047013b82af109fe963fde787f63f9e016fdc3384500c2823d
Deleted: sha256:01bb4fce3eb1b56b05adf99504dafd31907a5aadac736e36b27595c8b92f07f1

# Here again listing the images after deleting.
rio@0xveil:~$ sudo docker images                      
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

```

### Docker Logs

```sh
#  With this command we can check the logs
rio@0xveil:~$ sudo docker logs 879c678d978c
# these are logs
root@879c678d978c:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@879c678d978c:/# whoami
root

```

### How to attached running docker session.

* Suppose there is docker container running on the local system, we want to attached that session with our terminal, then we can use this process.

```sh
#  this shows the running docker container.
rio@0xveil:~$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
5bba7febe87d   ubuntu    "/bin/bash"   3 minutes ago   Up 3 minutes             cool_sanderson

# or this command will work same.
rio@0xveil:~$ sudo docker container ls
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
5bba7febe87d   ubuntu    "/bin/bash"   4 minutes ago   Up 4 minutes             cool_sanderson
 
# copy the container ID.
# Execute this command.
rio@0xveil:~$ sudo docker exec -it 5bba7febe87d bash
root@5bba7febe87d:/# echo "This is attached session to the running docker session" 
```

### Docker Build :

* Building `Docker_Images` with `Docker_File` by `docker build`.
* Suppose we want to build our own docker images, then can use Docker Hub in this case.
* First we need to go on [Docker Hub](https://hub.docker.com/) and `SignUp`.
* Then in `Terminal`

```sh
# To login with Terminal.
rio@0xveil:~$ sudo docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: sahilwep  
Password: *********************
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded


# On the directory where you have your own docker_file            
rio@0xveil:~/docker$ cat docker               
FROM ubuntu
CMD ["echo", "Hello from Sahilwep"]

# here my file name is `docker`, i got an error while building, so rename it to `Dockerfile`
rio@0xveil:~/docker$ mv docker Dockerfile
                                                                                                                                    
rio@0xveil:~/docker$ ls
Dockerfile

# Now we can build the file successfully. 
rio@0xveil:~/docker$ sudo docker build -t myfile .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM ubuntu
 ---> 99284ca6cea0
Step 2/2 : CMD ["echo", "Hello from Sahilwep"]
 ---> Running in b06e5a4dcfff
Removing intermediate container b06e5a4dcfff
 ---> 299d9e8ae78e
Successfully built 299d9e8ae78e
Successfully tagged myfile:latest

#  Now we can see our file here.
rio@0xveil:~/docker$ sudo docker images           
REPOSITORY    TAG       IMAGE ID       CREATED          SIZE
myfile        latest    299d9e8ae78e   51 seconds ago   77.8MB
ubuntu        latest    99284ca6cea0   12 days ago      77.8MB
hello-world   latest    9c7a54a9a43c   6 weeks ago      13.3kB


# When we run the file, it run the command that we passed during the creation.
rio@0xveil:~/docker$ sudo docker run myfile    
Hello from Sahilwep

# With inspect command we can check the configuration & all.
rio@0xveil:~/docker$ sudo docker inspect ubuntu
[
    {
        "Id": "sha256:99284ca6cea039c7784d1414608c6e846dd56830c2a13e1341be681c3ffcc8ac",
        "RepoTags": [
            "ubuntu:latest"
        ],
        "RepoDigests": [
            "ubuntu@sha256:6120be6a2b7ce665d0cbddc3ce6eae60fe94637c6a66985312d1f02f63cc0bcd"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2023-06-05T17:00:39.361599721Z",
...........
...........
...........


#  or we can use this command

rio@0xveil:~/docker$ sudo docker image ls             
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
myfile        latest    299d9e8ae78e   6 minutes ago   77.8MB
ubuntu        latest    99284ca6cea0   12 days ago     77.8MB
hello-world   latest    9c7a54a9a43c   6 weeks ago     13.3kB


# this command will show the information.
rio@0xveil:~/docker$ sudo docker image inspect myfile 
[
    {
        "Id": "sha256:299d9e8ae78ec41add040162cd0697a5b0b0215d81559b7f4944f8a1d356aee9",
        "RepoTags": [
            "myfile:latest"
...........
...........
...........

```






## Reference : 

* [Docker Docs](https://docs.docker.com/get-started/)
* [Share Docker With Others](https://www.howtogeek.com/devops/how-to-share-docker-images-with-others/)


