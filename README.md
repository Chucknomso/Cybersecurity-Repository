## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!Diagram/Network_Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - Elk-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized_ to the network.
- Load balancers protect the networks from DDoS attacks. A jumpbox provides a central point to administer webservers in a security group.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the security and system logs.
- Filebeats is a log shipper that offers a lightweight way to forward and cnetralize logs and files_
- Metricbeats collects and ships host metrics  to the ELK stack

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     |Webserver | 10.0.0.5   | Linux            |
| Web2     |Webserver | 10.0.0.7   | Linux            |
| Elk      |Webserver | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Whitelisted: 99.245.82.173_

Machines within the network can only be accessed by jump box.
- The jumpbox has access to the ELK server, the IP address is 10.0.0.4_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 99.245.82.173        |
|  Web1    | No                  | 10.0.0.4             |
|  Web 2   | No                  | 10.0.0.4             |
|  Elk VM  | No                  | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible streamlines and simplifies cloud provisioning process, it automates infrastructure creation and configuraton management. It saves the time taken to configure multiple VMs and reduces bugs and errors.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Configures the target VM.
- Installs Docker and pip packages.
- Configures the container with port mappings.
- Start the container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 and 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects and ships log files to the ELK server, it is the logging agent that collects log events and sends for indexing.
- Metricbeat collects and ships host metrics, it is installed on servers to monitor the performance example CPU, memory and load.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-playbook file to /etc/ansible/install-elk.yml.
- Update the host file to include the IP address of the ELK server
- Run the playbook, and navigate to138.91.127.199:5601 (the public IP of the Elk server) to check that the installation worked as expected.


to run the playbook:
$ ansible ansible-playbook install-elk.yml
