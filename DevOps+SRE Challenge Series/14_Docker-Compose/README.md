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

Docker compose official documentation
Ref: https://docs.docker.com/compose/install/

    $ docker compose version

### 2. Write a Docker compose file

Create a docker-compose.yml file to define all Yelb services:

Redis: Cache layer
PostgreSQL: Persistent data storage
Appserver: Application logic
UI: User interface

