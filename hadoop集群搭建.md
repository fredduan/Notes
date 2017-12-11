IP：
- 192.9.99.150，4G内存
- 192.9.99.151
- 192.9.99.152
- 192.9.99.153
- 192.9.99.154，4G内存
  
password：password

## 解析IP对应的主机名
scp /etc/hosts/ 192.9.99.151
    
fdisc -l
## 改磁盘
pvcreate 物理卷
vgcreate 
lvcreate 逻辑卷组

view-chat window 打开chat窗口，同时跟所有虚机对话
## 建立互信
所有服务器：
- $ mkdir ~/.ssh
- $ chmod 700 ~/.ssh
- $ /usr/bin/ssh-keygen -t rsa
- $ /usr/bin/ssh-keygen -t dsa
- $ cd ~/.ssh

hadoop01服务器：
[hadoop@node1 .ssh]$ ssh hadoop01 cat /home/hadoop/.ssh/id_rsa.pub >> authorized_keys
[hadoop@node1 .ssh]$ ssh hadoop01 cat /home/hadoop/.ssh/id_dsa.pub >> authorized_keys
[hadoop@node1 .ssh]$ ssh hadoop02 cat /home/hadoop/.ssh/id_rsa.pub >> authorized_keys
[hadoop@node1 .ssh]$ ssh hadoop02 cat /home/hadoop/.ssh/id_dsa.pub >> authorized_keys
[hadoop@node1 .ssh]$ ssh hadoop03 cat /home/hadoop/.ssh/id_rsa.pub >> authorized_keys
[hadoop@node1 .ssh]$ ssh hadoop03 cat /home/hadoop/.ssh/id_dsa.pub >> authorized_keys
[hadoop@node1 .ssh]$ ssh hadoop04 cat /home/hadoop/.ssh/id_rsa.pub >> authorized_keys
[hadoop@node1 .ssh]$ ssh hadoop04 cat /home/hadoop/.ssh/id_dsa.pub >> authorized_keys
[hadoop@node1 .ssh]scp authorized_keys hadoop02:/home/hadoop/.ssh/
[hadoop@node1 .ssh]scp authorized_keys hadoop03:/home/hadoop/.ssh/
[hadoop@node1 .ssh]scp authorized_keys hadoop04:/home/hadoop/.ssh/

## 配时间同步
service iptables stop-关防火墙
chkconfig ntpd on
service ntpd start

ntpq -q 命令输出时间同步的情况在显示器上

## 改端口

## 安装MySQL
- 创建MySQL组
- 创建MySQL用户
- 建软连接 

## MySQL里建一个Ambari用户，给这个用户权限

## 安装Ambari
- ambari-2.5.1.0-centos6.tar.gz


