## How to Reproduce the Website Deployment

This document explains how to reproduce the deployment of this project from scratch.
The goal is to deploy a static website on a VPS using Docker, NGINX, and automatic
updates from GitHub.

---

## 1. Create a VPS

- Create a Virtual Private Server (VPS) with a public IP address
- Use Debian Linux
- Enable SSH access

---

## 2. Connect to the VPS

From your local machine, connect to the server using SSH:

```bash
ssh debian@<VPS_IP>



# All Commands in BASH
# -INSTALL THE PROJECT-
* Clone the repository
  *  git clone https://github.com/username/repository name.git
* Enter project folder
  * cd repository name
# -SET UP THE SERVER-
  * update the server
  * sudo apt update && sudo apt upgrade
# -INSTALL NGINX-
* Install
  * sudo apt install nginx
* move your website into NGINX
  *  sudo cp -r * /var/www/html/
# -DEPLOY WEBSITE-
* pull latest code
  * git pull
* NGINX restart
  * systemctl restart nginx
* After setting up the ssh keys and an action workflow any pushed updates will auto deploy the server


