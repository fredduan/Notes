### 挂载光盘文件并添加到yum源上

- 将CentOS的ios文件传到/meida下，然后输入命令mount -o loop /media/CentOS.ios /meida. 这样就把ios光盘挂载到media目录下了
- cd到/etc/yum.repos.d目录下，建立以repo为结尾的文件
- 将刚才建立的文件输入以下内容
``` txt
[rhel-server]
name=server
baseurl=file:/meida
enabled=1
gpgcheck=0
```
- 完成上一步后用命令yum clean all进行刷新
- 至此完成了光盘文件挂载和yum源配置
