# Completely Remove MySQL (Ubuntu)

```
sudo -i
service mysql stop
killall -KILL mysql mysqld_safe mysqld
apt-get --yes purge mysql-server mysql-client
apt-get --yes autoremove --purge
apt-get autoclean
deluser --remove-home mysql
delgroup mysql
rm -rf /etc/apparmor.d/abstractions/mysql /etc/apparmor.d/cache/usr.sbin.mysqld /etc/mysql /var/lib/mysql /var/log/mysql* /var/log/upstart/mysql.log* /var/run/mysqld
updatedb
exit
rm ~/.mysql_history
```

Run `dpgk -l | grep mysql` to verify there are no more MySQL packages installed.

_* Tested on Ubuntu 16.04 using MySQL 5.7_

[Source](https://askubuntu.com/a/640900)
