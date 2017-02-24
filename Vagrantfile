# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define "iscsi" do |subconfig|
    subconfig.vm.box = "centos/7"
    subconfig.vm.hostname = "iscsi"
    subconfig.vm.network "forwarded_port", guest: 22, host: 2210
    subconfig.vm.network "private_network", ip: "192.168.30.10"
    subconfig.vm.provider "virtualbox" do |vb|
      vb.name = "iscsi"
      vb.memory = "256"
    end
  end

  config.vm.define "pcs1" do |subconfig|
    subconfig.vm.box = "centos/7"
    subconfig.vm.hostname = "pcs1"
    subconfig.vm.network "forwarded_port", guest: 22, host: 2211
    subconfig.vm.network "private_network", ip: "192.168.30.11"
    subconfig.vm.network "private_network", ip: "192.168.40.11"
    subconfig.vm.provider "virtualbox" do |vb|
      vb.name = "pcs1"
      vb.memory = "256"
    end
  end

  config.vm.define "pcs2" do |subconfig|
    subconfig.vm.box = "centos/7"
    subconfig.vm.hostname = "pcs2"
    subconfig.vm.network "forwarded_port", guest: 22, host: 2212
    subconfig.vm.network "private_network", ip: "192.168.30.12"
    subconfig.vm.network "private_network", ip: "192.168.40.12"
    subconfig.vm.provider "virtualbox" do |vb|
      vb.name = "pcs2"
      vb.memory = "256"
    end
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook     = "provisioning/site.yml"
    ansible.install      = true
  end

end
