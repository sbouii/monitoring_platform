# monitoring_platform
## Description

Spin up a production server using **[Vagrant](https://www.vagrantup.com/)** and **[Docker](https://www.docker.com/what-docker/)** for the automation of setting up the infrastructure and Ansible for the provisioning of the infrastructure.
the sever is equiped with a monitoring solution based on **[Grafana](https://grafana.com/)** + **[Prometheus](https://prometheus.io/)** +  **[Cadvisor](https://github.com/google/cadvisor)** for monitoring the production infrastructure and the running containers deployed on it.

For more informations about how to create Grafana Dashboards with prometheus and cadvisor https://logz.io/blog/prometheus-monitoring/

### Workflow ( we will stick only to the slack notification)

![image](https://linoxide.com/wp-content/uploads/2016/12/PromArch.png)


## Requirements
### Software requirements

- **Python 3.5**

- **Ansible 2.2** or higher

- **[Vagrant](https://www.vagrantup.com/) 1.7** or higher 

- **Virtualbox 5.1**
### Necessary Ansible roles

All the necessary ansible roles that are used for the server configuration are indicated in the requirements.yml file.
I have developed the ansible roles responsible for the required monitoring goals, precisely **[Grafana role](https://github.com/sbouii/Grafana-ansible)** and  **[Prometheus role](https://github.com/sbouii/Prometheus-ansible)** .

## Supported systems

- centos 7
- ubuntu 16.04

## Usage 

the vagrantfile describes the configuration of the virtual machines to set up .

to use vagrantafile you have to do the following :

1. Download and Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. Download and Install [Vagrant](https://www.vagrantup.com/downloads.html)
3. Install [Ansible](http://docs.ansible.com/intro_installation.html) **version >= 2.3**.
4. Open a shell prompt and cd into the folder containing the `Vagrantfile`
5. Run the following command to install the necessary Ansible roles for this profile: `$ ansible-galaxy install -r requirements.yml`

then you can simply setup the server by typing `vagrant up`.
 
- **[Grafana Docker-host-containers Dasboard1](https://snapshot.raintank.io/dashboard/snapshot/5ehLoYGgNfEuI8f0FW0JoGm9cKlWNQ3h)**
- **[Grafana Docker-host-containers Dasboard2](https://snapshot.raintank.io/dashboard/snapshot/YSWFNGAsBRi2rYuO4ok1CCXbTG5mFyzk)**
