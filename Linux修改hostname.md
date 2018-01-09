### Linux下修改hostnmae
- 一般只需要修改 /etc/hosts 和 /etc/sysconfig/network 两个文件下相关配置即可
- 然后命令行输入hostname查看一下当前的hostname是否已经更改
- hostname是Linux系统下的一个内核参数，它保存在/proc/sys/kernel/hostname下，但是它的值是Linux启动时从rc.sysinit读取的。
- /etc/sysconfig/network 确实是hostname的配置文件，hostname的值跟该配置文件中的HOSTNAME有一定的关联关系，但是没有必然关系，hostname的值来自内核参数/proc/sys/kernel/hostname，如果我通过命令sysctl kernel.hostname=Test修改了内核参数，那么hostname就变为了Test了。
- 其实hostname跟/etc/hosts下的配置是没有关系的。hostname的修改、变更完全不依赖hosts文件。
#### 修改hostname的四种方法
1. hostname yourhostname ： 运行后立即生效，新会话生效，但在系统重启后会丢失所做的修改
2. echo yourhostname > /proc/sys/kernel/hostname ： 运行后立即生效，新会话生效，但在系统重启后会丢失所做的修改
3. sysctl kernel.hostname=yourhostname ： 运行后立即生效，新会话生效，但在系统重启后会丢失所做的修改
4. 修改/etc/sysconfig/network下的hostname变量 ：需要重启生效，永久性生效
