## 基本命令使用

### 文件压缩解压tar
1. **选项与参数**：
tar -zxvf zipped_file_name :把文件解压（前五个是独立的命令，压缩解压都要用到其中一个，可以和别的命令连用但只能用其中一个。后面的参数是根据需要在压缩或解压档案时可选的。最后一个参数f是必须的）
- - c：建立压缩档案
- - x：解压
- - t：查看内容
- - r：向压缩归档文件末尾追加文件
- - u：更新原压缩包中的文件
-
- - z：有gzip属性的，此时文件名最好为*.tar.gz
- - j：有bz2属性的，此时文件名最好为*.tar.bz2
- - Z：(大写)有compress属性的
- - v：在压缩/解压缩的过程中,将正在处理的文件名显示出来
- - O：将文件解开到标准输出
- - C：(大写)这个选项用在解压缩,若要在特定目录解压缩,可以使用这个选项。
- - exclude=FILE：在压缩的过程中,不要将FILE打包
- - N：比后面接的日期(yyyy/mm/dd)还要新的才会被打包进新建的文件中
- - f：使用档案名字，切记，这个参数是最后一个参数，后面只能接档案名。
-
- c、t、x不可同时出现在一串指令列中

2. **用例**：
- 将/etc目录下的所有文件全部打包到/tmp目录中
- - tar -cvf /tmp/etc.tar /etc : 仅打包，不压缩
- - tar -jcvf /tmp/etc.tar.bz2 /etc : 以bzip2压缩后打包
- - tar-zcvf /tmp/etc.tar.gz /etc : 以gzip压缩后打包
-
- 显示显示/tmp/etc.tar.bz2内有哪些文件
- - tar -jtvf /tmp/etc.tar.bz2 : 因为文件是bz2结尾，所以是j
-
- 在/usr目录下解压缩/tmp/etc.tar.bz2文件
- - tar -jxvf /tmp/etc.bar.bz2 -C /user : 既然指定了解压到user目录，就需要用大C参数
-
- 仅解开单一档案，例如只需要把/tmp/etc.tar.bz2内的etc/passwd解压开
- - tar-jtf /tmp/etc.tar.bz2 | grep 'passwd' : 找到passwd文档
- - tar-jxvf /tmp/etc.tar.bz2 etc/passwd : 解压
-
- 打包/etc/root目录，但是不包含某些目录
- - tar -jcvf /tmp/etc.tar.bz2 --exclude=file1–exclude=file2 /etc/root : --exclude=file_name(dir_name)表示不包含该文件或目录
-
- 在/etc目录下比‘2012/04/05’新的档案才会备份
- - tar -N '2012/04/05' -jcvf /tmp/etc.tar.bz2 /etc
-
- 将/etc整个目录一边打包一边在/tmp解压，不产生文件
- - cd /tmp
- - tar-cvf - /etc | tar -xvf -

3. **其他**：
- 压缩：
- - tar -cvf jpg.tar *.jpg : 将目录里所有jpg文件打包成tar.jpg
- - tar -czf jpg.tar.gz *.jpg   : 将目录里所有jpg文件打包成jpg.tar后，并且将其用gzip压缩，生成一个gzip压缩过的包，命名为jpg.tar.gz
- - tar -cjf jpg.tar.bz2 *.jpg : 将目录里所有jpg文件打包成jpg.tar后，并且将其用bzip2压缩，生成一个bzip2压缩过的包，命名为jpg.tar.bz2
- - tar -cZf jpg.tar.Z *.jpg   : 将目录里所有jpg文件打包成jpg.tar后，并且将其用compress压缩，生成一个umcompress压缩过的包，命名为jpg.tar.Z
- - rar a jpg.rar *.jpg : rar格式的压缩，需要先下载rar for linux
- - zip jpg.zip *.jpg : zip格式的压缩，需要先下载zip for linux
- - jar -cvf file.war . : 打包war包，要打包war包必须先进入要打包的文件夹，所以最后的参数是个“.”，不然的话war包解压后第一级目录不是原来的目录了，被多生成了一级目录。
- - jar -xvf file.war: 将文件file.war解压到当前路径下
-
- 解压：
- - tar -xvf file.tar : 解压 tar包
- - tar -xzvf file.tar.gz : 解压tar.gz
- - tar -xjvf file.tar.bz2   : 解压 tar.bz2
- - tar -xZvf file.tar.Z   : 解压tar.Z
- - unrar e file.rar : 解压rar
- - unzip file.zip : 解压zip





