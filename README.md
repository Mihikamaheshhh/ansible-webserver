# 🚀 Automating Web Server & Website Hosting with Ansible

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3000&pause=1000&color=00C7FF&center=true&vCenter=true&width=750&lines=AWS+EC2+%7C+Ansible+%7C+Nginx;Automate+%7C+Deploy+%7C+Manage+%F0%9F%9A%80;Infrastructure+Automation+with+Ansible" alt="Typing SVG" />

<br><br>

<img src="https://img.shields.io/badge/AWS-EC2-orange?style=for-the-badge&logo=amazonaws&logoColor=white" />
<img src="https://img.shields.io/badge/Ansible-Automation-black?style=for-the-badge&logo=ansible&logoColor=white" />
<img src="https://img.shields.io/badge/Ubuntu-Linux-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" />
<img src="https://img.shields.io/badge/Nginx-Web_Server-009639?style=for-the-badge&logo=nginx&logoColor=white" />
<img src="https://img.shields.io/badge/SSH-Secure_Connection-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white" />
<img src="https://img.shields.io/badge/Git-GitHub-181717?style=for-the-badge&logo=github&logoColor=white" />
<img src="https://img.shields.io/badge/HTML-Website-E34F26?style=for-the-badge&logo=html5&logoColor=white" />

<br><br>

<img src="https://img.shields.io/badge/Infrastructure-Automation-blue?style=flat-square" />
<img src="https://img.shields.io/badge/Cloud-AWS-orange?style=flat-square" />
<img src="https://img.shields.io/badge/Web_Server-Nginx-green?style=flat-square" />
<img src="https://img.shields.io/badge/Configuration_Management-Ansible-red?style=flat-square" />

</div>

---

## 📌 Project Overview

This project demonstrates how to **automate the complete setup and deployment of a web server using Ansible on AWS EC2**.

Instead of manually connecting to an Ubuntu server and installing/configuring Nginx, Ansible performs the entire process automatically through **SSH**.

### 🔥 What this project does

```text
AWS EC2 Ubuntu
      │
      ▼
   SSH Connection
      │
      ▼
    Ansible
      │
      ├── 📦 Update Packages
      │
      ├── 🌐 Install Nginx
      │
      ├── ⚙️ Configure Nginx
      │
      ├── ▶️ Start Nginx
      │
      ├── 🔄 Enable Nginx
      │
      └── 📄 Deploy Website
              │
              ▼
        🚀 Website Live
```

---

# 🛠️ Tech Stack

<div align="center">

| Technology     | Purpose                               |
| -------------- | ------------------------------------- |
| ☁️ **AWS EC2** | Cloud server / virtual machine        |
| ⚙️ **Ansible** | Configuration management & automation |
| 🐧 **Ubuntu**  | Server operating system               |
| 🌐 **Nginx**   | Web server                            |
| 🔐 **SSH**     | Secure remote connection              |
| 📦 **Git**     | Version control                       |
| 🐙 **GitHub**  | Source code hosting                   |
| 🌎 **HTML**    | Website content                       |
| 🐧 **WSL**     | Local Linux environment               |

</div>

---

# 🏗️ Architecture

```text
                         👨‍💻 Developer
                              │
                              ▼
                    💻 Windows Laptop
                              │
                              ▼
                       🐧 WSL / Ubuntu
                              │
                              ▼
                     ⚙️ Ansible Controller
                              │
                              │ 🔐 SSH
                              ▼
                    ☁️ AWS EC2 Instance
                       Ubuntu Linux
                              │
                              ▼
                         🌐 Nginx
                              │
                              ▼
                     📄 HTML Website
                              │
                              ▼
                        🌍 Internet
```

---

# ⚙️ How Ansible Works

Ansible follows a simple **Controller → SSH → Managed Node** architecture.

```text
             ANSIBLE CONTROLLER
             🐧 WSL / Ubuntu
                    │
                    │ SSH
                    ▼
             ┌───────────────┐
             │   AWS EC2     │
             │    Ubuntu     │
             └───────────────┘
                    │
                    ▼
                 🌐 Nginx
                    │
                    ▼
               🚀 Website
```

### 🔹 Controller

The machine where Ansible is installed.

```text
Windows
   ↓
WSL
   ↓
Ubuntu
   ↓
Ansible
```

### 🔹 Managed Node

The AWS EC2 Ubuntu instance that Ansible manages.

---

# ⚡ Ansible Tasks

