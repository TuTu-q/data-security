第一、MYSQL
数据库（database）就是一个存储数据的仓库。为了方便数据的存储和管理，它将数据按照特定的规律存储在磁盘上。通过数据库管理系统，可以有效地组织和管理存储在数据库中的数据。MySQL数据库可以称得上是目前运行速度最快的SQL语言数据库,MySQL数据库可以称得上是目前运行速度最快的SQL语言数据库。
MySQL是一款免费软件。任何人都可以从MySQL的官方网站下载该软件。MySQL是一个真正的多用户、多线程SQL数据库服务器。它是以客户机/服务器结构实现的，由一个服务器守护程序mysqld以及很多不同的客户程序和库组成。它能够快捷、有效和安全地处理大量的数据。相对于Oracle等数据库来说，MySQL的使用非常简单。MySQL主要目标是快速、便捷和易用。
对MYSQL数据库安全配置、或者叫加固属于数据安全的一环，它需要安全人员在理论和实践的学习中不断发现新的问题，并针对这些问题对数据的各个方面的配置进行强化。
第二、实验目标
掌握MYSQL安装及基本配置，了解MYSQL数据库安全配置及可能存在风险（后期攻防将针对该安全配置进行模拟攻击）。 
第三、实验概述
1.在CentOS中安装及配置MYSQL。
2.了解和修改MYSQL安全配置选项。
第四、实验详细步骤
安装前的准备
到官网下载mysql-8.0.16-linux-glibc2.12-x86_64.tar.xd
通过Xshell或者Xftp、PSPC等工具把安装包上传到CentOS服务器。
#解压缩包
xd –d mysql-8.0.16-linux-glibc2.12-x86_64.tar.xd
tar -xvf mysql-8.0.16-linux-glibc2.12-x86_64.tar
#给包重命名为mysql,并安装到/usr/local/目录下
mv mysql-8.0.16-linux-glibc2.12-x86_64 /usr/local/mysql
#查看mysql目录下的文件
 
#检查mysql组和用户是否存在，如无创建
cat /etc/group | grep mysql 
cat /etc/passwd | grep mysql
#创建mysql用户组
groupadd mysql
useradd -g mysql mysql
#修改用户mysql的密码为A2019a（自己设定）
passwd mysql
 
#更改所属的组和用户
chown -R mysql mysql
chgrp -R mysql mysql
#进入mysql目录
cd /usr/local/mysql
#创建data目录，创建后会默认设定一个随机mysql登陆密码SnQytTb>%1;6（每次执行都会不一样）
su mysql
cd /usr/local/mysql/bin
./mysqld –initialize
 
#新版的数据库是没有my.cnf需要创建my.cnf
#在/etc/下创建创建my.cnf
cd /etc/
touch my.cnf
vim my.cnf
cat my.cnf
在配置文件my.cnf添加如下配置：
 
#修改config配置，修改SELINUX=disabled
vi /etc/selinux/config
 
#修改mysql目录权限
chown -R mysql:mysql /usr/local/mysql
#创建软连接(实现可直接命令行执行mysql)
ln -s /usr/local/mysql/bin/mysql /usr/bin
#mysqld配置,拷贝启动文件到/etc/init.d/下并重命令为mysqld
cp /usr/local/mysql/support-files/mysql.server  /etc/init.d/mysqld
#增加执行权限
chmod 755 /etc/init.d/mysqld
#检查自启动项列表中没有mysqld
chkconfig --list mysqld
#如果没有就添加mysqld
chkconfig --add mysqld
#设置开机启动
chkconfig mysqld on
#启动测试
service mysqld start
 
说明我们的配置文件成功，mysql彻底安装完成。
安装完数据库后，我们需要重置mysql连接密码，用上面随机生成的密码登陆mysql。
mysql -u root -p (一路直接回车)
 
#在mysql中修改密码为123456。
set PASSWORD = '123456';
 
第五、MYSQL数据安全配置
参考https://www.freebuf.com/articles/database/36777.html

