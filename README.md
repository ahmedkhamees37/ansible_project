# 🚀 Deploy WordPress with Ansible Roles (Apache, PHP, MariaDB)

## 📌 Overview
This project automates the deployment of **WordPress** using **Ansible** with three separate roles:
- **Apache** (Handles the web server)
- **PHP** (Processes WordPress code)
- **MariaDB** (Manages the WordPress database)

The playbook is designed to work on **Ubuntu**, **CentOS**, and supports deployment on **on-premises** and **AWS EC2 instances**. 🌟

![Screenshot 2025-04-02 140624](https://github.com/user-attachments/assets/947f5fb1-bc51-427b-a4ac-e424de7956a0)


---

## 📂 Project Structure
```bash
wordpress-deployment/
│── ansible.cfg
│── inventory.ini
│── playbook.yml
│── roles/
│   ├── apache/
│   │   ├── tasks/main.yml
│   │   ├── handlers/main.yml
│   │   └── templates/apache.conf.j2
│   ├── php/
│   │   └── tasks/main.yml
│   └── mariadb/
│       ├── tasks/main.yml
│       └── handlers/main.yml
│── group_vars/
│── host_vars/
```

---

## ⚙️ Prerequisites

Before running the playbook, ensure you have:
- **Ansible installed** (`sudo apt install ansible` or `sudo yum install ansible`)
- **SSH access to target servers**
- **AWS Key Pair** (if deploying on AWS)
- **Correct security group settings** (for AWS, ensure ports 22, 80, 443, and 3306 are open)

---

## 🏢 Supported Environments
- **On-Premises:** Supports local VM-based or bare-metal servers running Ubuntu or CentOS.
- **AWS EC2:** Automatically detects AWS instances and configures settings accordingly.

---

## 👩‍💻 Installation Guide

### 1️⃣ Clone the repository
```bash
git clone https://github.com/ahmedkhamees37/wordpress-ansible.git
cd wordpress-ansible
```

### 2️⃣ Edit the inventory file (`inventory.ini`)
Modify the file to include your target servers:
```ini
[webserver]
192.168.1.10 ansible_user=root ansible_os_family=Ubuntu

[dbserver]
192.168.1.20 ansible_user=root ansible_os_family=RedHat

[aws_instances]
10.5.10.8 ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/aws-key.pem ansible_os_family=RedHat
```

### 3️⃣ Run the playbook
```bash
ansible-playbook -i inventory.ini playbook.yml
```

---

## 🖥️ Roles Overview

### 📌 Apache Role (`roles/apache/`)
- Installs Apache (`apache2` for Ubuntu, `httpd` for CentOS)
- Deploys a custom VirtualHost configuration
- Starts and enables the service
- Configures firewall settings for web traffic

### 📌 PHP Role (`roles/php/`)
- Installs PHP and required extensions
- Ensures compatibility with WordPress

### 📌 MariaDB Role (`roles/mariadb/`)
- Installs MariaDB server
- Creates a WordPress database and user
- Configures security settings
- Ensures **on-premises** and **AWS EC2** compatibility

---

## 🌟 AWS Deployment Considerations
- Ensure your **AWS security group** allows:
  - **Port 22** (SSH)
  - **Port 80 & 443** (HTTP & HTTPS)
  - **Port 3306** (MariaDB - if connecting remotely)
- Use the correct **EC2 key pair** to connect via SSH.

---

## 💡 Next Steps
- Automate WordPress installation 📚
- Enhance security settings 🔒
- Implement SSL support with Let's Encrypt 🔑
- Optimize performance for AWS scaling 🚀

---

## 📃 License
This project is licensed under the **MIT License**.

---

## 🌍 Connect
👉 [LinkedIn](https://linkedin.com/in/ahmed-khamis37)

# ansible_project
# ansible_project
# ansible_project
# ansible_project
