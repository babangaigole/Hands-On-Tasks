# Day 13 Challenge: Mastering Docker Volumes for Persistent Applications

Docker volumes provide flexibility and enhanced functionality for containerized applications through persistence, isolation, sharing, and backup and migration.
The challenge covers key Docker volume commands, such as listing, creating, inspecting, removing, and pruning unused volumes.

## Steps to Complete the Challenge

### 1. Create a Docker volume
Create a new Docker volume named "my-vol"

    $ docker volume create my-vol

![create](https://github.com/user-attachments/assets/ba50c08a-e0e5-4ab9-b7f9-ac51c87ee07e)


### 2. Inspect a Docker volume
Display detailed information about a specific Docker volume named `my-vol`.

    $ docker volume inspect my-vol

![inspect](https://github.com/user-attachments/assets/aee78d71-6ecb-429c-84c6-86d3ad71cb62)

### 3. List Docker volume
List all the Docker volumes currently available on the system.

    $ docker volumes ls

### 4. Remove a Docker volume
Remove a volume named "my-vol".

    $ docker volume rm my-vol

### 5. Prune unused Docker volume
Remove unused and dangling Docker volumes.
It helps to free up disk space by deleting volumes that are not currently being used by any containers. 

$ docker volume prune

## Task Objectives:
1. Use Docker volumes to persist data for Redis and PostgreSQL components in the Yelb application.
2. Verify data persistence by stopping and removing the containers and restarting them to confirm that data is retained.

## Challenge Steps

### 1. Create a bridge network 'yelb-network'

    $ docker network create yelb-network

![yelb-network](https://github.com/user-attachments/assets/6b977173-4a10-4974-b19f-8ccdb191be42)

### 2. Run PostgreSQL with a Volume

Create a volume for PostgreSQL data:

    $ docker volume create pgsql-data

![volume_pgsql-data](https://github.com/user-attachments/assets/e2d118f9-9b1c-4d33-a0cc-476c2c048293)

Start the PostgreSQL container with the volume 'pgsql-data'

    $ docker run -d --name yelb-db --network=yelb-network \
    -v pgsql-data:/var/lib/postgresql/data -p 5432:5432 \
    mreferre/yelb-db:0.6

![container_yelb-db](https://github.com/user-attachments/assets/bdab9367-d053-44b1-a454-79b9efd2cf27)

### 3. Run Redis with a Volume

Create a volume for Redis data:

    $ docker volume create redis-data

![volume_redis-data](https://github.com/user-attachments/assets/8f5b0aec-ea18-48f9-8bb4-b990c212debb)

Start the Redis container with the volume:

    docker run -d --name redis-server --network=yelb-network \
    -v redis-data:/data -p 6379:6379 \
    redis:4.0.2

![container_redis-server](https://github.com/user-attachments/assets/deef61a7-c5f8-4c77-8715-97220d4ad9db)

### 4. Verify Data Persistence

Check the existing database data for both containers:

    $ docker container ls

Match the short container ID with the directories located in '/var/lib/docker/containers' (default volume mount location):
    
    $ sudo ls /var/lib/docker/containers

Check the stored data on local system:

![data_verification](https://github.com/user-attachments/assets/3e7700ac-04e1-4d7e-9e70-cb79b023dd6c)

Stop and remove the Redis and PostgreSQL containers:

    docker stop redis-server yelb-db
    docker rm redis-server yelb-db

Restart the containers and verify that data is retained:

    docker run --name yelb-db --network=yelb-network \
    -v pgsql-data:/var/lib/postgresql/data -p 5432:5432 \
    -d mreferre/yelb-db:0.6

    docker run --name redis-server --network=yelb-network \
    -v redis-data:/data -p 6379:6379 \
    -d redis:4.0.2

![verify-1](https://github.com/user-attachments/assets/89a433ed-b126-41e4-92c6-b9d977915819)

### 5. Inspect Volume Usage

Inspect the volumes to confirm they are in use:

    docker volume inspect pg-data
    docker volume inspect redis-data

![verify-2](https://github.com/user-attachments/assets/d425982a-cec9-4656-a767-49c5965f090d)

