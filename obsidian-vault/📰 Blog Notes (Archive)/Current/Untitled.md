---
tags: 📰
---

# Docker on Windows with WSL 2

## Intro
---

With the licensing changes around Docker Desktop I've been on a journey to investigate the possibilities of just running the Docker Engine, with other kinds of tooling and WSL 2 (Window Subsystem for Linux). For someone who is mostly focusing (at the moment) of leveraging this for development purposes I'm happy to not be mired in licensing woes; with an added bonus being that I get some further understanding of the 'guts' around how all of this operates.

I've pooled together numerous sources and gone through the basic setup I followed. Where I have bolted together components from other articles/blogs I have provided a detailed breakdown to cite all sources (so many thanks to everyone who has produced excellent content on this so far).

Here's how my adventure went down, buckle up!

## Clear Down Existing Docker Components
---

Before starting, ensure you you remove any current installation of Docker Desktop (taking appropriate backup measures as required). Navigate to 'Settings -> Apps & features -> Search for Docker Destop' and select uninstall. With this removed, you are primed to install WSL 2 on Windows.


## Install WSL 2 (Ubuntu)
---

You do have options around which Linux distribution you want, but for ease and brevity (and familiarity if I am being brutally honest) I moored myself up to Ubuntu.

To install WSL run the following command from the terminal (I'm using the powershell terminal inside Visual Studio code).

```shell
wsl --install -d ubuntu
```

After running this command you should see an Ubuntu terminal pop into existence. Provide a default UNIX user account name of your choice and provide a password (and confirm it) when prompted.

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


## Install the Docker Engine on WSL2

### Setup a Docker Repository

For the next set of commands we will be executing these using the Ubuntu (WSL) terminal in Visual Studio Code (or something like bash if you are connected to WSL already).

As you can see from my screenshot, when I ran `wsl -l -v` I hadn't yet uninstalled Docker Desktop. At this stage, I backtracked and uninstalled it (which you, if you are following this guide, should have already done so). Then, for sanity, I ran the following to ensure I have all Docker components fully removed:

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

A prerequisite to installing the Docker Engine itself is to set up a Docker repository. Once in place, you can install and update Docker from this repository.

Back over to the WSL terminal window...

In order to resynchronise `apt`  package indexes (from source) run the following.

```bash
sudo apt-get update
```

The `app` package tool can be configured to a repository over https as follow. (press 'Y' and enter when prompted to continue):

```bash
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

To save from any security headaches we next retrieve the official Docker GPG key: 

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

For more information on GPG see: https://www.digitalocean.com/community/tutorials/how-to-use-gpg-to-encrypt-and-sign-messages

Why use a GPG key for downloading packages: https://www.quora.com/Why-do-we-require-a-GPG-key-downloading-Docker-packages

In essence, we want to ensure we are dealing with unmodified and secure source material when downloading packages.

To finish configuring a ***stable*** repository execute the following:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine

```bash
sudo apt-get update
```

Press 'Y' and then enter to confirm ->

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Start the Docker Engine:

```bash
sudo service docker start
```

Verify docker is running:

```bash
docker -v
```

You should see verification, something like `Docker version 20.10.14, build a224086` .

Let's run the Docker hello-world image and confirm we're fully up and running:

```bash
docker run hello-world
```


### Manage Docker as Non-root User

Adding your specific UNIX user to the 'docker' group is a particular nice piece of frosting on the cake, that allows the running of docker commands as the non-root user.

The 'docker' group already existed in my case, with my assumption being that the engine installation created this for me. You are able to verify this with the following command regardless, and this will prompt if the group already exists:

```bash
sudo groupadd docker
```

To add your UNIX user to the group, run this command, substituting in your username in place of '$USER':

```bash
sudo usermod -aG docker $USER
```


## Tooling

Two key extensions to obtain at this point, before going any further, are 'Remote - WSL' and 'Docker Explorer'. Remote WSL enables you to connect to and open folders within WSL, enabling you to open a version of VS Code in the context of WSL. With VS Code connected to WSL you can add extensions just to this particular 'flavour' of VS Code; this is where Docker Explorer comes in. When installing Docker Explorer in the WSL connected application context extra functionality is added to the standard Explorer pane, allowing management of Images and Containers using GUI components.

Start with installing Remote WSL in VS Code, as shown:

IMAGE

Then, on the footer bar in VS Code, in the bottom lefthand corner, you can 'Open a Remote Window':

IMAGE

This will open a subset of command palette options, when you can select a 'New WSL Window':

IMAGE

Picking this will launch a new instance of VS Code bound to WSL. So far, so good! Inside this new window instance we then need to hunt out Docker Explorer. I very much messed up here on my first run through and installed this as an extension in the wrong environment, if you happen to do this by mistake you'll see, as per my second screenshot below, that VS Code will prompt you to 'Install in WSL: Ubuntu':

In the WSL VS Code window you should now see these additional panes in the Explorer where you can manage Images and Containers (double-clicking an entity will run a command to get filtered details for the particular Container).

## Spin up a SQL Server 2017 (Latest) Container

As a test run, which we will tear down in short order, let's try and pull down the latest SQL Server 2017 Image for kicks. Hit up the WSL terminal and start by pulling the Image.

```bash
docker pull mcr.microsopft.com/mssql/server:2017-latest
```

Verify the existence of the Image by running:

```bash
docker image ls
```

Then, let's spin up a SQL Server instance for the latest 2017 image that we have just pulled down. Ensure that you specify a strong password in place of '{YOUR_STRONG_PASSWORD}' (that meets the password requirements for SQL Server).

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD={YOUR_STRONG_PASSWORD}" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Once this is completed, verify the image is up and running as follows:

```bash
docker container ls
```

If you specifiy a password that does not meet the SQL Server requirements you may find that the container doesn't start up, which isn't an issue as we'll be deleting this momentarily to pull Images and spin up Containers using Docker Compose. The Container may be in a restart/retry loop, but you can check that it exists by running:

```bash
docker container ls -a
```

### Docker Compose

In my use case, I have created a simple 'docker-compose.yml' file that is designed to provide a stock SQL Server (2017) setup alongside a MongoDB instance, with Mongo Express in play so I have a basic web frontend.

To begin, you'll need to install the latest version of Docker Compose. Use this link as a reference...

Check latest version: https://docs.docker.com/compose/install/

...then, run the following commands in tow to install it and apply executable permissions to the binary:

```bash
sudo curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

You can use the following example 'docker-compose.yml' file as a guide. At the time of writing this guide the 'latest' image for 'mongo-express' was pulling a pre-alpha version, which caused complete and utter chaos with my local setup. Please review all versions and ensure you are happy with the settings before proceeding.

```yml
version: '3.1'

services:
  sql-server-db:
    container_name: sql-server-db
    image: mcr.microsoft.com/mssql/server:2017-latest
    restart: always
    ports:
      - "1433:1433"
    environment:
      SA_PASSWORD: "{YOUR_STRONG_PASSWORD}"
      ACCEPT_EULA: "Y"
  mongo:
    image: mongo:latest
    container_name: mongo-db
    restart: always
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: {PASSWORD}
    ports:
      - 27017:27017
  mongo-express:
    image: mongo-express:0.54
    container_name: mongo-express
    restart: always
    ports:
      - 8081:8081
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: root
      ME_CONFIG_MONGODB_ADMINPASSWORD: {PASSWORD}
    depends_on:
      - mongo
```

The Mongo passwords (and other values, such as ports) do not require quotes, although the convention here is something to be investigated further. You'll also note that 'restart: always' is specified, which means you will not have to manually start Containers in future when Docker springs into life.

Place a file called 'docker-compose.yml' into your Windows file system with the above content, I have placed this in a folder called 'DockerCompose':

IMAGE

Within a WSL terminal you can access a Windows folder using '/mnt', I changed my directory to this location using this command:

```bash
cd /mnt/c/dockercompose
```

Once you have changed directory to the location container the 'docker-compose.yml' you are execute docker-compose to pull down all of the relevant Images and configure Containers:

```text
docker-compose up
```

## Verify Setup

Verifying you are in a good spot isn't too tricky. First, in VS Code, verify that Containers are present and running (denoted with a green colour), as illustrated:

IMAGE

Next, let's take Mongo Express for a spin by attempting to access it via 'http://localhost:8081' (the default port for this installation). You should see the web interface in all its glory:

IMAGE

For SQL, if you have SSMS (although there are other ways, including a CLI interface, to verify this works) you can follow this process. The first thing you'll need is the generated Container name for SQL Server, which you can obtain using 'docker container ls':

IMAGE

With this in hand, pop on over to SSMS and adjust the 'Server name' using the following convention, ensuring you use the 'sa' password you specified in your 'docker-compose.yml' file during setup (the port should be 1433):

```text
convention: 127.0.0.1\{container-name}, {container-port}
```

IMAGE

You should now be connected to your SQL instance running in Docker!

It is possible to right-click on any Container entity in VS Code and 'inspect' (get configuration details), get 'Statistics' or scour 'Logs' as required, so you've always got plenty of actions you can take if you end up getting caught out. 

---

## WSL Refinements

Two additional files can be used to tailor and smarten up your configuration; the 'wsl.config' and 'wsl.conf'. For a complete list of options available you can peruse this link.

https://docs.microsoft.com/en-us/windows/wsl/wsl-config



```php
sudo chown -R myuser /path/to/folder
```


wsl.conf

```
[boot]
command = service docker start
```

---

.wslconfig

```
# Settings apply across all Linux distros running on WSL 2
[wsl2]

# Limits VM memory to use no more than 4 GB, this can be set as whole numbers using GB or MB
memory=2GB 

# Sets the VM to use two virtual processors
processors=2

# Turn off default connection to bind WSL 2 localhost to Windows localhost
localhostforwarding=true

# Turns on output console showing contents of dmesg when opening a WSL 2 distro for debugging
debugConsole=true


### Connectivity

---


```text
sudo apt install net-tools
```

https://superuser.com/questions/1594420/cant-access-127-0-0-180-outside-of-wsl2-ubuntu-20-04

Restart-Service LxssManager

Run as admin:

```None
Set-ExecutionPolicy -Scope CurrentUser
```

Type RemoteSigned

---

## Starting WSL on Startup (Windows)

For extra brownie points and cherries on top you could opt to start WSL on boot of Windows. This article looks like a great starting point to get you squared away:

https://medium.com/swlh/how-to-run-ubuntu-in-wsl2-at-startup-on-windows-10-c4567d6c48f1

---


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

 
docker pull mcr.microsoft.com/mssql/server:2017-latest
 

SQL SA: [XXX]

---

version: '3.1'

  

services:

 sql-server-db:

 container_name: sql-server-db

 image: mcr.microsoft.com/mssql/server:2017-latest

 restart: always

 ports:

 - "1433:1433"

 environment:

 SA_PASSWORD: "{PASSWORD}"

 ACCEPT_EULA: "Y"

 mongo:

 image: mongo:latest

 container_name: mongo-db

 restart: always

 environment:

 MONGO_INITDB_ROOT_USERNAME: root

 MONGO_INITDB_ROOT_PASSWORD: {PASSWORD}

 ports:

 - 27017:27017

 mongo-express:

 image: mongo-express:0.54

 container_name: mongo-express

 restart: always

 ports:

 - 8081:8081

 environment:

 ME_CONFIG_MONGODB_ADMINUSERNAME: root

 ME_CONFIG_MONGODB_ADMINPASSWORD: {PASSWORD}

 depends_on:

 - mongo