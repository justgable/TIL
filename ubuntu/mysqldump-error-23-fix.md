# `mysqldump` Error 23 Fix (Ubuntu) 

Error output

```
mysqldump: Got error: 23: Out of resources when opening file './DB_NAME/TABLE_NAME.MYD' (Errcode: 24 - Too many open files) when using LOCK TABLES
```

Check the number of files in a database and MySQL `open_file_limit`

```
ls /var/lib/mysql/DB_NAME/ -l|wc -l
mysql -u root -p mysql -e "SHOW VARIABLES LIKE 'open%'"
```

Edit `/etc/mysql/my.cnf`. Value should be more than maximum of largest database.

```
[mysqld]
open_file_limit=2048
```

Create system config for MySQL service override

```
sudo mkdir /etc/systemd/system/mysql.service.d
sudo vim /etc/systemd/system/mysql.service.d/override.conf
```

Add to `/etc/systemd/system/mysql.service.d/override.conf`

```
LimitNOFILE=2048
LimitMEMLOCK=2048
```

Restart services and check update value

```
systemctl daemon-reload 
systemctl restart  mysql.service
mysql -u root -p mysql -e "SHOW VARIABLES LIKE 'open%'"
```

[Source 1](http://www.shawnwang.net/1154.html)

[Source 2](https://dba.stackexchange.com/a/86988)
