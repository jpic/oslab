# -*- mode: ruby -*-
# vi: set ft=ruby :
#
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  # Faster mirror than hashicorp
  config.vm.box_url = "http://pub.yourlabs.org/centos7.box"

  config.vm.define "controller" do |controller|
    controller.vm.network "private_network", ip: "172.31.255.1"
  end

  config.vm.define "compute0" do |compute0|
    compute0.vm.network "private_network", ip: "172.31.255.1"
  end

  config.vm.define "compute1" do |compute1|
    compute1.vm.network "private_network", ip: "172.31.255.1"
  end

  config.vm.provider "virtualbox" do |vb|
    # vb.gui = true
    vb.memory = "2048"
  end

  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
