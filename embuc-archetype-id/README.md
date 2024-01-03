
This is a multi module maven project with two modules, one named backend contains simple Spring Boot app and other has
{React/Angular/Vue/etc} frontend. Maven builds frontend first and unpacks it and includes in building backend (boot jar
file).
During development both project can be run in separate servers (embedded tomcat for boot and express for frontend) 
independently.

# Frontend
run frontend server (from frontend folder):
### `npm run dev`

## Backend

run backend server (from backend folder):
### `mvn spring-boot:run`

## How to deploy

You can run this as executable jar (mind usage of profiles depending on the environment) e.g.:

#### Locally (jar)

`$> java  -Xmx256M -jar backend.jar &`

## Deploy with Docker

Look inside README.md in backend module for details on how to build and run docker container image with this application.
~~~~