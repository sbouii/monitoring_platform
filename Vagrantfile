# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  
   
  config.vm.box = "ubuntu/trusty64"

  # Disable automatique box update
  config.vm.box_check_update = false

  # Disable the default /vagrant share
  config.vm.synced_folder ".", "/vagrant" , disabled: true

  # Update /etc/hosts in all VMs
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.include_offline = true

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
    ansible.groups = {
    "ci-servers" => ["CI-VM"],
    }
   end
  end

  config.vm.define "DEV-VM" do |cfg|
   cfg.vm.hostname = "DEV-VM"
   cfg.vm.network "private_network", ip: "192.168.33.41"
   cfg.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = 'DEV-VM'
    vb.memory = 860
   end
   cfg.vm.provision :ansible do |ansible|
    ansible.playbook = 'provisioning/dev-setup.yml'
    ansible.groups = {
     "dev-servers" => ["DEV-VM"],
     }

   end
  end

  config.vm.define "CD-VM" do |cfg|
   cfg.vm.hostname = "CD-VM"
   cfg.vm.network "private_network", ip: "192.168.33.42"
   cfg.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = 'CD-VM'
    vb.memory = 1230
    
   end
   cfg.vm.provision :ansible do |ansible|
     ansible.playbook = 'provisioning/cd-setup.yml'
     ansible.groups = {
     "cd-servers" => ["CD-VM"],
     }
   end
  end
  
end
