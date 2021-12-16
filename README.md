# Elk-Stack-Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![RedTeam Diagram](https://user-images.githubusercontent.com/90080030/146150661-25b64bf6-1ed5-4b00-b533-75015af9a051.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the my_playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

["Filebeat Playbook"](https://github.com/janetna40/ELK-STACK-Project1/blob/0899bacb55d415564623d63b5ea4448d1daa149a/Ansible/filebeat-playbook.yml)




This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting incoming traffic to the network.
Load balancers protect the availability of the servers and it will switch loads. Jumpbox isolates points of entry to the network, only ssh can be used on the allowed public IP address. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system files.
Filebeat is good for monitoring and collecting log files from Virtual Machines.
Metricbeat records the usage of a computer.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |40.71.174.86 & 10.0.0.4 | Linux  |
| Web01    | Webserver| 10.0.0.11  | Linux            |
| Web02    | Webserver| 10.0.0.10  | Linux            |
| Elk      |Monitoring| 40.83.17.254 & 10.1.0.5|Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-my public IP

Machines within the network can only be accessed by Jumpbox. With my private IP  


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 40.71.174.86         |
| Web01    | No                  | 10.0.0.11            |
| Web02    | no                  | 10.0.0.10            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The configuration is much quicker than when done manually. Ansible can be run by the command line and its preferred to install and configure through here because it minimizes potential errors. Ansible enables automation.

The playbook implements the following tasks:

-Install docker.io
-Install python3-pip
-Install docker python pip module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/90080030/146299699-ee0adcab-e2cd-4179-bd0f-42097f70a5f5.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-Web01 10.0.0.11
-Web02 10.0.0.10

We have installed the following Beats on these machines:
-Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat helps generate and organize log files to send to Logstash and Elasticsearch. It logs information about the file system, including which files have changed and when.(ex: it keeps track of sudo commands,ssh logins and new users/groups on yur vm's.)

-Metricbeat monitors the health of your Virtual Machines. It also collects metrics from the operating system CPU usage and active services runned by the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat Configuration file to /etc/ansible/files.
- Update the configuration file to include the private IP of the Elk-Server.
- Run the playbook, and navigate to "http://[Elk-serverPublicIP]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? 
filebeat-playbook.yml
- Where do you copy it?
/etc/ansible/files/filebeat-config.yml
- _Which file do you update to make Ansible run the playbook on a specific machine?
nano filebeat-confi.yml
-   How do I specify which machine to install the ELK server on versus which to install Filebeat on?
  filebeat-config.yml
- _Which URL do you navigate to in order to check that the ELK server is running?
http://40.83.17.254:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
