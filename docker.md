# Docker Quick Reference Guide


## Setting up Docker on Linux
(Source: [Docker installation instructions](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/#upgrade-docker-ce))

### Pre-requisites

- First remove any old versions of `Docker`, if present
  > `sudo apt-get remove docker docker-engine docker.io`
- Update the repositories and install `linux-image-extra-*` to get `aufs` storage support
  > `sudo apt-get update` <br>
  > `sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual`

### Install Docker-Community Edition

- Install packages to allow `apt` over `https`
  > `sudo apt-get install apt-transport-https ca-certificates curl software-properties-common`
- Get the Docker GPG-Key
  > `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
- Add the stable Docker repositories and update
  > `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"` <br>
  > `sudo apt-get update`
- Install Docker CE
  - Search for the version to install
    > `apt-cache madison docker-ce`
  - Install the specific version using the output of above
    > `sudo apt-get install docker-ce=<Version>` <br>
    > E.g. `sudo apt-get install docker-ce=17.09.1~ce-0~ubuntu` 
  - Test the installation
    > `sudo docker run hello-world`
    
    This should show something like:<br>
    > ``` 
    >  Unable to find image 'hello-world:latest' locally 
    >  ...
    >  Hello from Docker!
    >  This message shows that your installation appears to be working correctly.
    >  ... ```

