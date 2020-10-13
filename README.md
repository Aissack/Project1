# Project1
Elk Stack Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the *yml* file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: *filebeat-playbook.yml*

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly *balanced*, in addition to restricting *heavy load* to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the *traffic* and system *performance*.
- _TODO: What does Filebeat watch for?_
Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

- _TODO: What does Metricbeat record?_
Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server. It takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     |          | 10.0.0.5   |                  |
| Web2     |          | 10.0.0.6   |                  |
| Web3     |          | 10.0.0.7   |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the *jumpbox* machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: *97.88.34.79*

Machines within the network can only be accessed by *jumpbox*.
- _TODO: Which machine did you allow to access your ELK VM? *jumpbox*
What was its IP address? *10.0.0.4*

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              |    97.88.34.79       |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? *streamlines and simplifies cloud provisioning*

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
  --- PLAY [installing and launching filebeat]
  --- TASK [Gathering Facts]
  --- TASK [download filebeat deb]
  --- TASK [install filebeat deb]
  --- TASK [drop in filebeat.yml]
  --- TASK [enable and configure system module]
  --- TASK [setup filebeat]
  --- TASK [start filebeat service]


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png) 

*http://52.249.190.16:5601/app/kibana#/home/tutorial/systemLogs*

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
      *10.0.0.5*
      *10.0.0.6*
      *10.0.0.7*
      *10.1.0.4*
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ *filebeat* (*metricbeat; optional)

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
  - Filebeat; is used to collecting and shipping log files.
	- Packetbeat; captures network traffic between severs used in applications and performance monitoring.
	- Metricbeat; supports internal modules for collecting statistics from specific platforms.
	- Winlogbeat; analyzes security events and updates installed.
	- Functionbeat; Monitors cloud environments by collecting and shipping data into the elk stack.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the *filebeat-config* file to *webvm's*.
- Update the Configuration file to include; * username*, *password* and *host IP*.
- Run the playbook, and navigate to *filebeat installtion page to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? *filebeat-playbook.yml*
    Where do you copy it? */etc/ansible*
- _Which file do you update to make Ansible run the playbook on a specific machine?  *filebeat-configuration.yml*
  How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- _Which URL do you navigate to in order to check that the ELK server is running? *10.1.0.4*

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc. *ansible-playbook filebeat-playbook.yml* or *curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/files/filebeat-config.yml*
