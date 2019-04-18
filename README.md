# Instructions

Activiti Admin requires a HTTP connection to your activiti engine. The application needs to have access to the network in order to reach the Activiti REST services

You can test this image with the following command:
```
docker run --rm -p 8080:8080 activiti-admin
```

This will start the container listening to port 8080. 
You can also:
  - Use this image as part of a docker-compose service, include your service and this image
  - Switch the parameters to use the hosts network
  - Change the internal .war file to use "host.docker.internal" on Docker for Mac in order to reach the external network or look at the notes for macOS docker
 
# Changing Activiti Admin Properties
You can change any of the Actiiti Admin properties directly by passing JAVA_OPTS parameters to the container. 
For example, the docker-compose.yaml file contains the following:

```
version: '3'
  
services:
  activiti-admin:
    image: jylups/activiti-admin
    ports:
     - "8888:8080"
    environment:
     - "JAVA_OPTS=-Drest.app.host=http://workflow"
```

This will change the default hosts setup for the REST interface. 

Some options include with default values:
```
# REST endpoint config
rest.app.name=Activiti app
rest.app.description=Activiti app Rest config
rest.app.host=http://localhost
rest.app.port=9999
rest.app.contextroot=activiti-app
rest.app.restroot=api
rest.app.user=admin
rest.app.password=test
```

You can use the sample docker-compose-service-sample.yaml file as a starter to deploy your own application in conjunction with the Activiti Admin interface

Your application can include Activiti's REST api. If you are using spring-boot you can simply include:
```
<dependency>
	<groupId>org.activiti</groupId>
	<artifactId>activiti-spring-boot-starter-rest-api</artifactId>
	<version>${activiti.version}</version>
</dependency>
```

# Notes for macOS Deployments
Docker for Mac provides a special network name for services running on the host machine. You can use "host.docker.internal" instead of "localhost" in order to find your activiti REST services (from your own service application)

