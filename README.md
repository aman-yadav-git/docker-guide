# Docker
---
### What is Docker?

**Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker's methodologies for shipping, testing, and deploying code, you can significantly reduce the delay between writing code and running it in production.**

### Install Docker 

> Update Fedora & CentOS
To updates package metadata
```
sudo dnf update -y 
```
> Remove old docker packages
This avoids conflicts.
```
sudo dnf remove docker \
                docker-client \
                docker-client-latest \
                docker-common \
                docker-latest \
                docker-latest-logrotate \
                docker-logrotate \
                docker-engine
```

> Add Docker Repository
```
sudo dnf -y install dnf-plugins-core
```
```
sudo dnf config-manager addrepo --from-repofile=https://download.docker.com/linux/fedora/docker-ce.repo
```
This adds official Docker packages.

> Install Docker Engine
```
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```
> Start Docker
```
sudo systemctl start --now docker
```
```
sudo systemctl enable --now docker
```
```
systemctl status docker
```
> Allow Non-root Docker Usage
```
sudo usermod -aG docker $USER
```
```
newgrp docker
```
> Test Docker
```
docker run hello-world
```

If successful then Docker is working.

> Install Docker Desktop on Linux

To install Docker Desktop on Fedora 
Download the latest RPM package `https://desktop.docker.com/linux/main/amd64/`
```
cd ~/Downloads
```
```
sudo dnf install ./docker-desktop-x86_64.rpm
```
```
systemctl --user start docker-desktop
```
It open Docker Desktop UI screen 

Learn Basic Docker First

> Pull image
```
docker pull ubuntu
```
> Run container
```
docker run -it ubuntu bash
```
-i = interactive
-t = terminal

Now you’re inside container.

> List containers
```
docker ps
```
> All containers
```
docker ps -a
```
**Now you can view it on Docker Desktop it will show running containers.**

> Stop container
```
docker stop CONTAINER_ID
```
Remove container
```
docker rm CONTAINER_ID
```

### VERY IMPORTANT CONCEPT

Container != VM

Containers:

share host kernel
lightweight
faster
