Docker workshop by TJB

# 1. What is a Docker container?

A proccess tree running within a namespace, networking and file system. 

# 2. Docker daemon

Manages docker containers.

# 3. Docker image

Template for docker container.

# 4. Docker CLI

To manage docker daemon.

# 5. Docker engine

Client-server application.

# 6. Don't use image:latest on production!!! Latest means newest, so it changes in time.
Eg. updating from Java 8 to Java 9 -> If we're doing it smoothly, we're just lucky, but in the other case (some crash) we don't
know what happened, because from our point of view (latest) nothing was changed.
Latest is good for development.

# 7. Where images are stored?

There stored under the docker root. 

# 8. Logs & inspecting container & searching images from terminal

docker logs [container-id] --> see logs of container
docker inspect [container-id] --> see container specification
docker search [some-image-name]

eg: docker search java will return images related to java
