<div align="center">

# 🚀 Automating Web Server & Website Hosting with Ansible

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&duration=3000&pause=1000&center=true&vCenter=true&width=600&lines=AWS+EC2+%7C+Ansible+%7C+Nginx;Automate+%7C+Deploy+%7C+Manage+%F0%9F%9A%80" />

![AWS](https://img.shields.io/badge/AWS-EC2-orange?style=for-the-badge&logo=amazonaws)
![Ansible](https://img.shields.io/badge/Ansible-Automation-black?style=for-the-badge&logo=ansible)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Linux-E95420?style=for-the-badge&logo=ubuntu)
![Nginx](https://img.shields.io/badge/Nginx-Web_Server-009639?style=for-the-badge&logo=nginx)

</div>

---

## 📌 About The Project

This project automates the setup of an **Nginx web server on an AWS EC2 Ubuntu instance** using Ansible.

Instead of manually configuring the server, Ansible automatically installs Nginx, starts the service, and deploys the website.

### 🏗️ Architecture

```text
💻 Windows + WSL
       │
       │ Ansible + SSH 🔐
       ▼
☁️ AWS EC2 Ubuntu
       │
       ▼
🌐 Nginx
       │
       ▼
🚀 Website

⚙️ Ansible Tasks

The Ansible playbook:

Updates Ubuntu packages
Installs Nginx
Starts and enables Nginx
Deploys the website to /var/www/html/
📂 Project Structure
ansible-webserver/
├── inventory
├── playbook.yml
├── website/
│   └── index.html
├── .gitignore
└── README.md
🚀 How to Run
Test EC2 connection
ansible -i inventory webservers -m ping
Run the playbook
ansible-playbook -i inventory playbook.yml
Access the website

Open:

http://YOUR_EC2_PUBLIC_IP
🔐 Security

Private SSH keys are excluded from GitHub using .gitignore.

*.pem
*.key

Never upload your AWS private key to GitHub.

🎯 Objective

The goal of this project is to demonstrate server configuration, web server deployment, and infrastructure automation using Ansible and AWS.
