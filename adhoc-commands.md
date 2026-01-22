Ad-hoc commands are one-line Ansible commands used to perform simple, quick tasks on managed nodes without writing a full playbook.  
  
They are commonly used for:
- Checking service status
- Installing packages
- Restarting services
- Gathering system facts
- Running shell commands  
  
Syntax:  
ansible <hosts> -m <module> -a "<arguments>"  
  
 1. Ping Managed Nodes (Connectivity Check)  
Used to verify SSH access.  
ansible all -i inventory.ini -m ping (for all nodes)  
For a particular node - mention its host name or group name
ansible web -i invetory.ini -m ping  
ansible GCP -i inventory.ini -m ping  
2. Gather Facts from Managed Nodes  
Facts include:  
- OS
- CPU
- Memory
- IP address
- Disk info
ansible all -i inventory.ini -m setup  
ansible web -i inventory.ini -m setup  
ansible GCP -i inventory.ini -m setup
3. Check service status(e.g. nginx)  
ansible all -i inventory.ini -m service -a "name=nginx state=started"  
ansible web -i inventory.ini -m service -a "name=nginx state=started"  
ansible GCP -i inventory.ini -m service -a "name=nginx state=started"  
4. Shell command  
ansible all -i inventory.ini -m shell -a "systemctl status nginx"  
ansible web -i inventory.ini -m shell -a "systemctl status nginx"  
ansible GCP -i inventory.ini -m shell -a "systemctl status nginx"  
5. Restart a service  
ansible all -i inventory.ini -m service -a "name=nginx state=restarted"  
ansible web -i inventory.ini -m service -a "name=nginx state=restarted"  
ansible GCP -i inventory.ini -m service -a "name=nginx state=restarted"  
6. Check Disk Usage  
ansible all -i inventory.ini -m shell -a "df -h"  
ansible web -i inventory.ini -m shell -a "df -h"  
ansible GCP -i inventory.ini -m shell -a "df -h"  
7. Check memory usage  
ansible all -i inventory.ini -m shell -a "free -m"  
ansible web -i inventory.ini -m shell -a "free -m"  
ansible GCP -i inventory.ini -m shell -a "free -m"
8. Check hostname  
ansible all -i inventory.ini -m command -a "hostname"  
ansible GCP -i inventory.ini -m command -a "hostname"  
9. Create a file on managed node  
ansible GCP -i inventory.ini -m file -a "path=/tmp/ansible_test.txt state=touch" --become  
10. Stop / Start Instances (Cloud Level)  
For cloud-level operations, use:
- AWS: EC2 module
- Azure: az CLI / Ansible Azure modules
- GCP: gcp_compute_instance module

Example (GCP – stop VM):  

ansible localhost -m google.cloud.gcp_compute_instance \
  -a "name=ansible-gcp zone=us-central1-c project=my-project-id state=stopped auth_kind=application"

