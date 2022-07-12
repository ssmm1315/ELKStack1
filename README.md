# ELKStack1
Project in Azure making an Virtual network and elk stack server
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://drive.google.com/file/d/1LFtFGs2Ta1-KuVcsAYbfz2WW0jFT1h9F/view?usp=sharing)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/ssmm1315/ELKStack1/tree/master/Ansible%20Playbooks

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
- What aspect of security do load balancers protect? They protect from DDoS attacks by managing traffic over multiple servers 
- What is the advantage of a jump box? This gives you more security over the network since there is only one to harden and manage for the whole network

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system health.
- What does Filebeat watch for?_monitors log files on servers that you install it on and collects log events
- What does Metricbeat record?_takes the statistics and puts them into Elasticsearch to help you monitor the servers

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     | VM       | 10.0.0.5   | Linux            |
| Web2     | VM       | 10.0.0.6   | Linux            |
| Web3     | VM       | 10.0.0.7   | Linux            |
| Elk      | VM       | 10.2.0.4   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 24.22.17.244

Machines within the network can only be accessed by JumpBox.
- Which machine did you allow to access your ELK VM? JumpboxProvisioner    
- What was its IP address?52.149.156.214

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     Yes             | 24.22.17.244         |
| Web1     |     No              | 10.0.0.4             |
| Web2     |     No              | 10.0.0.4             |
| Web3     |     No              | 10.0.0.4             |
| Elk      |     No              | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_it allows you to install on many servers at once

The playbook implements the following tasks:
- Installs Docker
- Installs Docker module
- Checks for memory
- Downloads and launches ELK Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![https://github.com/ssmm1315/ELKStack1/blob/master/ELK%20Server.png](Images/docker_ps_output.png)

![image](https://user-images.githubusercontent.com/63370629/89094822-f64f0280-d37c-11ea-807b-fbe313a4849e.png)









### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 Web1
- 10.0.0.6 Web2
- 10.0.0.7 Web3

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats
These Beats allow us to collect the following information from each machine:
- _Filebeats collect the log files from the servers it shows changes to the log files 
 - Metricbeat collects statistics from the servers  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible file to /etc/ansible.
- Update the hosts file to include the group the private ip address and the path 
- Run the playbook, and navigate to VM to check that the installation worked as expected.

_ Answer the following questions to fill in the blanks:_
- Which file is the playbook?  https://github.com/ssmm1315/ELKStack1/tree/master/Ansible%20Playbooks      
- Where do you copy it? nano a new file with the playbook's name in the /etc/ansible DIR and copy playbook into the new file, save file
- Which file do you update to make Ansible run the playbook on a specific machine? Hosts file 
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? Using groups in the host file example [webservers] [elk] could be created then list the IP addresses of the VM's in the groups.
- Which URL do you navigate to in order to check that the ELK server is running? https://52.151.56.200:5201/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- To run the playbook use this command while in the /etc/ansible folder- ansible-playbook pentest.yml
