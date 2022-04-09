---
tags: 📰
---

# Docker on Windows with WSL2

## Intro
---

TBD!


## Clear Down
---

Before starting, ensure you you remove any current installation of Docker Desktop (taking appropriate backup measures as required). Navigate to Settings -> Apps & features -> Search for Docker Destop and uninstall the current installation.


## Install WSL2 (Ubuntu)
---

To install WSL run the following command from the terminal (I'm using the terminal inside Visual Studio code).

```
wsl --install -d ubuntu
```

After running this command you should see an Ubuntu terminal pop into existence. Provive a default UNIX user account name of your choice and provide a password (and confirm it) when prompted.

![[ubuntu-startup-post-installation.jpg]]



![[ubuntu-terminal-in-vs-code.jpg]]

```text
wsl --set-version Ubuntu 2
```


## Install Docker Engine on WSL2
In order to resynchronise `apt`  

```text
sudo apt-get update
```

Then run, hitting 'Y' and enter when prompted to continue.

```text
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

### Original Source Notes

wsl --install -d ubuntu

 

OR (afterwards)

 

wsl --set-version Ubuntu 2

 

https://docs.docker.com/engine/install/ubuntu/

 

 

UNIX username: lewisgrint

Password: [XXX]

 

Then...

 

 

sudo apt-get remove docker docker-engine docker.io containerd runc

 

sudo apt-get update

 

sudo apt-get install \

    ca-certificates \

    curl \

    gnupg \

    lsb-release

               

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

 

echo \

  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \

  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

 

-- Install the Docker Engine

 

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io

 

wsl --set-version

 

sudo service docker start

 

sudo groupadd docker

 

sudo usermod -aG docker $USER

 

newgrp docker

 

 

-- https://hub.docker.com/_/microsoft-mssql-server

 

docker pull mcr.microsoft.com/mssql/server

 

 

SQL SA: [XXX]