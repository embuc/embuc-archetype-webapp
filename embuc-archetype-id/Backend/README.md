#### Run dev server

    mvn spring-boot:run

#### Run built jar

    java -jar target/backend.jar

#### Build docker container

    ./mvnw clean install -Pdocker


#### Run docker container (on Port 8081) With specified env-profile (if you define any)

    docker run  --add-host host.docker.internal:host-gateway -e SPRING_PROFILES_ACTIVE=local -d --name yuor-container-name -p 5000:8181 backend

#### Check for running containers

    docker ps 

#### Check for running containers even stopped/crashed

    docker ps -a

#### Stop running container

    docker stop backend

#### List Docker images

`$> docker images`

#### Export portable Docker image

`$> docker save -o backend.tar backend:latest`

#### Import Docker image

`$> docker load -i backend.tar`

#### Notes on Docker

Ensure Docker is Running: Before anything else, make sure Docker is running on your machine.

1. Permission on /var/run/docker.sock (Linux): If you're on Linux, the plugin might not have permissions to access Docker's Unix socket. You can grant permissions with:

`sudo chmod 666 /var/run/docker.sock`

Note: This method makes the Docker control socket world-readable/writable and is not recommended for production systems due to security reasons.
A safer approach would involve adding your user to the docker group.

2. Docker Desktop (Windows): If you're using Docker Desktop for Windows, ensure that the
   "Expose daemon on tcp://localhost:2375 without TLS" option is enabled in Docker settings.
   After enabling this, you can set the Docker host as tcp://localhost:2375. (but you don't Have to as this is the default)
