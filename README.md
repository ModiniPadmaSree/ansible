Document to run the playbook  
Prerequisites:  
1. Ansible installed on control node.
2. Target machine reachable via SSH.
3. Inventory file is configured.  
  
Sample ini file  
[web]
ec2-server ansible_host=<EC2_PUBLIC_IP> ansible_user=ubuntu ansible_ssh_private_key_file=~/mykey.pem  
  
Run the playbook  
ansible-playbook -i inventory.ini simple-playbook.yml  
  
This playbook:
-- Updates the system package index  
-- Installs the Nginx package  
-- Starts the Nginx service  
-- Enables Nginx to start automatically on system boot
  
Verification  
1. Verify the status of NGINX: systemctl status nginx
2. Access thorugh browser: <ip_of_instance>
