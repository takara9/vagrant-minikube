# coding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ##  Minikube仮想マシンの起動
  #
  config.vm.define 'minikube' do |machine|
    machine.vm.box = "ubuntu/xenial64"
    machine.vm.hostname = 'minikube'
    machine.vm.network :private_network,ip: "172.16.10.10"
    machine.vm.provider "virtualbox" do |vbox|
      vbox.gui = false        
      vbox.cpus = 2
      vbox.memory = 2048
    end

    ## Ansible
    #
    machine.vm.provision "ansible_local" do |ansible|
      ansible.playbook       = "minikube.yml"
      ansible.version        = "latest"      
      ansible.verbose        = false
      ansible.install        = true
      ansible.limit          = "minikube"      
      ansible.inventory_path = "hosts"
    end
  end
end
