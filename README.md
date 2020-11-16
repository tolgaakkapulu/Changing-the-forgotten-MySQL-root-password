# Changing the forgotten MySQL root password

<b>The following commands are executed respectively:</b>
- sudo systemctl stop mysql.service
- sudo mkdir /var/run/mysqld/
- sudo chown mysql /var/run/mysqld/
- sudo mysqld_safe --skip-grant-tables &
- sudo mysql -u root
  - use mysql;
  - update user set authentication_string=PASSWORD("NEW_PASSWORD") where User='root';
  - flush privileges;
  - GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY 'NEW_PASSWORD';
  - flush privileges;
  - exit;
- sudo systemctl stop mysql.service
- sudo ps ax | grep mysql | grep grant | awk '{print "kill -9 " $1}' | bash
- systemctl daemon-reload
- sudo systemctl start mysql.service
