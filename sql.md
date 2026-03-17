
## SQL

---

mobaXterm : DevOps123

installing mysql-server

```bash
# dnf install mysql-server -y
$ sudo dnf install mysql-server -y
```

to start mysql service → 

```bash
systemctl start mysqld
```

SQL has default username called root

- USERNAME → root
- Default port → 3306

Next, We need to change the default root password in order to start using the database service. Use password ExpenseApp@1 or any other as per your choice.

```bash
mysql_secure_installation --set-root-pass <password>
```

To verify the password → 

```bash
mysql -h <host-address> -u root -p<password>
```

this above command will take you to the mysql

```bash
mysql -> activate the sql
```

to connect locally → 

```bash
mysql -u root -p<password>
```

to use a database or engage with it , →

```bash
use <database-name>;
```

to print all table names → 

```bash
show tables;
```

[Backend](https://www.notion.so/Backend-3207f5b6ee7e80ab9eb7c807f1d4ad40?pvs=21)

[frontend](https://www.notion.so/frontend-3267f5b6ee7e80fa9e78c05414b57baf?pvs=21)
