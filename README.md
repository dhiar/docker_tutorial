# Docker Tutorial
### Installation
Youtube tutorial : [part 1](https://www.youtube.com/watch?v=9fWvbqth2NU)

Prerequisite installation :
```sh
sudo apt-get update

sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common 

```

Install access key - supaya server kita terhubung atau memiliki akses dengan server nya docker : 
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Get key docker
```bash
sudo apt-key fingerprint 0EBFCD88
```

Tambahkan ke repository server kita
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update
```

Install docker-ce
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Check status docker
```bash
sudo systemctl status docker
```

Beri user tertentu supaya bisa meng-akses docker
```bash
sudo usermod -aG docker <username>

sudo usermod -aG docker dhiar
```

Restart server
```bash
sudo restart
```

Youtube tutorial : [part 2](https://www.youtube.com/watch?v=aM4DPvhFBjc)Restart server

Lihat versi docker
```bash
docker -v
docker version
```

Lihat informasi docker
```bash
docker info
```

Example : pull image httpd
```bash
docker pull httpd:2.4-alpine
```

Melihat list images
```bash
docker images
```

Delete image
```bash
docker image rm -f mysql:latest
```


Create container
```bash
docker container create --name web httpd:2.4-alpine
```

lihat container
```bash
docker ps -a
docker container ls
```

hapus , start, stop container
```bash
docker container <rm,start,stop> web
```

Create container dengan port
```bash
docker container create --name web -p 8080:80 httpd:2.4-alpine
```

Membuat simple website image menggunakan Dockerfile
```
# Dockerfile
FROM httpd:2.4-alpine
COPY . /usr/local/apache2/htdocs

# index.html
```

Build image dengan Dockerfile
```bash
docker build -t mywebsite:1.0 .
```

Start image secara langsung (Sebenarnya ada 3 proses)
1. Pull
2. Container create
3. Start container
```bash
docker run --name wp -p 3040:80 -d wordpress:latest
# -d artinya adalah image yg akan gunakan
```

Membuat container mysql
```
docker run --name db -e MYSQL_ROOT_PASSWORD=manager247 -d mysql:5.7
```

Masuk container (name)db mysql
```
docker exec -it db mysql -u root -p
```

List network
```
docker network ls
```

Help network
```
docker help network
```

Membuat docker network
```
docker network create net-wp
```

Connect wordpress dengan DB
```
docker network connect net-wp db
```

Connect wordpress dengan Wordpress
```
docker network connect net-wp wp
```

List detail connect
```
docker network inspect net-wp
```