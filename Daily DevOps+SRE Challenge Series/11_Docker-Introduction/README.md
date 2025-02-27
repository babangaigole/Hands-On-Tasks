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

List image

<img width="522" alt="Docker_image_list" src="https://github.com/user-attachments/assets/c612338a-5e64-4a41-9d38-1adf63545d75" />

Run the custom container:

<img width="815" alt="Docker_my_custom_nginx_run" src="https://github.com/user-attachments/assets/a9dc86b0-bcbb-4569-9643-fe16fe3f6d67" />

### Access & Test

Default NGINX: http://localhost:8080

<img width="458" alt="Docker_curl_8080" src="https://github.com/user-attachments/assets/643c46ce-651e-48bd-a875-cc4cae5d1e90" />

Custom NGINX: http://localhost:8081

<img width="452" alt="Docker_curl_8081" src="https://github.com/user-attachments/assets/8111d675-6490-49b4-bfa6-90e4c1567b4d" />

### Troubleshooting Challenges

#### Try running another container on the same port 8080. Observe and fix the issue.

<img width="914" alt="Docker_same_host_port_error" src="https://github.com/user-attachments/assets/81a478ba-350b-4167-bdb8-8517d49bb53b" />

We cannot map the same host port to two different containers simultaneously. Each port on the host can only be bound to a single container at a time. If you try to map the same host port to multiple containers, you will encounter an error indicating that the port is already in use. However, we can only overcome this issue by binding another available host port e.g. 8082.

<img width="781" alt="Docker_run_8082" src="https://github.com/user-attachments/assets/eae4fa24-2bf1-4177-9ad9-ab590a43f2dc" />

#### Stop a running container and attempt to access its application in the browser. What happens?

When you stop a running container and attempt to access its application in the browser, the application will no longer be accessible. This happens because the container, which was hosting the application, is no longer running and therefore not serving any content.

<img width="508" alt="Docker_stop_start" src="https://github.com/user-attachments/assets/4c39046f-d58d-41b2-bd13-305519f5cc2a" />

We can access application in the browser again by starting the container.

Use the docker logs command to debug and restart a misconfigured container.
Introduce an error in the Dockerfile (e.g., a typo in the COPY instruction). Build the image and fix the issue by reading the logs.

### Cleanup

Stop and remove the containers:

<img width="785" alt="Docker_stop_remove" src="https://github.com/user-attachments/assets/c0fc0c1a-a903-4beb-978b-22bc7a32b748" />

Remove the custom image:

<img width="544" alt="Docker_image_list_2" src="https://github.com/user-attachments/assets/f3aa14b1-56d6-4969-834f-b442401eb952" />

<img width="484" alt="Docker_image_delete" src="https://github.com/user-attachments/assets/3ec915cf-fa68-4e86-b2f1-34b761e653c4" />


