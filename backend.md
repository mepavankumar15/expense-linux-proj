
# Backend

to know the several versions of a package → we use dnf module

Now check the several versions of nodejs

```bash
dnf module list nodejs
```

to disable a module → 

```bash
dnf module disable nodejs -y
```

to enable a module → 

```bash
dnf module enable nodejs:<version> -y
```

then install the nodejs → 

```bash
dnf install nodejs -y
```

Update openssl packages too not break SSH login

```bash
dnf update -y openssh openssh-server openssh-clients
```

Now add the Application user

```bash
useradd expense
```

User expense is a function / daemon user to run the application. Apart from that we don't use this user to login to server.

Also, username expense has been picked because it more suits to our project name.

We keep application in one standard location. This is a usual practice that runs in the organization.

let’s setup an app directory 

```bash
mkdir /app
```

Download the application code to created app directory.

```bash
curl -o /tmp/backend.zip https://expense-joindevops.s3.us-east-1.amazonaws.com/expense-backend-v2.zip
```

/tmp → OS stores unimportant temporary files 

go to app/ → 

```bash
cd /app
```

```bash
unzip /tmp/backend.zip
```

to install standard dependencies and libraries →

```bash
npm install
```

.service → / etc / systemd / system , here the services are stored

to start custom service → 

```bash
use -> vim /etc/systemd/system/<expense>.service
```

Setup SystemD Expense Backend Service

```bash
vim /etc/systemd/system/backend.service
```

add this description → 

```bash
[Unit]
Description = Backend Service

[Service]
User=expense
Environment=DB_HOST="<MYSQL-SERVER-IPADDRESS>" #private IP
ExecStart=/bin/node /app/index.js
SyslogIdentifier=backend

[Install]
WantedBy=multi-user.target
```

remember to reload the service → 

```bash
systemctl daemon-reload
```

For this application to work fully functional we need to load schema to the Database.

We need to load the schema. To load schema we need to install mysql client.

To have it installed we can use

```
dnf install mysql -y
```

Load Schema → 

```bash
mysql -h <MYSQL-SERVER-IPADDRESS> -uroot -pExpenseApp@1 < /app/schema/backend.sql
```

to start service 

```bash
systemctl start backend
```

to enable service →

```bash
systemctl enable backend
```

to restart the service →

```bash
systemctl restart backend
```
