Here's a formatted README file based on your provided commands and descriptions.

---

# Docker Commands Cheat Sheet

This document provides a summary of useful Docker commands for building, running, and managing Docker containers and images.

## Build Docker Images

- Build Docker image with a tag:
  ```sh
  docker build -t myapp .
  ```
- Build Docker image with a specific version tag:
  ```sh
  docker build -t myapp:v1 .
  ```

## Check Docker Images

- List all Docker images:
  ```sh
  docker images
  ```
  Example output:
  ```
  REPOSITORY                 TAG       IMAGE ID       CREATED          SIZE
  myapp                      latest    1b22886d531c   50 minutes ago   173MB
  node                       latest    3d4b037e6712   11 days ago      1.11GB
  docker/welcome-to-docker   latest    c1f619b6477e   6 months ago     18.6MB
  ```

## Run Docker Containers

- Run a container (non-detachable, in terminal):
  ```sh
  docker run --name myapp_a1 myapp:latest
  ```
  - Listening for requests on port 4000.
- Run a container (detachable, in terminal):

  ```sh
  docker run --name myapp_c2 -p 4000:4000 -d myapp:latest
  ```

  - Example container ID: `84dce28d7765e958afcc78b2ca8ff3df44818932e066184702b83ac569eabeb1`

- Run a container and delete it automatically when stopped:

  ```sh
  docker run --name myapp_mon -p 4000:4000 --rm myapp:v3
  ```

  - Listening for requests on port 4000.

- Run a container with volume binding and delete it automatically when stopped:
  ```sh
  docker run --name myapp_mon -p 4000:4000 --rm -v /home/shreyansh/Docker/project_react/api-5:/app -v /app/node_modules myapp:v3
  ```
  - Listening for requests on port 4000.

## Stop Docker Containers

- Stop a running container:
  ```sh
  docker stop myapp_c2
  ```

## List Docker Containers

- List running containers:

  ```sh
  docker ps
  ```

  - Example output:
    ```
    CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
    ```

- List all containers (running and non-running):
  ```sh
  docker ps -a
  ```
  - Example output:
    ```
    CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                         PORTS     NAMES
    84dce28d7765   myapp:latest   "docker-entrypoint.s…"   About a minute ago   Exited (137) 41 seconds ago              myapp_c2
    6a7b5e2b50dc   myapp:latest   "docker-entrypoint.s…"   7 minutes ago        Exited (137) 7 minutes ago               myapp_a1
    ```

## Start Docker Containers

- Start a stopped container (non-interactive):

  ```sh
  docker start myapp_c2
  ```

- Start a stopped container (interactive):
  ```sh
  docker start -i myapp_c2
  ```

## Remove Docker Images

- Remove a Docker image:

  ```sh
  docker image rm myapp
  ```

  - Error response if container using the image exists:
    ```
    Error response from daemon: conflict: unable to remove repository reference "myapp" (must force) - container a2c62b61076d is using its referenced image 1b22886d531c
    ```

- Force remove a Docker image:
  ```sh
  docker image rm myapp3 -f
  ```

## Remove Docker Containers

- Remove one or more Docker containers:
  ```sh
  docker container rm myapp_c1 myapp_c2
  ```

## Clean Up Docker System

- Remove all unused images, containers, and volumes:
  ```sh
  docker system prune -a
  ```

## Docker Compose Commands

- Start services defined in a `docker-compose.yml` file:

  ```sh
  docker-compose up
  ```

- Stop services started by Docker Compose:

  ```sh
  docker-compose down
  ```

- Stop services and remove all images, containers, and volumes:
  ```sh
  docker-compose down --rmi all -v
  ```

## Push and Pull Docker Images

- Build and tag Docker image:

  ```sh
  docker build -t shreyann56sh/myapp .
  ```

- Push Docker image to Docker Hub:

  ```sh
  docker push shreyann56sh/myapp
  ```

- Remove local Docker image:

  ```sh
  docker image rm shreyann56sh/myapp
  ```

- Verify removal by listing images:

  ```sh
  docker images
  ```

- Pull Docker image from Docker Hub:
  ```sh
  docker pull shreyann56sh/myapp
  ```

---

This cheat sheet provides a quick reference to essential Docker commands, enabling efficient container and image management.
