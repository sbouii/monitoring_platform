# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  
  config.vm.box = "centos/7"

  # Disable automatic box update
  config.vm.box_check_update = false

  # Disable the default /vagrant share
  config.vm.synced_folder ".", "/vagrant" , disabled: true  

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
