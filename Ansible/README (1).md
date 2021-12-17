## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  

Diagrams/VirtualNetwork.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ___playbook.YML__ file may be used to install only certain pieces of it, such as Filebeat.

 Ansible

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load Balancers help protect against denial of service attacks (DDoS) the load balancer watches the incoming internet traffic then sends it the appropriate servier.  If it isn't, the load balancer will divert traffic from the malfunctioning server until the issue is resolved. A jump box limits the access that the public has to your virtual network because in order to access the other virtual machines, an individual needs the private IPs of the machines. A jumpbox allows greater control over access to a virtual network and its contents.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the operating system and system services.
Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.3.0.4   | Linux            |
| Web1     | DVWA     | 10.3.0.6   | Linux            |
| Web2     | DVWA     | 10.3.0.5   | Linux            |
| Elkvm    | Elkserver| 10.0.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
20.124.104.37

Machines within the network can only be accessed by SSH.
The JumpBox was allowed access to the elkVM.  Its IP address is 10.3.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 20.124.104.37        |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because servcies running can be confined, system installation and update can be accomplished faster, quicker, and with more accuracy.
The main advantage of automationg configuration with ansible is that it allows IT departments and companies to automate the process of configuring a virtual network.  This gives the IT people and business more time to focus on other issues.

The playbook implements the following tasks:
•	Install Docker.
•	Create & Attach an Ansible container.
•	Create Filebeat on Web Vm's.
•	Create Filebeat configuration.YML file.
•	Create Filebeat installation playbook.
•	Create Metricbeat on Web Vm's.
•	Create Metricbeat configuration.YML file.
•	Create Metricbeat installation playbook.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  


![image](https://user-images.githubusercontent.com/89751905/146589475-454c5154-4a91-46c6-9937-220e9bcc3c6d.png)


### Target Machines & Beats
10.3.0.5
10.3.0.6

We have installed the following Beats on these machines:
Filebeats, Metricbeats

These Beats allow us to collect the following information from each machine:
Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing
Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible playbood file to /etc/ansible/
- Update the filebeat.yml file
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
filebeat-playbook.yml /etc/ansible/filebeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? The hosts file How do I specify which machine to install the ELK server on versus which to install Filebeat on? By choosing the correct host group
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
