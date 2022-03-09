# Docker-Cheat-Sheet


## Docker Basic Commands

- Docker images --> list of images

- docker --version --> gives the version of docker

- docker pull [name of docker image] --> download docker image from docker hub


- docker run -it -d --name [name your contrainer/optional] [name of docker image] -> to make container of image
    * -it --> interactive
    *  -d --> detached
    *    --name -> if you want to give name


- docker -a ps --> give information of  process state of your runnig container container
   * -a --> for all container

- docker exce -it [container id] bash --> will move to docker container cli where you can communicate  with container 

- docker rm -f [container id] --> delete container

- docker stop [container id] --> to stop container

- docker kill [container id] --> forcefully stop container

- docker container run -t ubuntu top --> create container of ubuntu image and top print the process

- docker container ls  --> list of running container

- ps -ef --> run  this command under the container, it shows the process states of the under container

- docker system prune --> removes any stopped containers, unused volumes and networks, and dangling images

- <ctrl>-c -> for close the process under linux

- docker image build -t python-hello-world .  --> Build the Docker image. Pass in the -t parameter to name your image python-hello-world.

- docker container logs [container id] --> If you want to see logs from your application, you can use the docker container logs command. By default, docker container logs prints out what is sent to standard out by your application.

- docker login --> Log in to the Docker registry account by entering docker login on your terminal

- docker tag python-hello-world [dockerhub username]/python-hello-world

- docker push jzaccone/python-hello-world --> After you properly tag the image, use the docker push command to push your image to the Docker Hub registry
 
 
### Notes 
- PID is just one of the Linux namespaces that provides containers with isolation to system resources. Other Linux namespaces include:
- MNT: Mount and unmount directories without affecting other namespaces.
- NET: Containers have their own network stack.
- IPC: Isolated interprocess communication mechanisms such as message queues.
- User: Isolated view of users on the system.
- UTC: Set hostname and domain name per container.



*Remember: You didn't have to install anything on your host (other than Docker) to run these processes! Each container includes the dependencies that it needs within the container, so you don't need to install anything on your host directly.
Running multiple containers on the same host gives us the ability to use the resources (CPU, memory, and so on) available on single host. This can result in huge cost savings for an enterprise. Although running images directly from the Docker Store can be useful at times, it is more useful to create custom images and refer to official images as the starting point for these images. You'll learn to build your own custom images in the next lab.*


### Summary of Containers

- Containers are composed of Linux namespaces and control groups that provide isolation from other containers and the host.

- Because of the isolation properties of containers, you can schedule many containers on a single host without worrying about conflicting dependencies. 
- This makes it easier to run multiple containers on a single host: using all resources allocated to that host and ultimately saving server costs.

- That you should avoid using unverified content from the Docker Store when developing your own images because these images might contain security vulnerabilities
or possibly even malicious software.

- Containers include everything they need to run the processes within them, so you don't need to install additional dependencies on the host.

## Build Custome Images
 
FROM python:3.6.1-alpine <br/>
RUN pip install flask <br/>
CMD ["python","app.py"] <br/>
COPY app.py /app.py <br/>

- From : strating point of docker file every layer build top of it : tag for the dependency if not provided the latest will be downloaded
- RUN :  It is run when containeris creating
- CMD : it runs the command  every time when container is starting.
- COPY : when container is creating












### Notes
*Remember: Docker images contain all the dependencies that they need to run an application within the image. 
This is useful because you no longer need to worry about environment drift (version differences) 
when you rely on dependencies that are installed on every environment you deploy to. 
You also don't need to follow more steps to provision these environments. Just one step: install docker, and that's it.*



## Summary of Docker File 
- The Dockerfile is used to create reproducible builds for your application. A common workflow is to have your CI/CD automation run docker image build as part of its build process.
- There is a caching mechanism in place for pushing layers too. Docker Hub already has all but one of the layers from an earlier push, so it only pushes the one layer that has changed.
- When you change a layer, every layer built on top of that will have to be rebuilt. Each line in a Dockerfile builds a new layer that is built on the layer created from the lines before it. This is why the order of the lines in your Dockerfile is important. 
- You optimized your Dockerfile so that the layer that is most likely to change (COPY app.py /app.py) is the last line of the Dockerfile. 
- Generally for an application, your code changes at the most frequent rate. 
- This optimization is particularly important for CI/CD processes where you want your automation to run as fast as possible.



 ### Note
 * You can do free certification course at <a href="https://cognitiveclass.ai/courses/docker-essentials">Docker Essentials: A Developer Introduction </a>*

 
 
