All Commands in BASH
-INSTALL THE PROJECT-
Clone the repository
--> git clone https://github.com/username/repository name.git
Enter project folder
--> cd repository name
-SET UP THE SERVER-
update the server
--> sudo apt update && sudo apt upgrade
install NGINX
--> sudo apt install nginx
move your website into NGINX
--> sudo cp -r * /var/www/html/
-DEPLOY WEBSITE-   --manual deployment
pull latest code
--> git pull
NGINX restart
--> systemctl restart nginx
--After setting up the ssh keys and an action workflow any pushed updates will auto deploy the server


