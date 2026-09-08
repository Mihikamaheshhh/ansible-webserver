<div align="center">

# 🚀 Automating Web Server & Website Hosting with Ansible

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3000&pause=1000&color=00C7FF&center=true&vCenter=true&width=700&lines=AWS+EC2+%7C+Ansible+%7C+Nginx;Automate+%7C+Deploy+%7C+Manage+%F0%9F%9A%80;Infrastructure+Automation+with+Ansible" />

<br>

<img src="https://img.shields.io/badge/AWS-EC2-orange?style=for-the-badge&logo=amazonaws" />
<img src="https://img.shields.io/badge/Ansible-Automation-black?style=for-the-badge&logo=ansible" />
<img src="https://img.shields.io/badge/Ubuntu-Linux-E95420?style=for-the-badge&logo=ubuntu" />
<img src="https://img.shields.io/badge/Nginx-Web%20Server-009639?style=for-the-badge&logo=nginx" />
<img src="https://img.shields.io/badge/Git-GitHub-181717?style=for-the-badge&logo=github" />

</div>

---

## 📌 Project Overview

This project automates the setup and configuration of an **Nginx web server on an AWS EC2 Ubuntu instance using Ansible**.

Ansible connects to the EC2 server through SSH and automatically installs Nginx, starts the service, and deploys a website.

---

## 🛠️ Technologies Used

- ☁️ AWS EC2
- 🐧 Ubuntu
- ⚙️ Ansible
- 🌐 Nginx
- 🔐 SSH
- 📦 Git & GitHub
- 🌎 HTML

---

## 🏗️ Architecture

```text
                 💻 Windows Laptop
                        │
                        ▼
                  🐧 WSL / Ubuntu
                        │
                        ▼
                   ⚙️ Ansible
                        │
                     🔐 SSH
                        │
                        ▼
                ☁️ AWS EC2 Ubuntu
                        │
                        ▼
                   🌐 Nginx
                        │
                        ▼
                   🚀 Website
⚙️ Ansible Tasks

The Ansible playbook automatically performs:

📦 Updates Ubuntu packages
🌐 Installs Nginx
▶️ Starts and enables Nginx
📄 Deploys the website to /var/www/html/
🔄 Automation Flow
📦 Update Packages
        ↓
🌐 Install Nginx
        ↓
⚙️ Configure Web Server
        ↓
▶️ Start Nginx
        ↓
📄 Deploy Website
        ↓
🚀 Website Live
📂 Project Structure
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
🚀 How to Run
1️⃣ Test EC2 Connection
ansible -i inventory webservers -m ping

Expected result:

webserver | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
2️⃣ Run the Ansible Playbook
ansible-playbook -i inventory playbook.yml

Ansible will automatically:

✅ Update packages
✅ Install Nginx
✅ Start Nginx
✅ Enable Nginx
✅ Deploy website
3️⃣ Access the Website

Open the EC2 public IP in your browser:

http://YOUR_EC2_PUBLIC_IP

🎉 Your website is now live!

🔐 Security

Private SSH keys are excluded from GitHub using .gitignore.

*.pem
*.key
*.retry
__pycache__/

⚠️ Never upload your AWS private key (.pem) to GitHub.

🎯 Objective

The goal of this project is to demonstrate:

🔧 Server configuration
🌐 Web server deployment
⚙️ Infrastructure automation
☁️ AWS EC2 management
🔐 SSH-based remote configuration
🚀 Ansible automation
💡 Why Ansible?
❌ Manual Configuration
Login to Server
      ↓
Update Packages
      ↓
Install Nginx
      ↓
Configure Server
      ↓
Deploy Website
✅ Ansible Automation
ansible-playbook
       ↓
    🚀 DONE

Ansible makes the deployment faster, repeatable, and consistent.

🔮 Future Improvements
🔄 Jenkins CI/CD
🐳 Docker
☸️ Kubernetes / AWS EKS
🏗️ Terraform
📊 Prometheus & Grafana
🔒 HTTPS / SSL
☁️ AWS Load Balancer
<div align="center">
🚀 Automate • Deploy • Scale
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer"/>
👩‍💻 Author

Mihika Maheshhh

</div> ```
