### SSH互信
- 原理就是，我跟你互信，我有一个私钥，把公钥传给你，这样以后在连的时候就不要密码了，反正谁手上有我的公钥，谁就能免密连到我。

- 第一步，关掉防火墙：service iptables stop

- 第二步，修改/etc/selinux/config。将其中的selinux的参数改为“disabled”

- 第三步，修改SSH配置文件（vi /etc/ssh/sshd_config），将以下三个配置去掉注释
``` txt
RSAAuthentication yes //字面意思..允许RSA认证

PubkeyAuthentication yes //允许公钥认证

AuthorizedKeysFile .ssh/authorized_keys //公钥存放在.ssh/au..文件中
```

- 第四步，修改完配置文件后，需要重启ssh服务。执行如下命令：/etc/init.d/sshd restart。注意在A、B两台机器都执行修改配置文件和重启ssh的操作。

- 第五步，生成密码对（ssh-keygen -t rsa），可以在路径././.ssh下找到生成的私钥idrsa公钥idrsa.pub。在A、B两台机器都执行这个命令。

- 第六步，将A的公钥传到B上，注意由于两台机都生成了公钥，所以其中一台公钥的名称需要改一下，否则就乱了。

- 第七步，在B机器上将公钥写入到authorized_keys，注意是A的公钥和B的公钥都要写
``` txt
cat id_rsa.pub >>authorized_keys

cat id_rsa.pub.host2 >>authorized_keys
```

- 第八步，修改authorized_keys文件权限（chmod 644 authorized_keys）

- 第九步，把刚才B机器的authorized_keys文件传到A机器上来，然后试一下ssh，验证是不是A和B就不需要输密码了
