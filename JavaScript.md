# 对象
1、数字的字面值（literal）不能当作对象使用。这是因为 JavaScript 解析器的一个错误， 它试图将点操作符解析为浮点数字面值的一部分。
```
2.toString(); // 出错：SyntaxError
```
有很多变通方法可以让数字的字面值看起来像对象。
```
2..toString(); // 第二个点号可以正常解析
2 .toString(); // 注意点号前面的空格
(2).toString(); // 2先被计算
```

# 作用域（程序源代码中定义变量的区域）
静态作用域与动态作用域 
- 静态作用于（词法作用域）：函数的作用域在函数定义的时候就决定了
- 动态作用于：函数的作用域在函数调用的时候才决定
- JavaScript 采用词法作用域(lexical scoping)，也就是静态作用域。

# 执行上下文（execution context）：
对于每个执行上下文，都有三个重要属性：
- 变量对象(Variabel object, VO)
- 作用域链(Scope chain)
- this


# JSON
'{"prop": "val"}' 是个合法的JSON, 但'{prop: "val"}'和"{'prop': 'val'}"都是不合法的,
所有属性名称和它的值都必须用双引号引住，不能使用单引号


# Linux 安装 MySql  http://blog.csdn.net/zhou920786312/article/details/77750604
/usr/local/mysql/bin/mysqld: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory
缺少安装包libaio和libaio-devel.
[root@iZwz9e9bjg74ljcpzr7stvZ bin]# yum install libaio

[root@iZwz9e9bjg74ljcpzr7stvZ bin]# ./mysqld --initialize --user=mysql --datadir=/usr/local/mysql/data/ 
2017-11-09T09:09:52.826209Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2017-11-09T09:09:54.885578Z 0 [Warning] InnoDB: New log files created, LSN=45790
2017-11-09T09:09:55.105938Z 0 [Warning] InnoDB: Creating foreign key constraint system tables.
2017-11-09T09:09:55.218562Z 0 [Warning] No existing UUID has been found, so we assume that this is the first time that this server has been started. Generating a new UUID: c0844cc4-c52d-11e7-b74f-00163e0ae84e.
2017-11-09T09:09:55.221300Z 0 [Warning] Gtid table is not ready to be used. Table 'mysql.gtid_executed' cannot be opened.
2017-11-09T09:09:55.221784Z 1 [Note] A temporary password is generated for root@localhost: uf)qP3+C?jpJ
[root@iZwz9e9bjg74ljcpzr7stvZ bin]# 


mysql -uroot -p

输入设置的密码

竟然报错了！

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YSE)

问朋友，他说初始密码是空的，可我命名设置了密码的阿。

密码留空

还是错误！

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

于是重改密码！

# /etc/init.d/mysql stop
# mysqld_safe --user=mysql --skip-grant-tables --skip-networking &
# mysql -u root mysql
mysql> UPDATE user SET Password=PASSWORD('newpassword') where USER='root';
mysql> FLUSH PRIVILEGES;
mysql> quit

# /etc/init.d/mysqld restart
# mysql -uroot -p
Enter password:

mysql>



新安装的MySQL5.7，登录时提示密码错误，安装的时候并没有更改密码，后来通过免密码登录的方式更改密码，输入update mysql.user  set password=password('root') where user='root'时提示ERROR 1054 (42S22): Unknown column 'password' in 'field list'，原来是mysql数据库下已经没有password这个字段了，password字段改成了
authentication_string

所以更改语句替换为update mysql.user set authentication_string=password('root') where user='root' ;即可
