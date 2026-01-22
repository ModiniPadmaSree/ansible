Creating Ansible Inventory Files for AWS, GCP, and Azure  
  
Ansible inventory files:  
An Ansible inventory file defines:  
- The managed nodes (hosts)
- Groups of hosts
- Connection details such as SSH user and private key  
Ansible uses the inventory file to know where and how to connect.  
  
Choose the Inventory File Format  
Ansible supports multiple formats - ini, yaml  
The INI format is used because it is simple and commonly used.  
  
Define Common Inventory Parameters  
Each host entry may include:
- `ansible_host` – Public IP or DNS of the VM
- `ansible_user` – Operating system user for SSH
- `ansible_ssh_private_key_file` – Private key on the control node  
  
Create an Inventory Group for AWS  
Define a group named aws and add EC2 instances to it.  
[aws]  
aws_vm1 ansible_host=13.218.172.216 ansible_user=ubuntu ansible_ssh_private_key_file=/home/ubuntu/padmasree.pem  
  
Create an Inventory Group for GCP  
Define a group named gcp and add Google Compute Engine instances.  
[gcp]  
gcp_vm1 ansible_host=34.171.87.214 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/gcp_key  
  
Create an Inventory Group for azure  
Define a group named azure and add Azure instances.  
[azure]  
azure_vm1 ansible_host=<ip> ansible_user=azureuser ansible_ssh_private_key_file=~/.ssh/azure_key  
  
Combine All Cloud Groups  
Create a parent group to manage all cloud instances together.  
[all:children]  
aws  
gcp  
azure  
  
Verify Inventory Usage  
Use an Ansible ad-hoc command to test connectivity.  
ansible all -i inventory.ini -m ping  
