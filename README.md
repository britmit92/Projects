## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagrams/Elk-Diagram 2.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the `YAML` file may be used to install only certain pieces of it, such as Filebeat.

  - [elk.yml](Ansible/elk.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly `redundant`, in addition to restricting `traffic` to the network.
- _What aspect of security do load balancers protect? What is the advantage of a jump box?_
  - The aspect of security that load balancers protect is availability. The advantage of the jumpbox is to reduce the amount of attack vectors because only the jumpbox can SSH into the webservers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the `configurations` and system `files`.
- _What does Filebeat watch for?_
  - Filebeat monitors for SSH logins, sudo commands, and account Linux logins.
- _TODO: What does Metricbeat record?_
  - Metricbeat monitors for CPU, RAM, and network usage.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    |          |        10.0.0.7    |     Linux             |
| Web-2    |          |   10.0.0.5        |       Linux           |
| Elk    | Monitoring Solution         |  10.1.0.5          |      Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the `Jumpbox` machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 - My personal IP

Machines within the network can only be accessed by `ansible container`.
- _Which machine did you allow to access your ELK VM? What was its IP address?_
  - Jumpbox (Ansible container) - 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes          | My Personal IP   |
|  Web-1        |    Yes                 |    40.87.53.9                  |
|   Web-2       |      Yes               |        40.87.53.9              |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _What is the main advantage of automating configuration with Ansible?_
  - The main advantage of automating configuration with Ansible is that it is prone to less security misconfigurations, less human errors, and faster deployment.

The playbook implements the following tasks:
- Install docker.io

- Install Python-pip
- Install docker container
- Install docker container:elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 
-Web-1 10.0.0.7, Web-2 10.0.0.5, and Web-3 10.0.0.8


We have installed the following Beats on these machines:
- Metricbeat and Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files or locations you specify, collects log events, and forward them to Elasticsearch or Logstash for indexing.
- Metricbeat is collects the metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the configuration file to include the webservers and elk-vm
- Run the playbook, and navigate to elk-vm to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? /etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? Edit /etc/ansible/hosts file to add webserver and elk ip addresses.

 How do I specify which machine to install the ELK server on versus which to install Filebeat on? Ensuring you are in the correct directory.
 
- Navigate to http://[your ELk vm external IP]:5601/app/kibana this will confirm if ELK and kibana is running.
