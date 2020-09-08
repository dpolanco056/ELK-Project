## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/dpolanco056/ELK-Project/blob/master/Diagram/Capture.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml. file may be used to install only certain pieces of it, such as Filebeat.



This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly exist, in addition to restricting permission to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_
avalibilities and restrictions in the network. jumpBox restricts IPs access. 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the JumpBox  and system logs.
- What does Filebeat watch for? manage the log files.
- What does Metricbeat record? monitor system and memory usage using elastic search.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| WEB1     |  DVWA    | 10.0.0.7   | Linux            |
| WEB2     |  DVWA    | 10.0.0.8   | Linux            |
| ELK-Project|        | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the host machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
73.251.65.118

Machines within the network can only be accessed by JumpBox.
- Which machine did you allow to access your ELK VM? JumpBox, Web1 and Web2 What was its IP address? 10.0.0.4,  10.0.0.5 and 10.0.0.6.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?

The playbook implements the following tasks:
-  name: install filebeat deb
   command: dpkg -i filebeat-7.4.0-amd64.deb
- 
- 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/dpolanco056/ELK-Project/blob/master/Diagram/Capture.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- JumpBox (10.0.0.4), Web1 (10.0.0.5) and Web2 (10.0.0.6). 

We have installed the following Beats on these machines:
- FileBeat and MetricBeat

These Beats allow us to collect the following information from each machine:
- FileBeat collect data from file system. MetricBeat collect machine metrics. ex: cpu usage, memory usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ssh keygen file to ssh public key.
- Update the security rules file to include the IP address.
- Run the playbook, and navigate to bash to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Which file is the playbook? FileBeat  Where do you copy it? All the webservers. 
- Which file do you update to make Ansible run the playbook on a specific machine? the Hosts conf. file. How do I specify which machine to install the ELK server on versus which to install Filebeat on? Update tasks hosts group, ELK or Webservers.  
- Which URL do you navigate to in order to check that the ELK server is running? http://[your.VM.IP]:5601/app/kibana

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.  ansible-playbook filebeat-playbook.yml
nano ansible.cfg to update user to: [remote user: sysadmin]
nano hosts to update webservers and Elk IPS EX: 
10.0.0.7 ansible_python_interpreter=/usr/bin/python3
10.0.0.8 ansible_python_interpreter=/usr/bin/python3
[elk]
10.1.0.4 ansible_python_interpreter=/usr/bin/python3

