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

With the installation complete, I noted that VS Code added a Ubuntu (WSL) option for use when creating new terminal windows, nice!

![[ubuntu-terminal-in-vs-code.jpg]]

I've gone through this process a couple of times and it is possible that version 1, instead of 2, can be installed. Verify this by using the following command (back in powershell for the moment):

```text
wsl -l -v
```

Check the version as follows:

![[check-wsl-ubuntu-version.jpg]]

If you are running version 1, this can be easily altered by using the following command:

```text
wsl --set-version Ubuntu 2
```


## Install Docker Engine on WSL2

### Setup a Docker Repository

As you can see from my screenshot, when I ran `wsl -l -v` I hadn't yet uninstalled Docker Desktop. At this stage, I backtracked and uninstalled it (which you, if you are following this guide, should have already done so). Then, for sanity, I ran the following to ensure I have all Docker components fully removed (again, running this in powershell):

```text
sudo apt-get remove docker docker-engine docker.io containerd runc
```

A prerequisite to installing the Docker Engine itself is to set up a Docker repository. Once in place, you can install and update Docker from this repository.

Back over to the WSL terminal window...

In order to resynchronise `apt`  package indexes (from source) run the following.

```text
sudo apt-get update
```

The `app` package tool can be configured to a repository over https as follow. (press 'Y' and enter when prompted to continue):

```text
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

To save from any security headaches we next retrieve the official Docker GPG key: 

```text
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

For more information on GPG see: https://www.digitalocean.com/community/tutorials/how-to-use-gpg-to-encrypt-and-sign-messages

Why use a GPG key for downloading packages: https://www.quora.com/Why-do-we-require-a-GPG-key-downloading-Docker-packages

In essence, we want to ensure we are dealing with unmodified and secure source material when downloading packages.

To finish configuring a ***stable*** repository execute the following:

```text
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine

```text
sudo apt-get update
```

Press 'Y' and then enter to confirm ->

```text
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Start the Docker Engine:

```text
sudo service docker start
```

Verify docker is running:

```text
docker -v
```

You should see verification, something like `Docker version 20.10.14, build a224086` .

### Hello World!



### Manage Docker as non-root User

Mine already existed (assuming the installation step created this). Verify by running anyway (will just prompt that it already exists):

```text
sudo groupadd docker
```

$USER = your UNIX user.

```text
sudo usermod -aG docker $USER
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