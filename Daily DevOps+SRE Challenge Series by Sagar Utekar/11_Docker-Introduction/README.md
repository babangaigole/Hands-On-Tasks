# Day11 Challenge - Docker Challenge: Getting Your Feet Wet with Docker

## What is Docker?
**Docker** is an open platform that helps developers and DevOps teams build, ship and run applications in isolated environments called **containers**.

## What are Docker Images?
**Docker Images** are compact, self-contained and lightweight executable software bundles that include all necessary dependencies to run an application.

## What are containers?
**Docker Containers** are running instances of Docker images that operate as isolated processes on a host machine.

## What is a Dockerfile?
**Dockerfile** is a script file with instructions for creating a Docker image.

### Docker Installation Official Document
Ref: https://docs.docker.com/engine/install/

https://github.com/babangaigole/Hands-On-Tasks/blob/main/Daily%20DevOps%2BSRE%20Challenge%20Series%20by%20Sagar%20Utekar/11_Docker-Introduction/images/Docker_Ver.png

### Pull & Run a Container

Pull the official nginx image:
docker pull nginx
Run the container in detached mode with port mapping:
docker run -d --name my-nginx -p 8080:80 nginx

### Inspect & Explore

List all running containers:
docker ps
Access the running container's logs:
docker logs my-nginx
Inspect the container metadata:
docker inspect my-nginx

### Build a Custom Docker Image

List all running containers:
docker ps
Access the running container's logs:
docker logs my-nginx
Inspect the container metadata:
docker inspect my-nginx

### Access & Test

Open your browser and visit:
Default NGINX: http://localhost:8080
Custom NGINX: http://localhost:8081

### Troubleshooting Challenges

Try running another container on the same port 8080. Observe and fix the issue.
Stop a running container and attempt to access its application in the browser. What happens?
Use the docker logs command to debug and restart a misconfigured container.
Introduce an error in the Dockerfile (e.g., a typo in the COPY instruction). Build the image and fix the issue by reading the logs.

### Cleanup

Stop and remove the containers:
docker stop my-nginx my-custom-nginx
docker rm my-nginx my-custom-nginx 
Remove the custom image:
docker rmi my-nginx:custom






####Submission Guidelines
Proof of Completion:

Screenshots showing the running containers (docker ps).
Screenshots of the custom webpage served via my-custom-nginx.
Output from docker logs my-nginx.
Documentation:

Update your README.md with:
Steps to build and run the custom image.
Challenges faced and how you resolved them.
Key learnings.

