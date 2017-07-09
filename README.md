# Why Docker and Ansible Laboratory
Everytime I do automation, I usually goes with [Chef](https://www.chef.io/) because this is the tool I have more experience, although, I'm not passionate about any specific tool and also I get no money from the vendors to advertise one or another. Now I decided it's time to learn a new tool and the [Puppet](https://puppet.com/) architecture is quite similar to Chef because they both are pull based and I was decided to learn a new push based tool. That's why I chose [Ansible](https://www.ansible.com/)

If you want to go deeper with Ansible, I would recommend to take a look in those links below:

[Ansible (1/4)](https://sysadmincasts.com/episodes/43-19-minutes-with-ansible-part-1-4)   
[Ansible (2/4)](https://sysadmincasts.com/episodes/45-learning-ansible-with-vagrant-part-2-4)   
[Ansible (3/4)](https://sysadmincasts.com/episodes/46-configuration-management-with-ansible-part-3-4)   
[Ansible (4/4)](https://sysadmincasts.com/episodes/47-zero-downtime-deployments-with-ansible-part-4-4)   
[Vagrant with Ansible](https://www.youtube.com/watch?v=Defm3i9jYvo)

This automation will only bring you some hosts with docker, if you decide, you can then create a cluster using docker swarm.
In order to do that, choose one of the servers, ssh into it and then type:
```console
docker swarm init --advertise-addr <MANAGER-IP>
```

In the example below you can see a expected result:
```console
$ docker swarm init --advertise-addr 192.168.99.100
Swarm initialized: current node (dxn1zf6l61qsb1josjja83ngz) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join \
    --token SWMTKN-1-49nj1cmql0jkz5s954yi3oex3nedyz0fb0xx14ie39trti4wxv-8vxv8rssmk743ojnwacrr2e7c \
    192.168.99.100:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```
After that, you can connect to the other hosts and join the cluster.

## Prerequisites

### Installed on your desktop
* Fedora 24 (My host Operating System)
* Vagrant 1.9.4
* Virtualbox 5.1.20
* Ansible 2.3.1

### Will be installed by the automation
* CentOS 7
* mDNS
* Docker

## Features
* Create and boot VirtualBox instances
* Provision the hosts with all necessary tools
* You can SSH into the instances using ```vagrant ssh <host>```
* Automatic SSH key generation to access your hosts through vagrant

## Usage
After install vagrant and virtualbox on your desktop, you can clone this repo, then you can just bring up the environment with ```vagrant up``` command, make sure you are in the right directory and Vagrantfile is on the same path where you type the command to start the provisioning.   
Depending on how many hosts you require for your environment, you can change the host variable 'docker_boxes' on Vagrantfile.   
As soon as you have your topology up and running, you can start playing with your new docker boxes   
Keep in mind that this is my personal laboratory, you can prepare you're production environment following this steps, but make sure you know what you're doing.