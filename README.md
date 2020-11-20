## Automated ELK Stack Deployment

*The files in this repository were used to configure the network depicted below.*

**_[XCorp's Red Team Network Diagram]_**(Images/diagram_filename.png)

The following files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the following files that may be used to install only certain pieces of it, such as Filebeat.

All the files below are located under /etc/ansible.

**_[Hosts]_

**_[Ansible.cfg]_

**_[Pentest.yml]_

**_[Install_elk.yml]_

**[Filebeat.yml]_
***[Filebeat-config.yml]

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


####Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly *available*, in addition to restricting *traffic* to the network.

  ***What aspect of security do load balancers protect?
  
  Load balancers protects the availability of data by re-routing network traffic to other available servers if one becomes unavailable due to attacks such as DDoS  

  ***What is the advantage of a jump box?
  
  A jumb box is can either be a physical or virtual device which is highly secured and only used for administrative task, such as "remoting" into production servers, running of   scripts/mass software updates across, other automations, etc.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the *network data* and system *logs*.

  ***What does Filebeat watch for? 
  
  Filebeat collects data from specific file system from specific locations and forwards them to Elasticsearch or Logstash.

   ***What does Metricbeat record?
   
   Metricbeat records machine metrics and statistics.

###The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function     | IP Address                      | Operating System |
|----------------------|--------------|---------------------------------|------------------|
| Jump-Box-Provisioner |Gateway       |INT: 10.0.0.4 EXT:52.187.249.137 | Linux            |
| Web-1                |Web Server    | 10.0.0.5                        | Linux            |
| Web-2                |Web Server    | 10.0.0.6                        | Linux            |
| ELKServer            |ELK Server    |INT:10.1.0.4 EXT:23.48.74.29     | Linux            |
| RedTeamLB            |Load Balancer |EXT:13.75.254.37                 | Linux            |


The machines on the internal network are not exposed to the public Internet. 

Only the **Jump-Box-Provisioner** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
**52.187.249.137**

Machines within the network can only be accessed by **Jump-Box-Provisioner**.

_Which machine did you allow to access your ELK VM? What was its IP address?_

**Jump-Box-Provisioner via internal network IP 10.0.0.4**

A summary of the access policies in place can be found in the table below.

| Name                   | Publicly Accessible  | Allowed IP Addresses                  |
|------------------------|----------------------|---------------------------------------|
| Jump-Box-Provisioner   |      Yes             | Workstation Public IP via SSH port 22 |
| Web-1                  |      No              | 10.0.0.4 on SSH  22                   |
| Web-2                  |      No              | 10.0.0.4 on SSH  22                   |
| ELKServer              |      No              | Workstation Public IP on  HTTP 80     | 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- **_What is the main advantage of automating configuration with Ansible?_**
- _Ansible ensures the same configuration (typically in the form of text files written in YAML) is run across one to many servers within minutes._

The playbook implements the following tasks:
- **_In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._**
- ...Modify /etc/ansible/hosts file to include the ELK server name, IP address and the python interpreter.  
- ...Install Docker and associated python module
- ...Use Command and sysctl Module to increase virtual memory and ensure it is mapped to a max value
- ...Download image (sebp/elk:761) and launch a docker elk container.  

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
