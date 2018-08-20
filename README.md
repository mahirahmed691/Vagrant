# Vagrant

##About this repo
- This repo is configured to deploy a Vagrant vm running centos-7
- The Vagrantfile is configured so that it will run a script that 
	- install gits
	- git clones the python-systemd-http-server
	- install python-systemd-http-server via running the make install command
	- use systemctl to run and enable services
