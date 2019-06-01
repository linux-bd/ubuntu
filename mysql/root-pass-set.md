## Ubuntu root password setting 18.04
```
sudo mysql --user=root mysql
update user set authentication_string=PASSWORD('nopass') where user='root';
update user set plugin="mysql_native_password" where User='root';
flush privileges;
quit;
sudo service mysql stop
sudo service mysql start
```