### 移动文件mv
- mv some_file_name path :将文件some_file_name移动到一个path下，原path不会再有这个文件
- cp -r file_path_1 file_path_2 : 将文件夹1复制到文件夹2中

### 远程拷贝文件scp
1. **简介**：
scp是secure copy的简写，用于在Linux下进行远程拷贝文件的命令，和它类似的命令有cp，不过cp只是在本机进行拷贝不能跨服务器，而且scp传输是加密的。可能会稍微影响一下速度。当你服务器硬盘变为只读 read only system时，用scp可以帮你把文件移出来。另外，scp还非常不占资源，不会提高多少系统负荷，在这一点上，rsync就远远不及它了。虽然 rsync比scp会快一点，但当小文件众多的情况下，rsync会导致硬盘I/O非常高，而scp基本不影响系统正常使用。

2. **命令格式**：scp [参数] [原路径] [目标路径]

3. **命令参数**：
- 1  强制scp命令使用协议ssh1
- 2  强制scp命令使用协议ssh2
- 4  强制scp命令只使用IPv4寻址
- 6  强制scp命令只使用IPv6寻址
- B  使用批处理模式（传输过程中不询问传输口令或短语）
- C  允许压缩。（将-C标志传递给ssh，从而打开压缩功能）
- p 保留原文件的修改时间，访问时间和访问权限。
- q  不显示传输进度条。
- r  递归复制整个目录。
- v 详细方式显示输出。scp和ssh(1)会显示出整个过程的调试信息。这些信息用于调试连接，验证和配置问题。
- c cipher  以cipher将数据传输进行加密，这个选项将直接传递给ssh。
- F ssh_config  指定一个替代的ssh配置文件，此参数直接传递给ssh。
- i identity_file  从指定文件中读取传输时使用的密钥文件，此参数直接传递给ssh。
- l limit  限定用户所能使用的带宽，以Kbit/s为单位。
- o ssh_option  如果习惯于使用ssh_config(5)中的参数传递方式，
- P port  注意是大写的P, port是指定数据传输用到的端口号
- S program  指定加密传输时所使用的程序。此程序必须能够理解ssh(1)的选项。

4. **用例**：
- 从本地服务器复制到远程服务器，复制文件
- - scp local_file remote_username@remote_ip:remote_folder : 指定了远程服务器的用户名和ip，命令执行后需要输入用户密码。
- - scp local_file remote_username@remote_ip:remote_file  : 指定了远程服务器上的文件路径和文件名，文件传到远程服务器上后会更改名字为指定的文件名
- - scp local_file remote_ip:remote_folder  : 没有指定用户名，命令执行后需要输入用户名和密码
- - scp local_file remote_ip:remote_file
-
- 从本地服务器复制到远程服务器，复制目录
- - scp -r local_folder remote_username@remote_ip:remote_folder
- - scp -r local_folder remote_ip:remote_folder
-
- 从远程服务器复制到本地，复制文件
- - scp remote_username@remote_ip:remote_file local_folder : 与从本地复制文件到远程类似，只需要将前两个参数交换位置即可
-
- 从远程服务器复制到本地，复制目录
- - scp -r remote_username@remote_ip:remote_file local_folder

### 查看文件信息whereis
- whereis python :查看python安装在哪个目录下


### which


### 文本搜索grep
1. **简介**:
Linux系统中grep命令是一种强大的文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来。grep全称是Global Regular Expression Print，表示全局正则表达式版本，它的使用权限是所有用户。grep的工作方式是这样的，它在一个或多个文件中搜索字符串模板。如果模板包括空格，则必须被引用，模板后的所有字符串被看作文件名。搜索的结果被送到标准输出，不影响原文件内容。grep可用于shell脚本，因为grep通过返回一个状态值来说明搜索的状态，如果模板搜索成功，则返回0，如果搜索不成功，则返回1，如果搜索的文件不存在，则返回2。我们利用这些返回值就可进行一些自动化的文本处理工作。

2. **命令格式**：
grep [option] pattern file

