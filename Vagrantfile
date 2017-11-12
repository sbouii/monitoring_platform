# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  
  config.vm.box = "bento/ubuntu-16.04"

  # Disable automatic box update
  config.vm.box_check_update = false

  # Disable the default /vagrant share
  config.vm.synced_folder ".", "/vagrant" , disabled: true
  
  config.vm.define "CI-VM" do |cfg|
   cfg.vm.hostname = "CI-VM"
   cfg.vm.network "private_network", ip: "192.168.33.40"
   cfg.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = 'CI-VM'
    vb.memory = 1120
    
   end
   cfg.vm.provision :ansible do |ansible|
    ansible.playbook = 'provisioning/ci-setup.yml'
    ansible.inventory_path = 'vagrant-inventory.ini'
    ansible.limit = 'CI-VM'
    ansible.verbose = 'v'
    ansible.extra_vars = {
        ansible_python_interpreter: "/usr/bin/python3.5",
    }
   end
  end

  config.vm.define "PROD-VM"do |cfg|
   cfg.vm.hostname = "PROD-VM"
   cfg.vm.network "private_network", ip: "192.168.33.42"
   cfg.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = 'PROD-VM'
    vb.memory = 1230
    
   end
   cfg.vm.provision :ansible do |ansible|
     ansible.playbook = 'provisioning/prod-setup.yml'
     ansible.inventory_path = 'vagrant-inventory.ini'
     ansible.limit = 'PROD-VM'
     ansible.verbose = 'v'
     ansible.extra_vars = {
        ansible_python_interpreter: "/usr/bin/python3.5",
    }
   end
  end
  
end
