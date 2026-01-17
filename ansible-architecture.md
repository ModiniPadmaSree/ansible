Understanding Ansible Architecture and Concepts  
  Ansible is an open-source automation tool used for configuration management, application deployment, orchestration, and cloud infrastructure automation. It is agentless, simple to use, and relies on SSH (or WinRM for Windows) to manage systems, making it lightweight and efficient.  
  
Ansible Architecture  
Ansible follows a simple, push-based architecture consisting of the following core components:  
Control Node - The control node is the machine where Ansible is installed and executed.
1. Runs Ansible CLI commands (ansible, ansible-playbook).
2. Contains playbooks, roles, inventories, and configuration files
3. Pushes configurations to managed nodes using SSH
4. Can be a developer’s laptop, a CI/CD server (e.g., Jenkins), or a dedicated automation server  
  
Managed Nodes - Managed nodes are the target systems that Ansible manages.
1. Can be physical servers, virtual machines, cloud instances, containers, or network devices
2. Do not require Ansible to be install.
3. Require SSH access (Linux/Unix)
4. Python installed (usually pre-installed)
5. Receive instructions from the control node  
  
Inventory - An inventory defines the list of managed nodes that Ansible controls.  
Types of inventories:
1. Static Inventory – A simple text or YAML file with host details
2. Dynamic Inventory – Automatically fetches hosts from cloud providers like AWS, Azure, or GCP  
  
Features:  
1. Grouping hosts (e.g., web servers, database servers)
2. Assigning variables to hosts or groups
3. Managing environments such as dev, staging, and production  
  
Modules - Modules are reusable units of code that perform specific tasks on managed nodes.
1. Modules are executed on managed nodes
2. They are idempotent (safe to run multiple times)
3. Ansible includes hundreds of built-in modules
4. Custom modules can also be written
5. Examples of tasks - install packages, start or stop services, create users, provision cloud resources.  
  
Playbook - A playbook is a YAML file that defines a series of tasks to be executed on managed nodes.
1. Hosts to target
2. Tasks to execute
3. Modules to use
4. Variables and conditionals  
  
Role of Ansible in Automating Cloud Infrastructure  
  
Ansible plays a crucial role in cloud infrastructure automation by enabling Infrastructure as Code (IaC) and configuration management.
1. Infrastructure provisioning: Ansible can provision cloud resources such as virtual machines, load balancers, security groups, etc.
2. Configuration Management: Once resources are provisioned, ansible install software, configure services, applies security settings.
3. Application Deployment: Ansible automates application installations, environment variable configuration, dependency managements, rolling deployments and updates.
4. Orchestration: Ansible orchestrate complex workflows like multi-tier app deployment, DB setup before app deployment, zero-downtime deployment.
5. Cloud Environment Management: Ansible automatically detects new instances, manage auto-scaling environment, handles multiple environments (dev, test, prod)

Example: Automating Cloud Infrastructure Using Ansible (AWS)  
  
An organization wants to deploy a web application on AWS in an automated and repeatable way.  
Create an EC2 instance  
Install Nginx  
Deploy a web application  
Ensure the service runs automatically  
1. Provision Infrastructure - Ansible uses AWS modules to create an EC2 instance, security group, and key pair.
2. Configure the Server - Ansible installs Nginx on the EC2 instance.
3. Deploy the Application - Application files are copied to the server, environment variables are set, nginx is configured to serve the application.
4. Orchestration - Nginx is started after installation completed and the app is deployed once the server is ready.
