## 🔄 LAMP to LEMP Migration 



---

## 📌 Project Overview
This project demonstrates how to migrate a running web application from a LAMP stack (Linux, Apache2, Mariadb,Php) to a LEMP stack (Linux, Nginx, Mariadb, Php) on an Ubuntu server, focusing on better performance and efficient resource usage


---

## 🧩what is Lamp Stack?
- L – Apache2 (Operating System) 
- A – Apache (Web Server)  
- M – MySQL (Database)  
- P – PHP (Server-side Scripting Language)


   ![App Screenshot](https://miro.medium.com/v2/resize:fit:750/format:webp/1*T9DiM25OtweGgNiKTPTvQw.png)
## ⚡Deployment Lamp on Ubuntu

 1. EC2 Instance launch in (Ubuntu)
 Security group:
- SSH → 22
- HTTP → 80 

  <img width="1000" height="500" alt="Screenshot 2025-12-24 184954" src="https://github.com/user-attachments/assets/2ab8c6e3-2d7f-4d67-ad5e-8d8be7def4d0" />
 

2.  Install, Start and enable all services:

```bash
  sudo apt update

```
```bash
  sudo apt install apache2 -y
  sudo systemctl start apache2.service 
  sudo systemctl enable apache2.service

```
```bash
  sudo apt install mariadb-server -y
  sudo systemctl status mariadb.service 

```
```bash
  sudo apt install php php8.3-fpm -y
  sudo systemctl status php8.3-fpm.service 

```
3. Test Lamp Stack 
 Place index1.html in /var/www/html/:
```bash
  cd /var/www/html
  sudo nano index1.html

```
4. Open browser → You should see PHP info page.
```bash
  http://your_server_ip/index1.html

```

# 🔄 Lamp to Lemp Conversion

## 🧩what is Lemp Stack?
- Linux (Amazon Linux)
- Nginx (Web Server)
- MariaDB (Database)
- PHP / PHP-FPM

## ♻️Update Ubuntu Server

1. Before making any changes, update your server and install nginx packages:
```bash
  sudo systemctl stop apache2.service

```
```bash
  sudo apt install nginx -y
  sudo systemctl status nginx.service
  sudo systemctl enable nginx.service

```
2. Configure file Nginx changes:

```bash
  cd /etc/nginx/sites-enable/
  sudo nano default

```


    server{
    listen 80;
    server_name localhost;

    root /var/www/html;
    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
--- 
 ```bash
  sudo systemctl reload nginx.service
  sudo systemctl restart nginx.service

```
3. Open in browser → You should see PHP info page
 ```bash
  http://your_server_ip/index1.html

```

## ▶️How to Run the project
  1. Clone the Repository
 
 ```bash
  git clone <your-repo-url>

```
2. Navigate into Project Folder
 
 ```bash
   cd Repository-name

```
3. Move Project file to web directory
 ```bash
   sudo mv * /var/www/html/

```
4. Run the Html File
 ```bash
   sudo nano /var/www/html/file-name

```

# 📤Output
<img width="1000" height="500" alt="Screenshot 2025-12-24 184915" src="https://github.com/user-attachments/assets/347c5e62-6e9e-491b-9608-87357199a689"/>





## 🎯 Key Learning Outcomes 

- Understood the difference between LAMP and LEMP
- Migrated from Apache to Nginx
- Configured Nginx with PHP-FPM
- Performed MySQL database migration
- Improved server performance and scalability


## 🚀Conclusion 
- The LAMP to LEMP migration was successfully completed on an Ubuntu server.
- Switching to Nginx improved performance, reduced resource usage, and enhanced scalability.
- This project strengthened hands-on skills in Linux administration and modern web deployment.
  
## 👩🏻‍💻Author
   Sakshi Gond
  
 
