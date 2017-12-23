# Docker Quick Reference Guide


## Setting up Docker on Linux
(Source: `https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/#upgrade-docker-ce`)

### Pre-requisites

- First remove any old versions of `Docker`, if present
 > `sudo apt-get remove docker docker-engine docker.io`
- Update the repositories and install `linux-image-extra-*` to get `aufs` storage support
 > `sudo apt-get update` <br>
 > `sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual`

