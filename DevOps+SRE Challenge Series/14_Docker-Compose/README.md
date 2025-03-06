# Day 14 Challenge: Orchestrating Yelb with Docker Compose

In this challenge, we will learn how to use Docker Compose to manage and deploy multi-container applications, specifically the Yelb application.
Docker Compose simplifies deployment by allowing users to define all required services, networks, and volumes in a single YAML file.
By the end of the challenge, we will be able to start, stop, and scale all Yelb services with a single command.

This challenge covers:
* Installing Docker Compose
* Writing a docker-compose.yml file
* Deploying the application
* Stopping and cleaning up.

Bonus tasks include:
* Scaling the appserver service
* Customizing service health checks

## Steps to Complete the Challenge

### 1. Install Docker Compose

[Docker compose official documentation](https://docs.docker.com/compose/install/)

    $ docker compose version

### 2. Write a Docker compose file

Create a [docker-compose.yml](https://github.com/babangaigole/Hands-On-Tasks/blob/main/DevOps%2BSRE%20Challenge%20Series/14_Docker-Compose/docker-compose.yaml) file to define all Yelb services:

    Redis: Cache layer
    PostgreSQL: Persistent data storage
    Appserver: Application logic
    UI: User interface

Reference: [Yelb Project](https://github.com/mreferre/yelb/tree/master/deployments/localtest)

### 3. Deploy the Yelb application

Start all services with a single command:

```
docker compose up -d
```

![Docker-Compose](https://github.com/user-attachments/assets/6d48779a-2b59-4f8e-bc37-0bf26b5c39c3)

### 4. Verify the deployment

Check the status of all containers:

```
$ docker compose ps
```

![Docker-Compose-ps](https://github.com/user-attachments/assets/bf11d8b0-8947-473a-8a54-f42c6db245b1)

Open your browser and visit http://localhost:8080 to interact with the Yelb UI.

![yelb_ui](https://github.com/user-attachments/assets/d34453b7-21d8-4638-96a2-7437b7b93a4d)

### 5. Bonus task

Customize service health checks in the compose file

```
  redis-server:
    image: redis:4.0.2
    ports:
      - 6379:6379
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 5s
      retries: 3
```

This health check ensures to continuously report the health state at an interval of very 10 seconds.
A timeout of 5 seconds defines the maximum amount of time that the health check should take.
And retries parameter set to 3, ensures that 3 consecutive failures will mark the container unhealthy.







