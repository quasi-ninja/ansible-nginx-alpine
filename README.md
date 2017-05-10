# An Alpine NGINX container running on Ubuntu

This is one possible solution for creating an Alpine Linux docker container running nginx to service a simple web page over the standard http port.

## Assumptions
* You have Ansible 2.4.0+
* You are using VirtualBox 5.0+ (Other providers are available)
* You are running Vagrant 1.8.1+

## Getting Started

With the above in place the only task remaining is to invoke vagrant.

From the cloned repository execute `vagrant up`

This will initially create an Ubuntu 14.04 instance and using Ansible as the provisioner will install the following packages;

* python-setuptools
* python-dev
* build-essential
* pip
* docker-py

From this point we put the docker in place attach it to the Docker Registry and start create our container.

playbook.yml runs sequentially through each of the tasks, it is not elegant and could be refactored to create separation of concerns but for simplicity it is what it is.

The Dockerfile in nginx-files creates the necessary user accounts and directories to get nginx up and running as well as applying the nginx.conf and static content.

Lastly it starts nginx.
