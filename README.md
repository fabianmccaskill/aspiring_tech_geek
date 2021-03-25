# aspiring_tech_geek
portfolio repository
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/fabianmccaskill/aspiring_tech_geek/blob/95e508606db9f10a81a797f68697edb6c6620e2e/Images/network_digram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/install-elk.yml
  - /etc/ansible/filebeat-playbook.yml
  - /etc/ansible/ansible.cfg
  - /etc/ansible/hosts
  - /etc/ansible/my_playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _accessible_, in addition to restricting _public access_ to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _logs_ and system _services_.

The configuration details of each machine may be found below.

| Name     | Function | IP Address   | Operating System |
|----------|----------|--------------|------------------|
| Jump Box | Gateway  | 20.191.65.85 | Linux            |
| Web-1    | DVWA     | 10.0.0.9     | Linux            |
| Web-2    | DVWA     | 10.0.0.8     | Linux            |
| Elk-2    | Elk      | 10.1.0.7     | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _JumpBox_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 184.96.60.57

Machines within the network can only be accessed by _JumpBox_.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses   |
|----------|---------------------|------------------------|
| Jump Box | yes                 | 184.96.60.57           |
| Web-1    | no                  | 10.0.0.10              |
| Web-2    | no                  | 10.0.0.10              |
| Elk-2    | yes                 | 184.96.60.57 10.0.0.10 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- it can simultaneously be run on multple systems with a given command, which can save a lot of time especially when configuring larger networks.

The playbook implements the following tasks:

- On the designated host, install docker.io, pythone-pip, and the docker module.
- Increase virtual memory to 262144.
- Download image: sebp/elk:761 and set it to always restart
- Enable docker service on boot.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/fabianmccaskill/aspiring_tech_geek/blob/f348bdbe38a09a07c08480d2189ab56c035d43e5/Images/docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.9 10.0.0.8

We have installed the following Beats on these machines:
- filebeats

These Beats allow us to collect the following information from each machine:

- Log events. For example, use the path /var/log/*.log to harvest all files in the /var/log/ directory that end with .log.
 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _install-elk.yml_ file to _/etc/ansible/_.
- Update the _hosts_ file to include: [elk]
                                      elk vm private IP address
- Run the playbook, and navigate to _http://your-Elk-VM-IP:5601/app/kibana#/home_ to check that the installation worked as expected.
