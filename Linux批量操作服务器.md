### 方法一
- ssh -tt
- 这种方法实际上是先连上一台其他机器，然后输入一个命令，把前面这两件事情放在一个循环里就成了
``` shell
for i in {40..92};  #在命令行里输入一个for循环，40和92分别是连续的IP的最后一位的首末
do ssh 10.135.1.$i  #连到服务器
"sed -i 's/^Defaults    requiretty/\#Defaults    requiretty/'/etc/sudoers";
# sed是一个流编辑器stream edit；找到/etc/sudoers文件中“Defaults requiretty”那一行然后改成“#Defaults requiretty”
done # 结束循环
```
- 这种方法的优点是简单，根本不用写脚本，特别适合批量简单通用的命令。缺点是如果没有做ssh互信，得输入N次密码，当然密码可以复制所以没什么特别不方便的。