The playbook automatically performs the following tasks:

### 1️⃣ Update Packages

```bash
sudo apt update
```

### 2️⃣ Install Nginx

```bash
sudo apt install nginx
```

### 3️⃣ Start Nginx

```bash
sudo systemctl start nginx
```

### 4️⃣ Enable Nginx

```bash
sudo systemctl enable nginx
```

### 5️⃣ Deploy Website

The website is copied to:

```text
/var/www/html/
```

### 6️⃣ Verify Deployment

Open:

```text
http://YOUR_EC2_PUBLIC_IP
```

---

# 🔄 Automation Flow

```text
        🚀 START
           │
           ▼
    📦 Update Packages
           │
           ▼
     🌐 Install Nginx
           │
           ▼
   ⚙️ Configure Web Server
           │
           ▼
      ▶️ Start Nginx
           │
           ▼
     🔄 Enable Nginx
           │
           ▼
     📄 Deploy Website
           │
           ▼
    🔍 Verify Deployment
           │
           ▼
      🎉 WEBSITE LIVE
```

---

# 📂 Project Structure

```text
ansible-webserver/
│
├── 📄 inventory
├── 📄 playbook.yml
│
├── 📁 website/
│   └── 📄 index.html
│
├── 📄 .gitignore
└── 📄 README.md
```

---

# 📄 Inventory File

The inventory file contains the details of the AWS EC2 server.

Example:

```ini
[webservers]

webserver ansible_host=YOUR_EC2_PUBLIC_IP \
ansible_user=ubuntu \
ansible_ssh_private_key_file=./your-key.pem
```

> ⚠️ Replace `YOUR_EC2_PUBLIC_IP` with your EC2 public IP address.

---

# ⚙️ Ansible Playbook

Example `playbook.yml`:

```yaml
---
- name: Configure Nginx Web Server
  hosts: webservers
  become: yes

  tasks:

    - name: Update apt package cache
      apt:
        update_cache: yes
        cache_valid_time: 3600

    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Start and enable Nginx
      service:
        name: nginx
        state: started
        enabled: yes

    - name: Deploy website
      copy:
        src: ./website/index.html
        dest: /var/www/html/index.html
        mode: '0644'
```

---

# 🌐 Website

The website files are stored inside:

```text
website/
└── index.html
```

Ansible automatically copies the website to:

```text
/var/www/html/index.html
```

Nginx then serves the HTML file to visitors.

---

# 🚀 Installation & Setup

## 1️⃣ Launch AWS EC2

Create an **Ubuntu EC2 instance**.

Recommended configuration:

```text
AMI       → Ubuntu
Instance  → Any suitable free-tier instance
Storage   → Default
Key Pair  → Create / use existing key pair
```

---

## 2️⃣ Configure Security Group

Allow the following inbound traffic:

| Type  | Port | Purpose                  |
| ----- | ---: | ------------------------ |
| SSH   |   22 | Ansible / SSH connection |
| HTTP  |   80 | Website                  |
| HTTPS |  443 | Future SSL support       |

Example:

```text
Inbound Rules

SSH
TCP
22
Your IP

HTTP
TCP
80
0.0.0.0/0
```

> 🔐 For better security, restrict SSH access to your own IP whenever possible.

---

# 🐧 3️⃣ Install Ansible

Inside WSL Ubuntu:

```bash
sudo apt update
```

Then:

```bash
sudo apt install ansible -y
```

Verify:

```bash
ansible --version
```

Expected:

```text
ansible [core ...]
```

---

# 🔐 4️⃣ Configure SSH Key

Move your EC2 private key into your working directory or configure an appropriate secure path.

Example:

```bash
chmod 400 your-key.pem
```

Test the connection:

```bash
ssh -i your-key.pem ubuntu@YOUR_EC2_PUBLIC_IP
```

If the connection works, Ansible can use the same SSH credentials.

---

# 🧪 5️⃣ Test EC2 Connection

Run:

```bash
ansible -i inventory webservers -m ping
```

Expected result:

