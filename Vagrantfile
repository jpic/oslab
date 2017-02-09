# -*- mode: ruby -*-
# vi: set ft=ruby :
#
Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/centos7"
  # Faster mirror than hashicorp
  config.vm.box_url = "http://pub.yourlabs.org/geerlingguy.centos7.box"

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  config.vm.provider "virtualbox" do |vb|
    # vb.gui = true
    vb.memory = "2048"
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  config.vm.define "controller" do |controller|
    controller.vm.hostname = "controller"
    controller.vm.network :private_network, ip: "172.31.255.20"
  end

  config.vm.define "compute0" do |compute0|
    compute0.vm.hostname = "compute0"
    compute0.vm.network :private_network, ip: "172.31.255.21"
  end

  config.vm.define "compute1" do |compute1|
    compute1.vm.hostname = "compute1"
    compute1.vm.network :private_network, ip: "172.31.255.22"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "rdo.yml"
    ansible.groups = {
      "controllers": ["controller"],
      "computes": ["compute0", "compute1"],
    }
    ansible.verbose = "v"
    ansible.limit = "all"
  end
end
