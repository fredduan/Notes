### Linux系统配置IP地址
- 在生成一个虚机后，必须要给它分配一个IP地址，注意该ip地址不能跟同一网段下有重复的ip。
- 以下是修改网卡eth0的IP配置的方法
- cd /etc/sysconfig/network-scripts
- 找到ifcfg-eth0文件，然后vim它，按照以下方法修改
``` txt
DEVICE=eth0 #这个是网卡的名字
IPADDR=192.168.13.104 #这个就是IP了，以后就通过它访问服务器
NETMASK=255.255.255.0 #掩码
DNS1=192.168.0.7 #这个应该是DNS服务器的地址
DOMAIN=192.168.0.8 #这个不知道是啥
GATEWAY=192.168.13.254 #网关
HWADDR=00:50:56:A0:C5:BE #MAC地址，不需要改
TYPE=Ethernet #网卡类型，不需要改
UUID=2c0ec31f-2b94-4bc7-ac79-ce7514894bcf #这个不知道是啥，不需要改
ONBOOT=yes #这个要改成yes
NM_CONTROLLED=yes #这个不知道是啥
BOOTPROTO=none #这个要改成none
```
- 修改完配置文件后，需要重启网卡
- service network restart
- 重启如果不报错，可以从本地ping一下上面那个IP，看能不能通，通了表示配置成功
