# Vagrant

## About this repo
- This repo is configured to deploy a Vagrant vm running centos-7
- The Vagrantfile is configured so that it will run a script that 
	- installs gits via the yum package 
	- git clones the python-systemd-http-server
	- installs python-systemd-http-server via running the make install command
	- uses systemctl to run and enable services

## Build
```vagrant up```

## Run 

```localhost:8080```
