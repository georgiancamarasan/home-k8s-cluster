# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

VAGRANT_NETWORK_IP_GROUP = "192.168.56."

Vagrant.configure("2") do |config|
  config.vm.box = "arch"

  config.vm.define "ctrl" do |ctrl|
    ctrl.vm.network :private_network, ip: VAGRANT_NETWORK_IP_GROUP + "10"
    ctrl.vm.hostname = "k8s-ctrl"

    ctrl.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "k8s-ctrl"
    end
  end

  config.vm.define "node1" do |node1|
    node1.vm.network :private_network, ip: VAGRANT_NETWORK_IP_GROUP + "11"
    node1.vm.hostname = "node1"

    node1.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "node1"
    end
  end

 config.vm.provision :ansible do |ansible|
   ansible.limit = "all"
   ansible.playbook = "playbook.yml"
   ansible.inventory_path = "inventory/vagrant.ini"
   ansible.verbose = "vv"
   # ansible.extra_vars = { target: VAGRANT_NETWORK_IP }
 end
end
