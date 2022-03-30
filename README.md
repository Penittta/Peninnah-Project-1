# Peninnah-Project-1
The Files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/102623533/160934598-5b96d76f-ac8b-4fe0-ad5d-41cb51909804.png)




These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk Deployment file may be used to install only certain pieces of it, such as Filebeat.

 -  [Myfirstplaybook.yml](https://github.com/Penittta/Peninnah-Project-1/blob/main/MyfirstPlaybook.yml)
 
-   [hosts](https://github.com/Penittta/Peninnah-Project-1/issues/1#issue-1186649033)

- [ansible.cfg]( https://ansible.com/)

- [install-elk](https://github.com/Penittta/Peninnah-Project-1/issues/3#issue-1186658505)

- [filebeat-config](https://github.com/Penittta/Peninnah-Project-1/issues/4#issue-1186672263)

- [Metricbeat-Config](https://github.com/Penittta/Peninnah-Project-1/issues/5#issue-1186677691)




This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional and available, in addition to restricting traffic to the network.

- What aspect of security do load balancers protect? 

They rerouteLive traffic from one server to another 

- What is the advantage of a jump box?

It is secured 

Ip Address that can communicate with the jumpbox under restrictions

- Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.

- What does Filebeat watch for?

Filebeat monitors log files, and forwards them to elastic search or logstash for indexing
-  What does Metricbeat record? 
 
 It collects statistics and matricss and ships them to the output specified 

The configuration details of each machine may be found below.


| Name | Function | Ip Address | Operating system |
|---|---|---|---|
| Jump-box | Gateway | 40.112.197.217 | linux(ubuntu 18.04) |
| web-1 | Dvwa | 10.0.0.10 | linux(ubuntu 20.04) |
| web-2 | Dvwa | 10.0.0.9 | linux(ubuntu 20.04 |
| Elk-server  | Elk | 10.1.0.5 | linux(ubuntu 20.04) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

- Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 
 My Home IP Address; Machines within the network can only be accessed by Jump-Box-Provisioner 

Machines within the network can only be accessed by Workstation and Jump-Box-Provisioner .

- Which machine did you allow to access your ELK VM?

Jump Box Provisioner 

- What was its IP address?

10.0.0.4

The Jump-Box-provitioner is able to connect via SSH to the Elk-Stack machine through port 22. In addition the Personal Host IP address is also able to access the Elk-Stack machine through port 5601

A summary of the access policies in place can be found in the table below.

| Name  | Publicly Accessible | Allowd Ip addresses |
|---|---|---|
| Jump Box | Yes | Public Ip, 10.0.0.4 |
| Load-Balancer | Yes | 52.225.72.41 |
| web-1 | No | 10.0.0.10 |
| web-2 | No | 10.0.0.9 |
| Elk-stack | yes/no |  Public IP, 10.1.0.5 |                     

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
- System installation and updates can be done efficiently.

- What is the main advantage of automating configuration with Ansible?

Ansible is very easy to set up and use, easy to read, no special coding skills are needed, and is open source.

The playbook implements the following tasks:

[install-elk](https://github.com/Penittta/Peninnah-Project-1/issues/3#issue-1186658505)

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

- name: set maximum map count in sysctl/systemd

- name: docker.io

- name: instal pip3

- name: Install Docker module

- name: download and launch elk


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/102623533/160903807-effa7b7e-afd4-4e33-9f44-0095194f2299.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-List the IP addresses of the machines you are monitoring: 

Web-1 10.0.0.10 , Web-2 10.0.0.9

- We have installed the following Beats on these machines:

 Filebeat , Metricbeat

- These Beats allow us to collect the following information from each machine:

Filebeat: Monitors log files and collects log events and then forwards them to Elasticsearch, or Logstash, or any other specified destination. The filebeat would look at the log events and send them to ELK-Stack VM.

Metricbeat: Takes the metrics and statistics collected and sends them out to programs such as Elasticsearch or Logstash, or any other specified destination. The metricbeat would look at the uptime of the system or the system logs.


### Using the Playbook
- In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

filebeat-playbook.yml playbook nano file - Once the file created, we need to run the command line (ansible-playbook filebeat-playbook.yml)

[filebeat-config](https://github.com/Penittta/Peninnah-Project-1/issues/4#issue-1186672263)

metricbeat-playbook.yml playbook nano file - Once the file created, we need to run the command line (ansible-playbook metricbeat-playbook.yml)

[Metricbeat-Config](https://github.com/Penittta/Peninnah-Project-1/issues/5#issue-1186677691)


SSH into the control node and follow the steps below:
-Copy the filebeat-config.yml file to /etc/ansible/files.
- Update the /etc/ansible /hosts file to include the ip address of the webserversand the elk-stack.
- Run the playbook, and navigate to: http://[your.BM.IP]:5601/app/kibana to check installation.




