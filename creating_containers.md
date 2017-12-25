# Creating Custom Containers

## The `Dockerfile`

The `Dockerfile` defines the environment hosted in the container. Applications hosted on this container will behave the same way irrespective of the hosting machine.

### Components of the `Dockerfile`

- `FROM` specifies the base image from which to start the docker image
  > E.g.: `FROM ubuntu:14.04`
- `RUN` lists the commands which are run when the docker image is built
  > E.g.: `RUN apt-get install python python-numpy python-scipy`
- `WORKDIR` specifies the working directory of the container
  > E.g.: `WORKDIR /experiment` sets `/experiment` in the docker as the working directory
- `ADD` adds the specified directory to the docker image
  > E.g.: `ADD <path to directory> /experiment` adds the directory given in the path to `/experiments` in the container
- `ENV <env name>` defines the environment variables
  > E.g.: `ENV MALMO_XSD_PATH /root/Malmo/Schemas`
- `CMD` specifies the command to run when the container launches
- Alternatively, `ENTRYPOINT` can be used for the same purpose
  > E.g.: `CMD ["python", "<path to script/program>"]` <br>
  > E.g.: `ENTRYPOINT ["<path to program1>", "<path to program2>", ...]`


### Sharing the Image

- Use `docker push` to submit the image to the Docker cloud repository 
  - Caveat: One should build the image using the `username/reponame:tagname` format
    > `docker build -t <username>/<repo>:<tag> .`
  - On then we can use `docker push <username>/<repo>:<tag>` command; else push fails.

[Home](./docker.md) | [Back](./using_docker.md)
