---
title: "🖥️ Hosting WordPress on AWS EC2"
date: 2025-06-19
tags: ["AWS", "EC2", "WordPress"]
cover:
  image: "/images/aws/ec2-wordpress.png"
  alt: "Hosting WordPress on EC2"
draft: false
---

This project documents how I hosted a WordPress blog on an AWS EC2 instance using the free tier. I manually set up Apache, PHP, MariaDB, and WordPress on an Amazon Linux 2023 instance.

✅ Tools Used
- AWS EC2 (Amazon Linux 2023)
- PuTTY (SSH client)
- WordPress
- Apache, PHP, MariaDB

---

🔧 **1. Launch EC2 Instance**
- Chose Amazon Linux 2023
- Instance type: t2.micro
- Set key pair (used later for SSH)
- Placed EC2 in a public subnet with auto-assigned public IP
- Security group rules:
    -Allow SSH (port 22) from your IP
    -Allow HTTP (port 80) from anywhere

---

🔑 **2. SSH into EC2 Instance**
Using PuTTY:

```bash
ssh -i your-key.pem ec2-user@your-ec2-public-ip
```

---

🧱 **3. Install Apache, PHP, and Required Extensions**

```bash
sudo dnf install httpd php php-mysqlnd php-fpm php-json php-mbstring -y

sudo systemctl start httpd
sudo systemctl enable httpd
```

---

🐬 **4. Install MariaDB (Manual Install)**

```bash
sudo dnf install mariadb105-server -y
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

---

🔐 **5. Secure MariaDB & Create DB for WordPress**

```bash
sudo mysql_secure_installation

# Then login
sudo mysql -u root -p

# Create WordPress DB and user
CREATE DATABASE wordpress;
CREATE USER 'brianblog'@'localhost' IDENTIFIED BY 'StrongPass123!';
GRANT ALL PRIVILEGES ON wordpress.* TO 'brianblog'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

---

🌐 **6. Install WordPress**

```bash
cd /var/www/html
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xzf latest.tar.gz
sudo cp -r wordpress/* .
sudo rm -rf wordpress latest.tar.gz
sudo chown -R apache:apache /var/www/html
sudo chmod -R 755 /var/www/html
```

---

📝 **7. Configure wp-config.php**
```bash
sudo cp wp-config-sample.php wp-config.php
sudo nano wp-config.php
```

Update the following:
```bash
define( 'DB_NAME', 'wordpress' );
define( 'DB_USER', 'brianblog' );
define( 'DB_PASSWORD', 'StrongPass123!' );
define( 'DB_HOST', 'localhost' );
```

---

🧪 **8. Test in Browser**
Visit:

http://your-ec2-public-ip

![Browser Test](/images/aws/aws-ec2.png)

---

📌 Notes
Ensure your EC2 instance is in a public subnet and has a public IP.
Make sure HTTP port (80) is open in your security group.