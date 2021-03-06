# Cyber_Security-Project-1
Project 1
Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

-Diagram 
![](Project%201%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

As the above YAML file show the details require more than just the aid of a playbook it also requires directions given withing the hosts file to direct certain tasks to each VM in this case but in a real environment will do the same thing.

-This document contains the following details: Description of the Topology

- Access Policies

- ELK Configuration

 - Beats in Use

 - Machines Being Monitored

- How to Use the Ansible Build

## Description of the Topology


-The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

-What aspect of security do load balancers protect?
- Load balancers protect the Availability leg of the triad ensuring that the weight of the traffic is not overloaded causing servers to be overwhelmed all at once.

-What is the advantage of a jump box?
- A jump server or Jump box is a hardened and monitored device that spans two dissimilar security zones and provides a controlled means of access between them.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jumpbox and system network.

-What does Filebeat watch for? 
- Forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

-What does Metricbeat record? periodically collect metrics from the operating system and from services running on the server
The configuration details of each machine may be found below.


|  Name       |    Function  |  IP Address  |  Operating System  |
| :---------- | :-----------:| :----------: | :----------------: |
|  Jump-Box   | Gateway      | 10.0.0.8     | Linux
|  Web-1      | Web Server   | 10.0.0.9     | Linux
|  Web-2      | Web Server   | 10.0.0.10    | Linux
|  Web-3      | Web Server   | 10.0.0.12    | Linux
|  Blue-ELK-1 | Log Analyzer | 10.1.0.4     | Linux

## Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: The IP that i have whitelisted is my personal public IP.

Machines within the network can only be accessed by the Jump Box.

-Which machine did you allow to access your ELK VM? 
- Jump Box/Ansible Container
- PrivateIP: 10.0.0.8
- PublicIP: 40.71.27.37

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible  | Allowed IP Addresses |
| :--------- | :------------------: | :------------------: | 
| Jump Box   |  Yes                 |     Personal IP      | 
| ELK        |  Yes                 |    10.0.0.0/16       |
| ELK        | Kibana-:5601-Yes     |    52.188.172.71     |
| Blood_Load | HTTP-80-Yes          |    52.188.172.71     |
| Web-2      |  No                  |    52.188.172.71     |
| Web-3      |  No                  |    52.188.172.71     |

## Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is useful because it provides a way to complete multiple tasks and changes to any number of machines using 1 command(within a playbook) this makes setting up a larger network extremely easy reducing the amount of time taken per machine.


-What is the main advantage of automating configuration with Ansible? 
- This allows multiple changes to multiple machines at once making

The playbook implements the following tasks:

-In the ELK install i used a playbook or YAML file with multiple commands that did the following.
- Installed docker.io which is the software used to house the container
- Installed python3-pip a package management system written in python used it install and manage software packages.
- Increase the virtual memory providing a high level of resource to the systemm helping to carry our multiple process simultaneously. 
- Download and launch the ELK container
- Give permissions for the ports that ELK requires to run
- Enable the service docker on boot

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

![](Docker%20ps.png)

## Target Machines & Beats

This ELK server is configured to monitor the following machines: 

| Web-1 | Web Server | 10.0.0.9  | Linux   |
| ----- | ---------- | :-------: | ------: |
| Web-2 | Web Server | 10.0.0.10 | Linux   |
| Web-3 | Web Server | 10.0.0.12 | Linux   |

We have installed the following Beats on these machines:

-Specify which Beats you successfully installed:
- I have successfully installed and ran both filebeats and metricbeats on all 3 VM's.

These Beats allow us to collect the following information from each machine:
- Filebeat will collects and monitors all log files or specific locations that are specified.
- Metricbeats will periodically collect metrics from the operating system and from services running on the server.

## Using the Playbook:

In order to use the playbook, you will need to have an Ansible control node already configured, assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

-Answer:

- Copy the elk_install.yml file to /etc/ansible/roles/install-elk.yml
- Update the hosts file to include (IP ansible_python_interpreter=/usr/bin/python3
- Run the playbook, and navigate to http://[your_elk_server_ip]:5601/app/kibana to check that the installation worked as expected.



How do I specify which machine to install the ELK server on versus which to install Filebeat on? The ELK server would be installed on the VM and filebeat would be the added software within the ELK Stack.

To access the ELK server goto  http://[yourip.ELK-VM.External.IP]:5601/app/kibana
- If you are successful with all the tasks above and goto your browser you should see the following:

![](Kibana.png)


 