```text
webserver | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

🎉 Your Ansible controller can now communicate with the EC2 server!

---

# 🚀 6️⃣ Run the Ansible Playbook

Execute:

```bash
ansible-playbook -i inventory playbook.yml
```

Ansible will automatically:

```text
✅ Connect to EC2
✅ Update packages
✅ Install Nginx
✅ Start Nginx
✅ Enable Nginx
✅ Deploy website
```

---

# 🌍 7️⃣ Access the Website

After the playbook finishes, open:

```text
http://YOUR_EC2_PUBLIC_IP
```

Example:

```text
http://3.XX.XX.XX
```

🎉 **Your website is now live on AWS EC2!**

---

# 🔍 Verify Nginx

SSH into your EC2 instance:

```bash
ssh -i your-key.pem ubuntu@YOUR_EC2_PUBLIC_IP
```

Check Nginx:

```bash
sudo systemctl status nginx
```

Expected:

```text
Active: active (running)
```

---

# 📊 Useful Ansible Commands

### Check Ansible Version

```bash
ansible --version
```

### Test Connectivity

```bash
ansible -i inventory webservers -m ping
```

### Run Playbook

```bash
ansible-playbook -i inventory playbook.yml
```

### Check Inventory

```bash
ansible-inventory -i inventory --list
```

### Check Managed Hosts

```bash
ansible -i inventory webservers --list-hosts
```

### Run Ad-Hoc Command

```bash
ansible -i inventory webservers -m shell -a "uptime"
```

### Check Nginx Status

```bash
ansible -i inventory webservers -m shell -a "systemctl status nginx"
```

---

# 🔐 Security

Security is an important part of this project.

### 🚫 Never commit private keys

Add the following to `.gitignore`:

```gitignore
*.pem
*.key
*.retry
__pycache__/
.env
```

### ⚠️ Never upload:

```text
❌ AWS private keys
❌ Passwords
❌ API keys
❌ Access tokens
❌ AWS credentials
```

### 🔒 SSH Best Practices

```text
✔ Restrict SSH to your IP
✔ Use SSH keys
✔ Never expose private keys
✔ Rotate compromised credentials
✔ Avoid hardcoding secrets
```

---

# 🆚 Manual Configuration vs Ansible

## ❌ Manual Configuration

```text
Login to EC2
     ↓
Update Packages
     ↓
Install Nginx
     ↓
Configure Nginx
     ↓
Start Nginx
     ↓
Copy Website
     ↓
Verify Website
```

This becomes repetitive when managing multiple servers.

---

# ✅ Ansible Automation

```text
        playbook.yml
             │
             ▼
          Ansible
             │
             ▼
        🔐 SSH
             │
             ▼
       ☁️ EC2 Server
             │
             ▼
      🚀 Everything Done
```

### Benefits

| Manual                 | Ansible                  |
| ---------------------- | ------------------------ |
| ❌ Time consuming       | ✅ Fast                   |
| ❌ Repetitive           | ✅ Automated              |
| ❌ Error prone          | ✅ Consistent             |
| ❌ Difficult to scale   | ✅ Easy to scale          |
| ❌ Manual configuration | ✅ Infrastructure as Code |

---

# 💡 Why Ansible?

Ansible provides:

### ⚡ Automation

Automates repetitive server configuration.

### 🔁 Repeatability

The same playbook can be executed repeatedly.

### 📈 Scalability

One playbook can manage multiple servers.

### 🎯 Consistency

Servers can be configured using the same desired state.

### 🔐 Secure Communication

Uses SSH for Linux server management.

### 📖 Easy to Understand

YAML-based playbooks are relatively human-readable.

---

# 🧠 Key Concepts Demonstrated

This project demonstrates practical knowledge of:

```text
☁️ AWS EC2
🐧 Linux
🔐 SSH
⚙️ Ansible
📦 Package Management
🌐 Nginx
📄 Web Deployment
📝 YAML
🔧 Configuration Management
📂 File Management
🚀 Infrastructure Automation
🐙 Git & GitHub
```

---

# 🎯 Project Objectives

The primary objectives are:

```text
🔧 Server Configuration
        +
🌐 Web Server Deployment
        +
⚙️ Infrastructure Automation
        +
☁️ AWS Cloud
        +
🔐 SSH Configuration
        +
🚀 Ansible
        =
💻 Automated Web Hosting
```

---

# 📈 Real-World Use Case

Imagine you have:

```text
        1 Server
           │
        Ansible
           │
      Easy to manage
```

Now imagine:

```text
        10 Servers
           │
        Ansible
           │
      Easy to manage
```

And:

```text
        100 Servers
           │
        Ansible
           │
      Automated Management
