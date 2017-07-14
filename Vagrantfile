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

  config.vm.define "Prod-VM" do |cfg|
   cfg.vm.hostname = "Prod-VM"
   cfg.vm.network "private_network", ip: "192.168.33.42"
   cfg.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = 'Prod-VM'
    vb.memory = 1230
    
   end
   cfg.vm.provision :ansible do |ansible|
     ansible.playbook = 'provisioning/cd-setup.yml'
     ansible.groups = {
     "Prod-servers" => ["Prod-VM"],
     }
   end
  end
  
end
