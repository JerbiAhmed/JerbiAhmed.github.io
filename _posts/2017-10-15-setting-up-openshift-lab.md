---
layout: post
title:  "Setting up a local Openshift Lab"
date:   2017-10-15
excerpt: "Openshift installation instruction"
tag:
- Openshift
- Ubuntu
- Debian
- Windows
- Orchestration
- DevOps
---

[//]: # (ToDo: add links to other articles)

This tutorial series aims to provide you with an introduction to container and container orchestration technology using Docker, Kubernetes, and Red Hat OpenShift Container Platform.

This DevOps Tutorial is Part 1 of my series on Red Hat Openshift. Check out the other articles:
1. [Setting Up the Lab Environment][1]
2. [Overview of the Docker Architecture][2]
3. [Managing the Life Cycle of Containers][3]
4. [Building Custom Container Images with Dockerfile][4]
5. [Creating Kubernetes Resources][5]
6. [Creating Applications with Source-to-Image facility of Red Hat OpenShift][6]

# Setting Up the Lab Environment

This serie includes a number of guided exercises, which give you an opportunity to practice the skills you are learning. To complete these exercises, you need to configure a practice environment that you completely control.

The installation of the lab environment consists of the following tasks:
1. Install Oracle VirtualBox to serve as a virtualization manager for Red Hat CDK .
2. Install Red Hat CDK 3.
3. Verify the installation by starting an OpenShift cluster.


## Install Oracle VirtualBox

```shell
wget -q -O- http://download.virtualbox.org/virtualbox/debian/oracle_vbox_2016.asc | sudo apt-key add -
sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list'
sudo apt update
sudo apt-get install virtualbox-5.1
```
## Install RED HAT CDK 3

Download the Red Hat Container Development Kit 3 from [here][7], you may need to login or to create a Red Hat developer account if you don't have one already.  
Download the appropriate package for the operating system then rename the downloaded file to **`minishift​`** and copy the binary file to **`/usr/local/bin`​** or another directory that is accessible in your command-shell path.  
On Windows rename your file to **minishift.exe** and add its directory to path env variable.


```shell
sudo mv cdk-3.1.1-1-minishift-linux-amd64 /usr/local/bin/minishift
sudo chmod +x /usr/local/bin/minishift
```

## Configure and run Openshift

First we need to change two persistent configuration options as we will use the virtualbox driver and will allocate 2 GB of RAM which should be enough for our lab.

### On linux 

```shell
minishift setup-cdk
minishift config set vm-driver virtualbox
minishift config set memory 2048
```

### On windows

Open a powershell and browse to minishift.exe path then run it.

```shell
cd c:/minishift
./minishift.exe setup-cdk
./minishift.exe config set vm-driver virtualbox
./minishift.exe config set memory 2048
```
The minishift config​ command may issue a warning message, "No Minishift instance exists…".
This message can safely be ignored.  
Execute the following command to start an OpenShift cluster when prompted enter your Red Hat developer account credentials.

### On linux 

```shell
minishift start
```
### On Windows

```shell
./minishift.exe start
```


[1]: https://jerbiahmed.github.io/setting-up-openshift-lab
[2]: /
[3]: /
[4]: /
[5]: /
[6]: /
[7]: https://developers.redhat.com/products/cdk/download