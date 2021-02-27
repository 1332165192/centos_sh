# Centos7安装MySQL

## 1、下载并安装MySQL

~~~shell
wget http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm &&
yum -y install mysql57-community-release-el7-10.noarch.rpm &&
yum -y install mysql-community-server
~~~

## 2、启动MySQL数据库

~~~shell
systemctl start mysqld.service
~~~

## 3、查看MySQL初始密码

~~~shell
grep "password" /var/log/mysqld.log
~~~

### 4、登录数据库

~~~shell
mysql -uroot -p
~~~

## 5、修改MySQL默认密码

~~~sh
 #修改密码安全策略为低（只校验密码长度，至少8位）。
set global validate_password_policy=0; 
ALTER USER 'root'@'localhost' IDENTIFIED BY '12345678';
~~~

## 6、授予root用户远程管理权限

~~~
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '12345678';
~~~

