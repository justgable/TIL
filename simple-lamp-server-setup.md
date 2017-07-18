# Simple LAMP Server Setup (Ubuntu)

## Create user with sudo access

```
adduser username
adduser username sudo
exit
ssh username@203.0.113.10
```

## Setup SSH Key-pair authentication

```
ssh-keygen -b 4096
ssh-copy-id username@203.0.113.10
```

Verify you are able to ssh into the server without a password prompt

*On OSX install `ssh-copy-id` with `brew install ssh-copy-id`*

### Update SSH Daemon configuration

```
sudo vim /etc/ssh/sshd_config
```
Set `sshd_config` settings below

```
PermitRootLogin no
PasswordAuthentication no
```

Save the file then run

```
sudo service ssh restart
```

## Install Fail2Ban

```
sudo apt-get install fail2ban
```

[Source](https://www.linode.com/docs/security/securing-your-server)

## Setup Firewall (UFW)

```
ufw allow 80/tcp
ufw allow http/tcp
ufw allow ssh
ufw allow https

sudo systemctl start ufw
sudo systemctl enable ufw
sudo ufw status
```

[Source](https://www.linode.com/docs/security/firewalls/configure-firewall-with-ufw)

## Setup LAMP Stack

### Install Apache 2.4, PHP 7.0 (FPM) and MySQL

```
sudo apt-get install apache2 mysql-server php-mysql php -y
sudo a2enmod proxy_fcgi
```

Configure VirtualHost with `ProxyPassMatch`

```
# Example
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName mywebsite.com
	DocumentRoot /var/www/mywebsite.com/prod

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	ProxyPassMatch ^/(.*\.php(/.*)?)$ unix:/run/php/php7.0-fpm.sock|fcgi://localhost/var/www/mywebsite.com/prod
</VirtualHost>
```

[Source](http://www.geoffstratton.com/ubuntu-1604-web-server-apache-php-and-mysql)
