# ELK-stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Leilani705/Cloud-Security-Diagram/blob/main/diagram_cloudsecurity.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK file may be used to install only certain pieces of it, such as Filebeat.

  -https://github.com/Leilani705/cybersecurity-assignments/blob/main/filebeat_playbook.yml
  -https://github.com/Leilani705/cybersecurity-assignments/blob/main/metricbeat_playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting traffic to the network.
-load balancers protect against DDoS attacks. The advantage of a jump box is a seperated security zone with controllability.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
filebeats watch for data about the file system. metric beats collect machine metrics, such as uptime.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |  10.0.0.1  | Linux            |
| ELK      |elk server|  10.1.0.4  | Linux            |   
| VM       |web server|  10.0.0.5  | Linux            |   
| VM       |web server|  10.0.0.7  | Linux            |   
| VM       |web server|  10.0.0.8  | Linux            |   
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 52.186.150.88:5601

Machines within the network can only be accessed by:
- Jump Box is the only machine that has access to my ELK VM. It's IP is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |          No         |   168.62.196.99      |
|   ELK    |          No         | 52.186.150.88:5601   |
|   VM     |          No         |       10.0.0.4       |
|   VM     |          No         |       10.0.0.4       |
|   VM     |          No         |       10.0.0.4       |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it automates multi-tier deployements, making it a common IT engine for automating tasks.

The playbook implements the following tasks:
- installs and launches filebeat/metricbeat onto the ELK server
- downloads and opens the filebeat/metricbeat
- enables and configures the system module
- sets up and starts the filebeat/metricbeat
- enables service filebeat/metricbeat on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![dockerps](https://user-images.githubusercontent.com/78867429/124840744-e5bde980-df48-11eb-8382-dbc696a7fe90.PNG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1: 10.0.0.8
- Web 2: 10.0.0.5
- Web 3: 10.0.0.7

We have installed the following Beats on these machines:
- filebeat and metricbeat on ELK Server, Web 1, Web 2, and Web 3

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to collect data about the filesystem. An example of this would be log events from all the servers.
- metricbeat allows us to collect machine metrics. An example of this would be uptime from the servers. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible/roles.
- Update the hosts file to include the elk server with the destination IP address
- Run the playbook, and navigate to kibana(http://52.224.124.194:5601/app/kibana#/home) to check that the installation worked as expected.

- the .yml files are the playbooks, these are copied to etc/ansible/roles.
- you update the hosts file to run the playbook on specific machines. To specify which machines to install the ELK sever on and which to install filebeats use groups.
-In order to check that the ELK server is running properly navigate to the kibana address. 

