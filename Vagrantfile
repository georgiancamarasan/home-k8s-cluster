# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

VAGRANT_NETWORK_IP = "192.168.56.10"

Vagrant.configure("2") do |config|
  config.vm.box = "arch"

  config.vm.network :private_network, ip: VAGRANT_NETWORK_IP
  config.vm.hostname = "k8s-ctrl"

  config.vm.provider "virtualbox" do |virtualbox|
    virtualbox.name = "k8s-ctrl"
  end

  config.vm.provision :ansible do |ansible|
    ansible.limit = "all"
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "inventory/vagrant.ini"
    ansible.verbose = "vv"
    # ansible.extra_vars = { target: VAGRANT_NETWORK_IP }
  end
end
