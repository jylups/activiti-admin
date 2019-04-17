# Activiti Admin Application
  
This is a contenerized version of the Activiti Addmin application. This package includes the following sources:
https://github.com/Activiti/Activiti/tree/6.x/modules/activiti-admin

This image leverages Tomcat's latest version when built from source code.

For more information about Tomcat please see:

https://hub.docker.com/_/tomcat
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
  - Change the internal .war file to use "host.docker.internal" on Docker for Mac in order to reach the external network 


