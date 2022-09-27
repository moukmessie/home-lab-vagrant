# -*- mode: ruby -*-
# vi: set ft=ruby :
RAM = 1024
CPU = 1

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo Welcome to MOUkLab"
 
  config.vm.define "manager" do |manager|
    manager.vm.box = "ubuntu/trusty64"
    #using vagrant-hostupdater
    manager.vm.hostname = "manager"
    manager.vm.network "private_network", ip: "192.168.122.10"
    
    #Provision ansible local
    manager.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "lab.yml"
      ansible.install = true
      ansible.install_mode = :pip
      ansible.pip_install_cmd  = "curl https://bootstrap.pypa.io/pip/3.5/get-pip.py | sudo python"
    end

  end
  config.vm.provider "virtualbox" do |v|
    v.memory = RAM
    v.cpus = CPU
  end
 
  config.vm.define "server_1" do |server_1|
    server_1.vm.box = "debian/jessie64"
      #using vagrant-hostupdater
    server_1.vm.hostname = "server1"
    server_1.vm.network "private_network", ip: "192.168.122.11"
  end
  config.vm.provider "virtualbox" do |v|
    v.memory = RAM
    v.cpus = CPU
  end

    config.vm.define "server_2" do |server_2|
    server_2.vm.box = "debian/jessie64"
      #using vagrant-hostupdater
    server_2.vm.hostname = "server2"
    server_2.vm.network "private_network", ip: "192.168.122.12"
  end
  config.vm.provider "virtualbox" do |v|
    v.memory = RAM
    v.cpus = CPU
  end
end
