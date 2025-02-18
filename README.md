# Udemy Course Docker Mastery: with Kubernetes+Swarm from a Docker Captain

[![](https://dcbadge.limes.pink/api/server/devops)](https://discord.gg/devops)

> Build, test, and deploy containers with the best mega-course on Docker, Kubernetes, Compose, Swarm and Registry using a cloud native DevOps mindset

This repository is for use in my Udemy Courses "[Docker Mastery](https://www.udemy.com/course/docker-mastery/?referralCode=1410924A733D33635CCB
)" and "[Swarm Mastery](https://www.udemy.com/course/docker-swarm-mastery/?referralCode=4927D9CB156D4AE0228C)"

- Get these courses with my "cheapest on the internet" coupon links: [bretfisher.com/courses](https://www.bretfisher.com/courses)
- Get the [weekly newsletter](https://www.bretfisher.com/newsletter) on all the cloud native DevOps content I'm creating.

## Course Sections

1. Quick Start!
   1. [README](./intro/README.md)
   2. [Commands and Links](./references/S01%20Commands%20and%20Links.md)
2. Course Introduction
3. The Best Way to Setup Docker for Your OS
4. Creating and Using Containers Like a Boss
5. Container Images, Where To Find Them and How To Build Them
6. Container Lifetime & Persistent Data: Volumes, Volumes, Volumes
7. Making It Easier with Docker Compose: The Multi-Container Tool
8. Swarm Intro and Creating a 3-Node Swarm Cluster
9.  Swarm Basic Features and How to Use Them In Your Workflow
10. Swarm App Lifecycle
11. Container Registries: Image Storage and Distribution
12. Docker in Production
13. The What and Why of Kubernetes
14. Kubernetes Architecture and Install
15. Your First Pods
16. Inspecting Kubernetes Resources
17. Exposing Kubernetes Ports
18. Kubernetes Management Techniques
19. Moving to Declarative Kubernetes YAML
20. Your Next Steps and The Future of Kubernetes
21. Automated CI Workflows
22. GitHub Actions Workflow Examples
23. Docker Security Good Defaults and Tools
24. Docker 19.03 Release New Features
25. DevOps and Docker Clips
26. Dockerfiles and Docker Images in 2022
27. Dockerfile and Compose File Reviews
28. Extra's, Common Questions, and Resources

# Docker Image V.S. Docker Container

- A **Docker image** is a **read-only** blueprint for creating containers Docker contains all the libraries and source code that all make up your application.

- A **Docker registry** is a **storage and distribution system** for Docker images. It allows images to be pushed (uploaded) and pulled (downloaded). Popular registries include: Docker Hub (public), Amazon ECR (AWS), Google Container Registry (GCR) and Private Docker registries (self-hosted)

- Docker Container is an instance of that image running as a process. You can have many running same docker image

-docker's default image "registry" is called Docker Hub


# Docker container command

      # general syntax for docker container run
      
      docker container run [OPTIONS] IMAGE [COMMAND] [ARG...]
      
      Common docker run Options
      Option	                            Description

      --name my-container	                Assigns a custom name to the container.
      -d	                                  Runs the container in detached mode (in the background).
      -p 8080:80	                         Maps port 80 in the container to port 8080 on the host.
      -v /host/path:/container/path	       Mounts a volume from the host to the container.
      -e ENV_VAR=value	                   Sets an environment variable inside the container.
      --rm	                               Removes the container automatically when it stops.
      --network my-network	                Connects the container to a specific Docker network.

      # create and basic command

      - docker container run --publish 80:80 nginx : 
      1) Downloading image 'nginx' from Docker Hub 
      2) started a new container from that image
      3) opened port 80 on the host IP
      4) Routes that traffic to the container IP, port 80
      5) and it is running in foreground(ข้างหน้า) inside command line

      - docker container run --name my-nginx --publish 80:80 --detach nginx:
      basiclly same as above but running in the background instead of foreground
      quick note: nginx - Specifies the Nginx Docker image (defaults to the latest version from Docker Hub).

      - stop docker contatiner : docker container stop <container id/name>. ex: docker container stop 3df9.

      - list all docker container we have: docker container ls -a.
      - list all running docker container we have: docker container ls.
      
      - get log(activities) from docker container: docker container logs <container name>. ex: docker container logs abc.

      - remove docker container(you can't delete docker container that are currently running): docker container rm <container name>. ex: docker container rm 3df9 61e9.

      # Process and Monitoring
      
      - docker container top <container name>: process list in one container.

      - docker container inspect <container name>: details of one container config.

      - docker container stats: performance stats for all containers.

      # get in container

      - docker container run -it --name ubuntu1 ubuntu : create container and making command access by ubuntu

      - docker container start -ai <container name> : access that container. only work if the container's default command is interactive (e.g., bash, sh)

      - docker container exec -it <container name> <program you want to run such as ubuntu, bash> : run a command inside an already running container

# what happens in the backgroud when we run 'docker container run'


![alt text](<Screenshot (157).png>)