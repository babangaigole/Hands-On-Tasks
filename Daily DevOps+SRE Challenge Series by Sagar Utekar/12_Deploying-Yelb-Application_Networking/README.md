# Day12 Challenge - Deploying Yelb application with Docker to understand Docker networking

The challenge involves deploying the Yelb application using Docker and understanding Docker networking features.
The key concepts of Docker networking include isolation, name resolution, and customizability.

The challenge includes creating a user-defined bridge network, deploying Redis and PostgreSQL, and launching the Yelb appserver and UI. The application is then tested, and troubleshooting tips are provided.

This challenge aims to help learners understand Docker networking and its importance in deploying containerized applications.

## Steps to Complete the Challenge

### 1. Create a Docker network

$ docker network create yelb-network
$ docker network ls

![network-ls](https://github.com/user-attachments/assets/54e616a0-4e7f-4be4-b86e-f3a401644c6a)

### 2. Run Redis server
Redis acts as a caching layer to store page views. It stores data persistently at location '/tmp/myredis/conf'.

$ docker run -d --name=redis-server --network=yelb-network -p 6379:6379 -v /tmp/myredis/conf:/usr/local/etc/redis redis:4.0.2

![redis-server-container](https://github.com/user-attachments/assets/0ea35ef2-4643-4ef8-874b-1b37e320a724)

### 3. Run PostgreSQL database
The PostgreSQL database is storing its persistently in a volume 'pgsqldata'.

$ docker create volume pgsqldata
$ docker run -d --name=yelb-db --network=yelb-network -p 5432:5432 -v pgsqldata:/var/lib/postgresql/data mreferre/yelb-db:0.6

![yelb-dbsrv](https://github.com/user-attachments/assets/5d798ddd-e19d-483b-830d-013259d8e649)

### 4. Run Yelb appserver
The Yelb application server is connected to both Redis and PostgreSQL servers.

$ docker run -d --name=yelb-appserver --network=yelb-network -p 4567:4567 -e RACK_ENV=test mreferre/yelb-appserver:0.7

![yelb-appsrv](https://github.com/user-attachments/assets/17d14038-68d5-4946-a09d-095521cd38f9)

### 5. Run Yelb UI
Yelb UI is the front-end container that serves the user with UI access.

$ docker run --name yelb-ui --network=yelb-network -d -p 8080:80 -e UI_ENV=test mreferre/yelb-ui:0.10

![yelb-UI-srv](https://github.com/user-attachments/assets/31d709d5-58b4-4756-b595-0f0cc2a291cd)

### 6. Verification

To visit the UI, open http://localhost:8080

![Yeb-UI](https://github.com/user-attachments/assets/15d5aeae-5eee-4e8a-96ee-2b4bf36f2f31)

## Troubleshooting

### 1. Deleting redis-server container

$ docker container stop redis-server

![redis-srv_delete](https://github.com/user-attachments/assets/fa619a71-920a-47cb-af47-976cc6a54d17)

### 2. Deleting yelb-db container

$ docker container stop yelb-db

![redis-srv_delete](https://github.com/user-attachments/assets/12dc468e-2dfa-4ca5-b144-10faf4804644)

Re-creating both the containers resumes the UI with correct data. This is only possible due to the persistent data stores for both containers.


