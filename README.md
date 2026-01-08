# nginx-aws-ubuntu-setup

# NGINX Setup on AWS EC2 (Ubuntu)

This project demonstrates how to install, configure, and run **NGINX on an AWS EC2 Ubuntu instance**, including changing default ports and configuring AWS Security Groups.

---

##  Architecture
User → Internet → AWS Security Group → EC2 (Ubuntu) → NGINX

---

##  Technologies Used
- AWS EC2
- Ubuntu 20.04 / 22.04
- NGINX
- Linux
- AWS Security Groups

---

## Step-by-Step Setup

### Launch EC2 Instance
- AMI: Ubuntu
- Instance type: t2.micro
- Security Group:
  - SSH (22)
  - HTTP (80)
  - Custom TCP (3000 / 8080)

---

### Connect to EC2
```bash
ssh -i key.pem ubuntu@<public-ip>    ex: http://<public-ip>

<<<<<<ubuntu>>>>>
sudo apt update
sudo apt install nginx -y


sudo systemctl start nginx
sudo systemctl enable nginx

sudo systemctl status nginx  ---------> its show the Active



********************Change NGINX Port (Example: 3000)**************
 
sudo nano /etc/nginx/sites-available/default ------>   server {        change to 3000

                                                                        listen 8080 default_server;

                                                                          Listen [::]:8080 default_server;

                                                                        # SSL configuration

                                                            root /var/www/html;
                                                               }


sudo nginx -t (fix syntax)

Then REload

sudo systemctl reload nginx


incase of firewall blocking  use

sudo ufw status-------------->inactive

sudo ufw allow 3000


********************************Then reload**************

http://<EC2-PUBLIC-IP>:**3000**    


                   Welcome to nginx!
                   If you see this page, thration is required.

                    For online documentation and support please refer to nginx.org.
                    Commercial support is available at nginx.com.

                     Thank you for using Nginx.











