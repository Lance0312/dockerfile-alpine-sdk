Dockerfile - alpine-sdk
=======================

Usage
-----

### Create Volumes
```bash
# For RSA key pair and built packages
$ docker volume create --name alpine-sdk-home
# For package cache
$ docker volume create --name alpine-sdk-distfiles
```

### Generate RSA key pair
```bash
$ docker run -it --rm -v alpine-sdk-home:/home/abuild lancechen/alpine-sdk abuild-keygen -a
```

### Build a Package
```bash
$ cd aports/testing/<package>
# Run `abuild checksum && abuild -r` by default
$ docker run -it --rm -v $(pwd):/build -v alpine-sdk-home:/home/abuild -v alpine-sdk-distfiles:/var/cache/distfiles lancechen/alpine-sdk
```
