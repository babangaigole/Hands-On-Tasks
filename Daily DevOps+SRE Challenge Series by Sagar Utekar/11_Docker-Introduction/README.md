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

<img width="223" alt="Docker_Ver" src="https://github.com/user-attachments/assets/8b6d17d8-2f70-4c29-a008-fc21b0439706" />

### Pull & Run a Container

Pull the official nginx image:

<img width="482" alt="Docker_pull" src="https://github.com/user-attachments/assets/316ab133-705b-4489-9051-ff67df605fdd" />

Run the container in detached mode with port mapping:

<img width="404" alt="Docker_run" src="https://github.com/user-attachments/assets/7e61c0e6-316e-4417-9a09-32d80cc10675" />

### Inspect & Explore

List all running containers:

<img width="695" alt="Docker_container_list" src="https://github.com/user-attachments/assets/4a5f1d19-7c90-4b8c-baee-78144673a0bc" />

Access the running container's logs:

<img width="579" alt="Docker_container_logs" src="https://github.com/user-attachments/assets/8e341649-04a3-4053-8091-a6beb1a6b7ed" />

Inspect the container metadata:

<img width="802" alt="Docker_inspect" src="https://github.com/user-attachments/assets/607b1f48-79c7-428e-b129-7ea38312f277" />

### Build a Custom Docker Image

Download and save the provided index.html file to your project directory:

<img width="366" alt="Docker_index_file" src="https://github.com/user-attachments/assets/de851fc4-ae96-4bb1-9a99-5e50d0bcf05c" />

Create a Dockerfile in the same directory with the following content:

<img width="372" alt="Docker_Dockerfile" src="https://github.com/user-attachments/assets/27e5700c-1457-448d-952d-aff36ea5df55" />

Build the image and tag it:

<img width="917" alt="Docker_build" src="https://github.com/user-attachments/assets/4ae65a3a-f894-44d9-a5f0-f162ed8c9465" />

<img width="522" alt="Docker_image_list" src="https://github.com/user-attachments/assets/c612338a-5e64-4a41-9d38-1adf63545d75" />

Run the custom container:

<img width="815" alt="Docker_my_custom_nginx_run" src="https://github.com/user-attachments/assets/a9dc86b0-bcbb-4569-9643-fe16fe3f6d67" />



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

