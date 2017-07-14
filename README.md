# Prototyping_devops_pipeline
## Description

Spin up a continuous integration server and a production server using **[Vagrant](https://www.vagrantup.com/)** , **[Docker](https://www.docker.com/what-docker/)** for the automation of setting up the infrastructure and **[Ansible](https://www.ansible.com/)**  for the provisioning of the infrastructure.
the production sever is equiped with a monitoring solution  **[Grafana](https://grafana.com/)** + **[Prometheus](https://prometheus.io/)** for monitoring the production infrastructure and the application running inside it.

for more informations about how to configure Grafana with prometheus https://logz.io/blog/prometheus-monitoring/

## Requirements
### Software requirements

- **Python 2.7** or higher

- **Ansible 2.0** or higher (can be easily installed via pip. E.g: sudo pip install ansible==2.0.0.2)

- **[Vagrant](https://www.vagrantup.com/) 1.7** or higher 

- **Virtualbox**
### Necessary Ansible roles

All the necessary ansible roles that are used in the servers configuration are indicated in the requirements.yml file 
I have developed ansible the roles responsible for the monitoring aspect of the production server configuration precisely
**[Grafana role](https://github.com/sbouii/Grafana_ansible_role)** and  **[Prometheus role](https://github.com/sbouii/Prometheus_ansible_role)** with testing the infrastructure using the infrastructure testing tool **[KitchenCi](http://kitchen.ci/)** just to verify it's configured as expected .

## Supported systems

- Ubuntu

## Usage 

the vagrantfile describes the configuration of the virtual machines to set up .

to use vagrantafile you have to do the following :

1. Download and Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. Download and Install [Vagrant](https://www.vagrantup.com/downloads.html)
3. Install [Ansible](http://docs.ansible.com/intro_installation.html)
4. Open a shell prompt (Terminal app on a Mac) and cd into the folder containing the `Vagrantfile`
5. Run the following command to install the necessary Ansible roles for this profile: `$ ansible-galaxy install -r requirements.yml`

then you can simply setup the two environments by typing `vagrant up` or setup a specific environment  
for example for the continuos integration enviroment type `vagrant up CI-VM `