3. **命令参数**：
- a   --text   #不要忽略二进制的数据。
- A<显示行数>   --after-context=<显示行数>   #除了显示符合范本样式的那一列之外，并显示该行之后的内容。
- b   --byte-offset   #在显示符合样式的那一行之前，标示出该行第一个字符的编号。
- B<显示行数>   --before-context=<显示行数>   #除了显示符合样式的那一行之外，并显示该行之前的内容。
- c    --count   #计算符合样式的列数。
- C<显示行数>    --context=<显示行数>或-<显示行数>   #除了显示符合样式的那一行之外，并显示该行之前后的内容。
- d <动作>      --directories=<动作>   #当指定要查找的是目录而非文件时，必须使用这项参数，否则grep指令将回报信息并停止动作。
- e <范本样式>  --regexp=<范本样式>   #指定字符串做为查找文件内容的样式。
- E  --extended-regexp   #将样式为延伸的普通表示法来使用。
- f<规则文件>  --file=<规则文件>   #指定规则文件，其内容含有一个或多个规则样式，让grep查找符合规则条件的文件内容，格式为每行一个规则样式。
- F --fixed-regexp   #将样式视为固定字符串的列表。
- G  --basic-regexp   #将样式视为普通的表示法来使用。
- h  --no-filename   #在显示符合样式的那一行之前，不标示该行所属的文件名称。
- H   --with-filename   #在显示符合样式的那一行之前，表示该行所属的文件名称。
- i    --ignore-case   #忽略字符大小写的差别。
- l    --file-with-matches   #列出文件内容符合指定的样式的文件名称。
- L   --files-without-match   #列出文件内容不符合指定的样式的文件名称。
- n   --line-number   #在显示符合样式的那一行之前，标示出该行的列数编号。
- q   --quiet或--silent   #不显示任何信息。
- r   --recursive   #此参数的效果和指定“-d recurse”参数相同。
- s   --no-messages   #不显示错误信息。
- v   --revert-match   #显示不包含匹配文本的所有行。
- V   --version   #显示版本信息。
- w   --word-regexp   #只显示全字符合的列。
- x    --line-regexp   #只显示全列符合的列。
- y   #此参数的效果和指定“-i”参数相同。

4. **规则表达式**：
- grep的规则表达式：
- - ^  #锚定行的开始 如：'^grep'匹配所有以grep开头的行。
- - $  #锚定行的结束 如：'grep$'匹配所有以grep结尾的行。
- - .  #匹配一个非换行符的字符 如：'gr.p'匹配gr后接一个任意字符，然后是p。
- - \*  #匹配零个或多个先前字符 如：'*grep'匹配所有一个或多个空格后紧跟grep的行。
- - .*   #一起用代表任意字符。
- - [ ]   #匹配一个指定范围内的字符，如'[Gg]rep'匹配Grep和grep。
- - [^]  #匹配一个不在指定范围内的字符，如：'[^A-FH-Z]rep'匹配不包含A-R和T-Z的一个字母开头，紧跟rep的行。
- - \\(..\\)  #标记匹配字符，如'\(love\)'，love被标记为1。
- - \\<      #锚定单词的开始，如:'\<grep'匹配包含以grep开头的单词的行。
- - \\>      #锚定单词的结束，如'grep\>'匹配包含以grep结尾的单词的行。
- - x\\{m\\}  #重复字符x，m次，如：'0\{5\}'匹配包含5个o的行。
- - x\\{m,\\}  #重复字符x,至少m次，如：'o\{5,\}'匹配至少有5个o的行。
- - x\\{m,n\\}  #重复字符x，至少m次，不多于n次，如：'o\{5,10\}'匹配5--10个o的行。
- - \\w    #匹配文字和数字字符，也就是[A-Za-z0-9]，如：'G\w*p'匹配以G后跟零个或多个文字或数字字符，然后是p。
- - \\W    #\w的反置形式，匹配一个或多个非单词字符，如点号句号等。
- - \\b    #单词锁定符，如: '\bgrep\b'只匹配grep。
-
- POSIX字符:为了在不同国家的字符编码中保持一至，POSIX(The Portable Operating System Interface)增加了特殊的字符类，如[:alnum:]是[A-Za-z0-9]的另一个写法。要把它们放到[]号内才能成为正则表达式，如[A- Za-z0-9]或[[:alnum:]]。在linux下的grep除fgrep外，都支持POSIX的字符类。
- - [:alnum:]    #文字数字字符
- - [:alpha:]    #文字字符
- - [:digit:]    #数字字符
- - [:graph:]    #非空字符（非空格、控制字符）
- - [:lower:]    #小写字符
- - [:cntrl:]    #控制字符
- - [:print:]    #非空字符（包括空格）
- - [:punct:]    #标点符号
- - [:space:]    #所有空白字符（新行，空格，制表符）
- - [:upper:]    #大写字符
- - [:xdigit:]   #十六进制数字（0-9，a-f，A-F）

