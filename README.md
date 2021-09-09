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
```
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
  name: ubuntu-gpu-ofed
  labels:
    name: ubuntu-gpu-ofed
spec:
  containers:
  - name: ofed-driver
    image: ofed-driver
    command:
    - sleep
    - "3600"
    resources:
      limits:
         nvidia.com/gpu: 1
EOF
```
