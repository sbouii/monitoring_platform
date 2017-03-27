# prototyping_devops_pipeline
## Description

it's a prototyping design for continious delivery pipeline with dev, test and prod environement using **[Vagrant](https://www.vagrantup.com/)** and **[Docker](https://www.docker.com/what-docker/)** for the automation of the provisioning .

## Requirements
### Software requirements

- **Python 2.7** or higher

- **Ansible 2.0** or higher (can be easily installed via pip. E.g: sudo pip install ansible==2.0.0.2)

- **[Vagrant](https://www.vagrantup.com/) 1.7** or higher 

- **Virtualbox**

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

then you can simply setup the three environments of the pipeline by typing `vagrant up` or setup a specific environment  
for example for the continuos integration enviroment type `vagrant up CI-VM `
