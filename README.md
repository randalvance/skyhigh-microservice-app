# SkyHigh Microservice Reference App
A reference app I created where I apply (and continuously improve) everything I've learned about designing microservices applications.

# Components
This app is composed of multiple microservices located on separate GitHub repositories.

| Name | Description |
|------|-------------|
|[Web FrontEnd](https://github.com/randalvance/skyhigh-web)|A web application made in Angular|
|[Enrollment Microservice](https://github.com/randalvance/skyhigh-enrollment-service)|The api for enrolling students. Created with node.js|
|[Students Microservice](https://github.com/randalvance/skyhigh-enrollment-service)|The API for managing students. Created using ASP.NET Core with postgresql as database.|
|[Subjects Microservice](https://github.com/randalvance/SkyHigh.Services.Subjects)|The API for managing subjects. Created using ASP.NET Core|

Additionally, RabbitMQ was used for messaging and integration events.

# Installation

Checkout all the repositories.

## Web FrontEnd
* Run `npm install`
* Run `ng build --prod`
* Run `docker build -t skyhigh-web .`

## Enrollment Microservice
* Run `docker build -t skyhigh-services-enrollment .`

## Students Microservice
* Run `dotnet publish -o ./publish`
* Run `docker build -t skyhigh-services-students .`

## Subjects Microservice
* Run `dotnet publish -o ./publish`
* Run `docker build -t skyhigh-services-subjects .`

## Running the Docker Containers
After everything is installed, go to the root folder of this repository and run:
```
docker-compose up -d
```
If everything is running, you should see this when you do a `docker ps` command.
```
CONTAINER ID        IMAGE                         COMMAND                  CREATED             STATUS              PORTS                                                                             NAMES
9387fce74dde        skyhigh-services-students     "dotnet SkyHigh.Se..."   21 minutes ago      Up 3 seconds        0.0.0.0:8181->80/tcp                                                              skyhigh-services-students-instance
1a3c358e7d28        skyhigh-services-enrollment   "npm start"              21 minutes ago      Up 3 seconds        0.0.0.0:3001->3001/tcp                                                            skyhigh-services-enrollment-instance
e76425fc86cc        skyhigh-services-subjects     "dotnet SkyHigh.Se..."   21 minutes ago      Up 3 seconds        0.0.0.0:8182->80/tcp                                                              skyhigh-services-subjects-instance
78db7d26909e        rabbitmq                      "docker-entrypoint..."   21 minutes ago      Up 4 seconds        4369/tcp, 0.0.0.0:5672->5672/tcp, 5671/tcp, 25672/tcp, 0.0.0.0:15672->15672/tcp   skyhigh-rabbitmq
a635d0d2de22        skyhigh-web                   "nginx -g 'daemon ..."   21 minutes ago      Up 3 seconds        0.0.0.0:8001->80/tcp                                                              skyhigh-web-instance
1e9d7f38aad0        mongo                         "docker-entrypoint..."   21 minutes ago      Up 4 seconds        0.0.0.0:27017->27017/tcp                                                          skyhigh-enrollment-mongodb
627a2cb213a8        postgres                      "docker-entrypoint..."   21 minutes ago      Up 4 seconds        0.0.0.0:5432->5432/tcp                                                            skyhigh-students-db
```
# Accessing the Web Front End
You can access the web application in:
```
http://localhost:8001
```