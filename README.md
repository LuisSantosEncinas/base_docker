## Docker Base project.
```bash
This project starter kit will create a base template using on Drupal Projects
```
## Docker images based
```bash
1. Ubuntu: Ubuntu latest official image
```
## Starting the Dockerfile environment

## 1. Build Docker image
```bash
docker build -t ubuntu:v1 . --no-cache=true
```
## 2. Run Docker image. The -v argument set the VOLUME we want to use inside the container.
```bash
docker run -v /home/ec2-user/environment/base_docker/content:/var/www/html -d -p 8080:80 ubuntu:v1
```
## Manage created images
```bash
## List all dangling images
docker images -f dangling=true

## Delete all dangling images
docker images -f dangling=true -q | xargs docker rmi

## Force delete all dangling images
docker images -f dangling=true -q | sudo xargs docker rmi -f
```
## Delete specific image by NAME
```bash
docker rm -fv <NAME>
```

## Listing your components
Whenever you require some container id or have to check what you have running
you can use these commands:

```bash
# List your containers
docker container ls
# List your images
docker image ls
# List your volumes
docker volume ls
# List your networks
docker network ls
# Most used:
docker ps -a
```
## Cleaning up your components
Most of the time when you get into disk space issues you want to check what
components you can get rid of. So before you execute any of the commands below,
always check what you have on your system by listing your components.

```bash
# Clean up "stopped" containers
docker container prune
# Clean up "unused" images, you can add the --all option if you want to remove
# all unused images instead of just the dangling ones.
docker image prune
# Clean up "unused" volumes
docker volume prune
# Clean up "unused" networks
docker network prune
# Clean up everything:
docker system prune
 ## This will remove:
            - all stopped containers
            - all networks not used by at least one container
            - all images without at least one container associated to them
            - all build cache
# Check orphan docker volumes
docker volume ls -qf dangling=true
# Prune orphan docker volumes
docker volume rm $(docker volume ls -qf dangling=true)
```

### Make your life easier using alias

```bash
alias dcweb="docker-compose exec web "
```

### Run single commands on the running web service with an alias

```bash
dcweb composer --version
```
