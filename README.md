# MySQL-Changing-the-forgotten-root-password

<b>The following commands are executed respectively:</b>
<ul>
  <li>
    sudo /etc/init.d/mysql stop
  </li>
  <li>
    sudo mkdir /var/run/mysqld/
  </li>
<li>
  sudo chown mysql /var/run/mysqld/
  </li>
<li>
  sudo mysqld_safe --skip-grant-tables &
  </li>
<li>
  sudo mysql -u root
  </li>
<li>
  <ul>
    <li>
      use mysql;
    </li>
    <li>
  update user set authentication_string=PASSWORD("NEW_PASSWORD") where User='root';
  </li>
<li>
  flush privileges;
  </li>
<li>
  exit;
  </li>
  </ul>
  </li>
<li>
  sudo /etc/init.d/mysql stop
  </li>
<li>
  sudo /etc/init.d/mysql start
  </li>
</ul>

