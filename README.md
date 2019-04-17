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
 
# Notes for macOS Deployments
Docker for Mac provides a special network name for services running on the host machine. You can use "host.docker.internal" instead of "localhost" in order to find your activiti REST services (from your own service application)

