Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/gambit198/HW13-Github/blob/main/Diagrams/ELKnetwork.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the pentest.yml (ansible playbook) file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/gambit198/HW13-Github/blob/main/Ansible/filebeatscript.txt

Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
 Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.
 
What aspect of security do load balancers protect? What is the advantage of a jump box?
Load balancers help protect the availability of the server. And a jumpbox is a secure computer that all admins first connect to before launching any administrative task or use and an organization point to connect to other servers or untrustworthy environments.
 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system data.
 
What does Filebeat watch for? 
Filebeat monitors the log files or locations that you specify.
 
What does Metricbeat record? 
Metricbeat collects metrics from the system and services running on the server.
 
The configuration details of each machine may be found below.

 
| Name          | Function          | IP Address      | Operating System |
|---------------|-------------------|-----------------|------------------|
| Jump Box      | Gateway           | 10.0.0.8        | Linux            |
| Web1          |    VM             | 10.0.0.9        | Linux            |
| Web2          |    VM             | 10.0.0.10       | Linux            |
| Web3          |    VM             | 10.0.0.11       | Linux            |
 
Access Policies
The machines on the internal network are not exposed to the public Internet.
 
Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 
Add whitelisted IP addresses:  host Ip addess
 
Machines within the network can only be accessed by jumpbox.

Which machine did you allow to access your ELK VM? What was its IP address? 
Jumpbox 168.61.66.131
 
A summary of the access policies in place can be found in the table below.
 
| Name       | Publicly Accessible | Allowed IP Addresses               |
|------------|---------------------|------------------------------------|
| Jump Box   | No                  | host machine IP address            |
|  ELK       |  Yes                | jumpbox, http port 80, port 5601   |


Elk Configuration
 
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

What is the main advantage of automating configuration with Ansible? 
Every function such as starting, updating and installing are done automatically.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.

After the VM was created for the ELK server it was added to the ansible hosts file 
Will create a new ansible-playbook to configure our new ELK VM
the playbook will install docker.io, python3-pip, and docker.
When docker is installed, it will download and run the sebp/elk:761 container.
After the ELK container is installed, SSH to your container and double-check that your elk-docker container is running.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://drive.google.com/file/d/1OdQj5V-TdK4lnHno4qtz46Uqp96oJ65T/view?usp=sharing
  
Target Machines & Beats

This ELK server is configured to monitor the following machines:

List the IP addresses of the machines you are monitoring
-10.0.0.9
-10.0.0.10
-10.0.0.11 

We have installed the following Beats on these machines:
-Filebeat
-Metricbeat
 
These Beats allow us to collect the following information from each machine:
-Filebeat will monitor the log files or locations that are specified
-Metricbeat will collect metrics from the system and services running on the server.


Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
 
SSH into the control node and follow the steps below:
- Copy the ansible configuration file to the container.
- Update the hosts file to include the 3 vm’s ip addresses.


Run the playbook, and navigate to kibana to check that the installation worked as expected.
 http://(your.vm.ip):5601/app/kibana
 
As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
-Ansible-playbook /etc/ansible/pentest.yml

