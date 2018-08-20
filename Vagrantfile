# -*- mode: ruby -*-
# vi: set ft=ruby :

# importing yaml
require 'yaml'
# making variable machine and to take input from a yaml file
machines = YAML.load_file("config.yaml")

Vagrant.configure("2") do |config|
	# for all entry in the yaml file refer to that data as machine
	machines.each do |machine|
		# running the following procedure for each instance
		config.vm.define machine['name'] do |machine_vm|
			# calling a defined method for the creation of each vm 
			# and installing scripts
			set_details(machine, machine_vm)
			install_scripts(machine, machine_vm)
		end
	end
end

# creating a method for basic setup, ie
# name of the vm 
# os 
# memory 
# cpus
def set_details(machine, machine_vm)
	machine_vm.vm.box = machine['box']
	machine_vm.vm.provider "virtualbox" do |vb|
		vb.cpus = machine['cpus']
		vb.memory = machine['memory']
	end
	machine_vm.vm.network "forwarded_port", guest: machine['guest_port'], host: machine['host_port'], host_ip: "127.0.0.1"
end

# creating a script to see if any scripts need to be run,
# checking if it is not nil and then running it
def install_scripts(machine, machine_vm)
	unless machine['scripts'].nil?
		machine['scripts'].each do |script|
			machine_vm.vm.provision "shell", privileged: false, path: "vagrant_scripts/#{script}"
		end
	end
end
