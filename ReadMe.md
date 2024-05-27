docker build -t myapp .

 <!-- For build docker after writing the code  -->

docker build -t myapp:v1 .

 <!-- **MOST IMPORTANT**: For build docker after writing the code in tag version -->

<!-- [+] Building 30.0s (10/10) FINISHED                                                                                                                                   docker:default
 => [internal] load build definition from Dockerfile                                                                                                                            0.1s
 => => transferring dockerfile: 179B                                                                                                                                            0.0s
 => [interna -->

docker images

 <!-- To check images -->

<!-- REPOSITORY                 TAG       IMAGE ID       CREATED          SIZE
myapp                      latest    1b22886d531c   50 minutes ago   173MB
node                       latest    3d4b037e6712   11 days ago      1.11GB
docker/welcome-to-docker   latest    c1f619b6477e   6 months ago     18.6MB -->

docker run --name myapp_a1 myapp:latest

<!-- NON detachable IN TERMINAL -->

<!-- listening for requests on port 4000 -->

docker run --name myapp_c2 -p 4000:4000 -d myapp:latest

<!-- Detachable IN TERMINAL -->

<!-- 84dce28d7765e958afcc78b2ca8ff3df44818932e066184702b83ac569eabeb1 -->

docker run --name myapp_mon -p 4000:4000 --rm myapp:v3

<!-- NON-Detachable IN TERMINAL -->

<!-- IMPORTANT:: listening for requests on port 4000, but will delete container automatically if you stop that container -->

docker run --name myapp_mon -p 4000:4000 --rm -v /home/shreyansh/Docker/project_react/api-5:/app -v /app/node_modules myapp:v3

<!-- NON-Detachable IN TERMINAL -->

<!-- **MOST IMPORTANT** (concept VOLUME):: listening for requests on port 4000, but will delete container automatically if you stop that container -->

docker stop myapp_c2

<!-- myapp_c2 -->

docker ps

<!-- Will only show the running containers! -->

<!-- CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES -->

docker ps -a

<!-- Will show both running and non-running containers! -->

<!-- CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                         PORTS     NAMES
84dce28d7765   myapp:latest   "docker-entrypoint.s…"   About a minute ago   Exited (137) 41 seconds ago              myapp_c2
6a7b5e2b50dc   myapp:latest   "docker-entrypoint.s…"   7 minutes ago        Exited (137) 7 minutes ago               myapp_a1 -->

docker start myapp_c2

<!-- Already build one before with not working terminal -->

<!-- myapp_c2 -->

docker start -i myapp_c2

<!-- Already build one before with working terminal -->

<!-- myapp_c2 -->

docker image rm myapp

<!-- if container does exists -->
<!-- Error response from daemon: conflict: unable to remove repository reference "myapp" (must force) - container a2c62b61076d is using its referenced image 1b22886d531c -->

docker image rm myapp2

<!-- if container doesnt exists -->
<!-- Deleted: sha256:b6a849c79e247dce78530cbc69dd30e7d93494bebf4d718cdf41526d0359a2f3 -->

docker image rm myapp3 -f

<!-- Delete it forcefully -->
<!-- Deleted: sha256:b6a849c79e247dce78530cbc69dd30e7d93494bebf4d718cdf41526d0359a2f3 -->

docker container rm myapp_c1 myapp_c2

<!-- both or ones remove container -->

docker system prune -a

<!-- Remove all the images -->

docker-compose up

<!-- For start the process -->

docker-compose down

<!-- For stop the process, but images, container and volume will remain in docker app -->

docker-compose down --rmi all -v

<!-- For stoping the process and removes all images, container and volume. -->

<!-- //////////////////////////////////////////////// -->

<!-- "Final how to push and pull the images" -->

docker build -t shreyann56sh/myapp .
docker push shreyann56sh/myapp
docker image rm shreyann56sh/myapp
docker images
docker pull shreyann56sh/myapp
