# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.box_check_update = false
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = 2048
  end

  (0..2).each do |i|
    config.vm.define "controller-#{i}" do |node|
      node.vm.hostname = "controller-#{i}"
      node.vm.network "private_network", ip: "10.240.0.1#{i}"
      node.vm.provision :hosts, :sync_hosts => true
      node.vm.provider "virtualbox" do |vb|
        vb.name = "controller-#{i}"
      end
      node.vm.provision "shell", path: "heartbeat.sh"
    end
  end

  (0..4).each do |i|
    config.vm.define "worker-#{i}" do |node|
      node.vm.hostname = "worker-#{i}"
      node.vm.network "private_network", ip: "10.240.0.2#{i}"
      node.vm.provision :hosts, :sync_hosts => true
      node.vm.provider "virtualbox" do |vb|
        vb.name = "worker-#{i}"
      end
    end
  end
end
