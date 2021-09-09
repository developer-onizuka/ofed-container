# ofed-container

```
$ uname -r
5.4.0-42-generic
```

```
git clone https://github.com/Mellanox/ofed-docker.git
cd ofed-docker/
sudo docker build -t ofed-driver --build-arg D_BASE_IMAGE=ubuntu:20.04 --build-arg D_OFED_VERSION=5.3-1.0.0.1 --build-arg D_OS=ubuntu20.04 --build-arg D_ARCH=x86_64 ubuntu/
sudo docker run --rm -it --name="ofed" --privileged ofed-driver
```
