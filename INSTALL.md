## How to Reproduce the Project Deployment

This document explains how to set up and deploy the website from scratch.

---

## 1. Create a VPS

- Create a VPS with a public IP address
- Use Debian Linux
- Enable SSH access

---

## 2. Connect to the VPS

-ssh debian@<VPS_IP>



## 3. Update the System
- sudo apt update && sudo apt upgrade -y


## 4. Install Docker
- sudo apt install docker.io -y
- sudo systemctl start docker
- sudo systemctl enable docker

Check installation:
- docker --version


## 5. Create the NGINX Container
- sudo docker run -d -p 80:80 --name unix-container nginx
This runs an NGINX web server inside a Docker container and exposes it to the internet.


## 6. Clone the Repository on the VPS
- git clone https://github.com/username/repository-name.git

- cd repository-name


## 7. Copy Website Files into the Container
-sudo docker cp website/. unix-container:/usr/share/nginx/html/
-sudo docker restart unix-container
The website should now be accessible using the VPS IP address.


## 8. Enable SSH Password Authentication
GitHub Actions uses SSH with a password to connect to the VPS.
Edit the SSH config:
- sudo nano /etc/ssh/sshd_config
Set:
PasswordAuthentication yes

Restart SSH:
- sudo systemctl restart ssh


## 9. Configure GitHub Secrets
In the GitHub repository:
Settings → Secrets and variables → Actions → New repository secret

Add:
VPS_IP        = VPS public IP
VPS_PASSWORD = VPS user password


## 10. Add the GitHub Actions Workflow
Create the file:
- .github/workflows/deploy.yml
This workflow connects to the VPS, pulls the latest code, copies the website into the container, and restarts it.


## 11. Automatic Deployment
To deploy updates:
- git add .
- git commit -m "Update website"
- git push origin main
Any push to main automatically updates the live website.


