1. CREATE A NEW VM FOR AWX  
Create one more EC2   
Ubuntu 22.04  
Security Group: Port 80, Port 22
2. Install prerequisites  
Install docker: sudo apt update   
sudo apt install -y docker.io docker-compose git  
sudo systemctl enable docker
sudo systemctl start docker  
docker --version  
docker-compose --version
3. Install AWX by cloning the AWX repo: git clone https://github.com/ansible/awx.git
cd awx  
cd tools/docker-compose  
docker-compose up -d  
docker ps
4. Access AWX UI  
In browser: ip_of_instance  
Login with username and password as 'admin'  
5. Configure AWX  
- Create Organization  
AWX UI → Organizations → Add  
Name: awx  
- Create Credential (SSH)  
AWX → Credentials → Add  
Type: Machine  
Username: ubuntu  
SSH Private Key: paste privatekey  
- Create Inventory  
AWX → Inventories → Add  
Name: multi-cloud-inventory  
Add Hosts:AWS VM IP, GCP VM IP  
- Create Project  
AWX → Projects → Add  
Source Control Type: Git  
Repo URL: Repo that has playbook  
Branch: main  
- Create Job Template  
AWX → Job Templates → Add  
Inventory: multi-cloud-inventory  
Project: repo  
Playbook:sample.yml  
Credential: SSH credential  
Launch job  
6. Verify  
If success, green job output, tasks run on managed nodes
