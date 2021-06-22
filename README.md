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