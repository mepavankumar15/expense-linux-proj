
# frontend

basic format of project declaration

---

- Installing the program RUNTIME
- creating a directory and system user
- Download and unzip the code
- Install dependencies
- Create Systemctl service
- Run DB scripts if required
- Start Application

---

### NGINX

===========

NGINX is a high-performance, open-source web server used primarily **to handle high-traffic websites through reverse proxying, load balancing, and caching**. It acts as an intermediary,

Key Uses :

- HTTPS/HTTP WEBSERVER
- Reverse Proxying
- Load Balancing
- Caching
- Security and Firewall

configs -> /etc/nginx
HTML -> /usr/share/nginx/html
logs -> /var/log/nginx
default page -> /usr/share/nginx/html/index.html

This is a static content and to serve static content we need a web server. This server

Developer has chosen Nginx as a web server and thus we will install Nginx Web Server.

Install Nginx

```
dnf install nginx -y
```

Enable nginx

```
systemctl enable nginx
```

Start nginx

```
systemctl start nginx
```

**Try to access the service once over the browser and ensure you get some default content**

Remove the default content that web server is serving.

```
rm -rf /usr/share/nginx/html/*
```

Download the frontend content

```
curl -o /tmp/frontend.zip https://expense-joindevops.s3.us-east-1.amazonaws.com/expense-frontend-v2.zip
```

Extract the frontend content.

```
cd /usr/share/nginx/html
```

```
unzip /tmp/frontend.zip
```

# Forward Proxy

1. hiding client identity
2. sits in between client and server
3. client aware
4. VPN, content filtering, traffic monitoring
5. Can be used as caching also.

# Reverse Proxy

1. Hiding server identity
2. Server Aware
3. Security reasons and queue management
4. Load balancing
5. used for SSL/TLS/HTTPS termination

**Try to access the nginx service once more over the browser and ensure you get expense content.**

Create Nginx Reverse Proxy Configuration.

```
vim /etc/nginx/default.d/expense.conf
```

here to create a reverse proxy configuration → we need to make changes in 

/etc/nginx/default.d/<username>.conf

```bash
vim /etc/nginx/default.d/<username>.conf
```

include /etc/nginx/conf.d/*.conf;
include /etc/nginx/default.d/*.conf;

/etc/sudoers.d/

Now after configuration → restart the service 

```bash
systemctl restart nginx
```
