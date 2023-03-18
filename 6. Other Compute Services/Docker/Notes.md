# Docker

## Docker is a software development platform to deploy apps

## Containers
* Apps are packaged in containers that can be run on any OS 
* Apps run the same, regardless of where they're run 
1. Any machine 
2. No compatibility issues 
3. Predictable behavior
* E.g. An EC2 instance can have containers running Java, Node, MySQL code separately.
* Docker images are stored in Docker Repositories 
* Public: Docker Hub: https://hub.docker.com
* Can find base images for many technologies 
1. Ubuntu
2. MySQL
3. NodeJS 
* Private: Amazon ECR (Elastic Container Registry) to store private docker images 
* Docker VS Virtual machines 
* Docker is a "Sort of" virtualization technology but not exactly
* Resources are shared with the host => Many containers on one server