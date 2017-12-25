# Creating Custom Containers

## The `Dockerfile`

The `Dockerfile` defines the environment hosted in the container. Applications hosted on this container will behave the same way irrespective of the hosting machine.

### Sharing the Image

- Use `docker push` to submit the image to the Docker cloud repository 
  - Caveat: One should build the image using the `username/reponame:tagname` format
    > `docker build -t <username>/<repo>:<tag> .`
  - On then we can use `docker push <username>/<repo>:<tag>` command; else push fails.

[Home](./docker.md) | [Back](./using_docker.md)