```

This is where configuration management becomes extremely valuable.

---

# 🔮 Future Improvements

This project can be extended into a complete DevOps pipeline.

### 🔄 CI/CD

Integrate:

```text
Jenkins
GitHub Actions
AWS CodePipeline
```

### 🐳 Containerization

Add:

```text
Docker
Docker Compose
```

### ☸️ Orchestration

Move toward:

```text
Kubernetes
AWS EKS
```

### 🏗️ Infrastructure as Code

Add:

```text
Terraform
AWS CloudFormation
```

### 📊 Monitoring

Implement:

```text
Prometheus
Grafana
CloudWatch
```

### 🔒 Security

Add:

```text
HTTPS
SSL/TLS
Let's Encrypt
AWS WAF
IAM best practices
```

### ☁️ High Availability

Add:

```text
AWS Load Balancer
Auto Scaling
Multiple EC2 Instances
Route 53
```

---

# 🚀 Future Architecture

```text
                         👨‍💻 Developer
                              │
                              ▼
                         🐙 GitHub
                              │
                              ▼
                       🔄 CI/CD Pipeline
                              │
                              ▼
                         🏗️ Terraform
                              │
                              ▼
                         ☁️ AWS Cloud
                              │
              ┌───────────────┴───────────────┐
              ▼                               ▼
          EC2 Instance 1                 EC2 Instance 2
              │                               │
              └───────────────┬───────────────┘
                              ▼
                           ⚙️ Ansible
                              │
                              ▼
                           🌐 Nginx
                              │
                              ▼
                       ⚖️ Load Balancer
                              │
                              ▼
                           🌍 Users
                              │
                              ▼
                    📊 Prometheus + Grafana
```

---

# 📸 Project Screenshots

Add your project screenshots here:

```markdown
## 📸 Screenshots

### AWS EC2

![AWS EC2](screenshots/ec2.png)

### Ansible Ping

![Ansible Ping](screenshots/ansible-ping.png)

### Ansible Playbook

![Ansible Playbook](screenshots/playbook.png)

### Website

![Website](screenshots/website.png)
```

Recommended folder:

```text
screenshots/
├── ec2.png
├── ansible-ping.png
├── playbook.png
└── website.png
```

---

# 🏆 Project Highlights

<div align="center">

### 🚀 Infrastructure Automation

### ☁️ AWS Cloud Deployment

### ⚙️ Configuration Management

### 🌐 Automated Web Hosting

### 🔐 SSH-Based Server Management

### 🐧 Linux Administration

### 📦 Nginx Deployment

### 🐙 GitHub Version Control

</div>

---

# 📚 What I Learned

Through this project, I gained practical experience with:

```text
✅ AWS EC2
✅ Ubuntu Server
✅ Linux Commands
✅ SSH Authentication
✅ Ansible Inventory
✅ Ansible Modules
✅ Ansible Playbooks
✅ YAML
✅ Nginx
✅ Web Server Configuration
✅ Automated Deployment
✅ Git & GitHub
```

---

# 💼 Resume Value

This project demonstrates hands-on experience in:

> **Cloud Computing + Linux + Configuration Management + Infrastructure Automation + Web Server Deployment**

### Resume Project Description

```text
Automated Nginx web server provisioning and website deployment
on AWS EC2 using Ansible. Configured SSH-based remote management,
automated package installation, service management, and website
deployment through reusable Ansible playbooks.
```

---

# 🏷️ Topics

```text
#AWS
#AWSCloud
#EC2
#Ansible
#DevOps
#CloudComputing
#Linux
#Ubuntu
#Nginx
#Automation
#InfrastructureAsCode
#ConfigurationManagement
#WebServer
#SSH
#Git
#GitHub
#CI_CD
#CloudEngineer
#DevOpsEngineer
```

---

# ⭐ Give This Project a Star

If you found this project useful or interesting:

<div align="center">

### ⭐ Star the repository

### 🍴 Fork the repository

### 📢 Share it with other DevOps learners

</div>

---

# 👨‍💻 Author

<div align="center">

## 🚀 Mihika Maheshhh

**Cloud | DevOps | AWS | Ansible**

<br>

<img src="https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazonaws" />
<img src="https://img.shields.io/badge/DevOps-Automation-blue?style=for-the-badge" />
<img src="https://img.shields.io/badge/Ansible-Infrastructure-black?style=for-the-badge&logo=ansible" />
<img src="https://img.shields.io/badge/Linux-Ubuntu-E95420?style=for-the-badge&logo=ubuntu" />

<br><br>

### 🚀 Automate • Deploy • Manage • Scale

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer" width="100%" />

</div>
