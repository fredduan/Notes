### HDFS 基本操作命令

- hdfs dfs -命令 参数
- 这是hdfs操作的基本格式，其中命令跟一般的bash命令大部分一致，只需要前面加个“-”.
-
- hdfs dfs -put /本地的路径 /hdfs上的路径
- 该命令将本地的文件put到hdfs上面去
-
- hdfs dfs -get /hdfs上的路径 /本地的路径
- 该命令将hdfs上的文件下载到本地
-
- hdfs dfs -copyFromLocal /本地的路径 /hdfs上的路径
- 从本地拷贝文件至hdfs
-
- hdfs dfs -copyToLocal /hdfs上的路径 /本地的路径
- 从hdfs拷贝到本地

### HDFS基本系统架构

- hdfs主要采用主备模式，其架构包含NameNode，DataNode，Client三个部分
- - NameNode:NameNode用于存储、生成文件系统的元数据。运行一个实例。
- - DataNode：DataNode用于存储实际的数据，将自己管理的数据块上报给NameNode ，运行多个实例。
- - Client：支持业务访问HDFS，从NameNode ,DataNode获取数据返回给业务。多个实例，和业务一起运行。
