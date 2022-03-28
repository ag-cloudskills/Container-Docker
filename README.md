# Docker
## Docker Installation (Ubuntu)
* Remove old Docker
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```
### Set up repository
1. Update apt and packages to allow apt to use repo over https
```bash
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
2. Add Docker's public GPG key*
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
3. Set up stable docker repo
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  ```
* Install Docker Engine
 Update apt package index and install docker
```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
docker --version
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
### Basic Docker commands
```bash
docker ps
docker ps -a
docker stop <containername/id>
docker rm <containername/id>
docker images
docker rmi <image>
docker pull <imagename>
docker run <imagename>
docker run <imagename> sleep 5
# To be run on running continer
docker exec <containername>  <command>
# to run docker in detach mode
docker run -d <imagename>
docker attach <containerid/name>
```
*docker bash*
```bash
docker run -it centos bash
```
*docker with tag*
```bash
docker run <imagename>:<tagename>
docker run redis:4.0
```
*docker STDIN*
```bash
docker run -i <imagename>
docker run -it <imagename>
#i stands for interative and t stands for conatiner terminal

# Port mapping
docker run -d -p <dockerhostport>:<dockercontainerport>
docker run -d -p 80:8080
docker run -d -p 8081:8080

# Volume mapping
docker run -v <dockerhostmount>:<dockercontainermount>
docker run -v /opt/data:/var/lib/mysql mysql

# docker inspect
docker inspect <conatiner>

# docker container logs
 docker logs <conatinerid>
