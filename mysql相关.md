### 设置大小写不敏感
- linux下mysql安装完后是默认：区分表名的大小写，不区分列名的大小写；
- 用root帐号登录后，在/etc/my.cnf 中的[mysqld]后添加添加lower_case_table_names=1，重启MYSQL服务，这时已设置成功：不区分表名的大小写；

### 开启event_scheduler
- 时间调度器是否开启由全局变量event_scheduler决定，它有三个可以设定的值： – OFF : 事件调度器是关闭的，调度线程并没有运行，并且在SHOW PROCESSLIST中不显示，默认值是OFF – ON ：事件调度器是开启的，调度线程并没有运行，并且执行所有的调度事件，通过SHOW PROCESSLIST可以查看Waiting for next activation的进程 – DISABLED : 设定这个值表示Event Scheduler是被禁止的，无法在Mysql运行状态下改变其值。
- 在Mysql启动时如果在my.cnf设置了event_scheduler=ON（OFF or 1 or 0）时，就不能在运行时修改撑DISABLED，如果设置event_scheduler=DISABLED时，就不能在运行时修改其值为ON （ OFF or 1 or 0）
- 在mysql运行时开启/关闭Event（4种方法均可）：
```
SET GLOBAL event_scheduler = ON/OFF;
SET @@global.event_scheduler = ON/OFF;
SET GLOBAL event_scheduler = 1/0;
SET @@global.event_scheduler = 1/0;
```

### 创建用户
- use mysql;
- create user 'new_username'@'%' identified by 'new_password';
- grant all privileges on database.* to 'new_username'@'%' with grant option;
- commit;
- flush privileges;
