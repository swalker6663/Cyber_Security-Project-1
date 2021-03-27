# Cyber_Security-Project-1
Project 1
Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

-Diagram 
![](Project%201%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

As the above YAML file show the details require more than just the aid of a playbook it also requires directions given withing the hosts file to direct certain tasks to each VM in this case but in a real environment will do the same thing.

-This document contains the following details: Description of the Topology

#Access Policies
-ELK Configuration
-Beats in Use
-Machines Being Monitored
-How to Use the Ansible Build
-Description of the Topology
-The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

-What aspect of security do load balancers protect?
Load balancers protect the Availability leg of the triad ensuring that the weight of the traffic is not overloaded causing servers to be overwhelmed all at once.

-What is the advantage of a jump box?
A jump server or Jump box is a hardened and monitored device that spans two dissimilar security zones and provides a controlled means of access between them.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jumpbox and system network.

What does Filebeat watch for? Forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
What does Metricbeat record? periodically collect metrics from the operating system and from services running on the server
The configuration details of each machine may be found below.




| Name       |    Function  |  IP Address  |  Operating System  |
|----------- | :-----------:| ------------ | -----------------: |
| Jump-Box   | Gateway      | 10.0.0.8     | Linux
| Web-1      | Web Server   | 10.0.0.9     | Linux
| Web-2      | Web Server   | 10.0.0.10    | Linux
| Web-3      | Web Server   | 10.0.0.12    | Linux
| Blue-ELK-1 | Log Analyzer | 10.1.0.4     | Linux

##Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: The IP that i have whitelisted is my personal public IP.

Machines within the network can only be accessed by _____.

Which machine did you allow to access your ELK VM? What was its IP address?_
A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible  | Allowed IP Addresses |
| ---------- | :------------------: | -------------------: | 
| Jump Box   |  Yes/No              |     Personal IP      | 
| ELK        |  No                  |                      |
| Web-1      |  No                  |                      |

## Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

What is the main advantage of automating configuration with Ansible? This allows multiple changes to multiple machines at once making
The playbook implements the following tasks:

TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
...
...
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

TODO: Update the path with the name of your screenshot of docker ps output

## Target Machines & Beats

This ELK server is configured to monitor the following machines: 

| Web-1 | Web Server | 10.0.0.9  |Linux 
| Web-2 | Web Server | 10.0.0.10 |Linux 
| Web-3 | Web Server | 10.0.0.12 |Linux

We have installed the following Beats on these machines:

Specify which Beats you successfully installed:
I have successfully installed and ran both filebeats and metricbeats on all 3 VM's.

These Beats allow us to collect the following information from each machine:

In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., Winlogbeat collects Windows logs, which we use to track user logon events, etc.
Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured, assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the _____ file to _____.
Update the _____ file to include...
Run the playbook, and navigate to ____ to check that the installation worked as expected.
-Answer the following questions to fill in the blanks:_

Which file is the playbook? Where do you copy it?
Which file do you update to make Ansible run the playbook on a specific machine? In order to add another machine so Ansible can run the playbook you will need to change the hosts file located in the /etc/ansible/ dir.

How do I specify which machine to install the ELK server on versus which to install Filebeat on? The ELK server would be installed on the VM and filebeat would be the added software within the ELK Stack.

To access the ELK server goto  http://[your.ELK-VM.External.IP]:5601/app/kibana

As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.
Once inside the Ansible container you will navigatew to the directory that contains the playbook once there use the command.
ansible-playbook (the .yml file to be used) and hit enter this command will run and could take some time so be patient.
