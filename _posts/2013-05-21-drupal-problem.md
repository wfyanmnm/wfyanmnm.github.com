---
layout: post
title: "今天布置drupal项目时遇到的几个问题"
description: "mysql问题，权限问题"
category: drupal
tags: [mysql, svn, drupal]
---
## 问题1.去掉更新svn时的提示Password for 'default' GNOME keyring:

    $ svn update
    Password for 'default' GNOME keyring:

解决：edit the ~/.subversion/config with gedit or nano , and add the following

    [auth] 
    password-stores =
参考：[http://askubuntu.com/questions/206604/svn-and-gnome-keyring](http://askubuntu.com/questions/206604/svn-and-gnome-keyring)

## 问题2.ERROR 1396 (HY000): Operation CREATE USER failed for 'wfy'@'localhost'
出现问题的原因： 直接用delete命令删除用户

    delete from mysql.db where user = 'wfy'
正确的做法是

    drop user wfy@localhost;
    flush privileges;
    create user wfy@localhost identified by 'admins_password'
参考：[http://stackoverflow.com/questions/5555328/error-1396-hy000-operation-create-user-failed-for-jacklocalhost](http://stackoverflow.com/questions/5555328/error-1396-hy000-operation-create-user-failed-for-jacklocalhost)
## 问题3.Warning: Got a packet bigger than 'max\_allowed\_packet' bytes query: INSERT INTO watchdog
解决：把mysql的max_allowed_packet参数值设置的大一些

**my.cnf**

    [mysqld]
    max_allowed_packet = 500M
参考：[http://drupal.org/node/355076](http://drupal.org/node/355076)
## 问题4.The directory sites/default/files is not writable
解决：

    chmod -R a+w sites/default/files

{% include JB/setup %}