5. **用例**：
- 查找指定进程
- - ps -ef | grep svn : 查找svn进程
-
- grep不显示本身进程
- - ps aux|grep \\[s]sh
- - ps aux | grep ssh | grep -v "grep"
-
- 查找指定进程个数
- - ps -ef|grep svn -c
- - ps -ef|grep -c svn
-
- 从文件中读取关键词进行搜索
- - cat test.txt | grep -f test2.txt : 输出test.txt文件中含有从test2.txt文件中读取出的关键词的内容行
-
- 从文件中读取关键词进行搜索 且显示行号
- - cat test.txt | grep -nf test2.txt : 输出test.txt文件中含有从test2.txt文件中读取出的关键词的内容行，并显示每一行的行号
-
- 从文件中查找关键词
- - grep 'linux' test.txt
-
- 从多个文件中查找关键词
- - grep 'linux' test.txt test2.txt
-
- 找出已u开头的行内容
- - cat test.txt |grep ^u
-
- 输出非u开头的行内容
- -cat test.txt |grep ^[^u]
-
- 输出以hat结尾的行内容
- - cat test.txt |grep hat$
-
- 显示包含ed或者at字符的内容行
- - cat test.txt |grep -E "ed|at"
-
- 显示当前目录下面以.txt 结尾的文件中的所有包含每个字符串至少有7个连续小写字符的字符串的行
- - grep '[a-z]\\{7\\}' *.txt

### 软件包管理rpm


### 权限管理chmod


### 网络连接netstat
1.**简介**：
- netstat命令用于显示与IP、TCP、UDP和ICMP协议相关的统计数据，一般用于检验本机各端口的网络连接情况。netstat是在内核中访问网络及相关信息的程序，它能提供TCP连接，TCP和UDP监听，进程内存管理的相关报告。
- 如果你的计算机有时候接收到的数据报导致出错数据或故障，你不必感到奇怪，TCP/IP可以容许这些类型的错误，并能够自动重发数据报。但如果累计的出错情况数目占到所接收的IP数据报相当大的百分比，或者它的数目正迅速增加，那么你就应该使用netstat查一查为什么会出现这些情况了。

2.**命令格式**：
- netstat [-acCeFghilMnNoprstuvVwx][-A<网络类型>][--ip]

3.**命令参数**：
- a或–all 显示所有连线中的Socket。
- A<网络类型>或–<网络类型> 列出该网络类型连线中的相关地址。
- c或–continuous 持续列出网络状态。
- C或–cache 显示路由器配置的快取信息。
- e或–extend 显示网络其他相关信息。
- F或–fib 显示FIB。
- g或–groups 显示多重广播功能群组组员名单。
- h或–help 在线帮助。
- i或–interfaces 显示网络界面信息表单。
- l或–listening 显示监控中的服务器的Socket。
- M或–masquerade 显示伪装的网络连线。
- n或–numeric 直接使用IP地址，而不通过域名服务器。
- N或–netlink或–symbolic 显示网络硬件外围设备的符号连接名称。
- o或–timers 显示计时器。
- p或–programs 显示正在使用Socket的程序识别码和程序名称。
- r或–route 显示Routing Table。
- s或–statistice 显示网络工作信息统计表。
- t或–tcp 显示TCP传输协议的连线状况。
- u或–udp 显示UDP传输协议的连线状况。
- v或–verbose 显示指令执行过程。
- V或–version 显示版本信息。
- w或–raw 显示RAW传输协议的连线状况。
- x或–unix 此参数的效果和指定”-A unix”参数相同。
– ip或–inet 此参数的效果和指定”-A inet”参数相同。

4.**用例**：
- 显示当前UDP链接状况
- - netstat -nu
-
- 显示UDP端口号的使用情况
- - netstat -apu
-
- 显示网卡列表
- - netstat -i
-
- 显示监听的套接口
- - netstat -l
-
- 显示所有已建立的有效连接
- - netstat -n







### 进程管理ps




## 具体操作汇集

- cat /etc/passwd :查看所有用户信息
- su - root :su命令切换用户
- kill -9 pid : pid为进程号，该命令用来关闭某个进程
- netstat -anp|grep 80 : 查看有80字样的端口的情况
- echo 1 > /proc/sys/vm/drop_caches
- sz file_name :发送文件到本地
- rz ：本地文件上传到远端
