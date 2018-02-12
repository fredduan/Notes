### MR job 运行分析
1. client提交MR的job给rm
2. rm协调资源分配
3. nm启动并监控container
4. app master协调task
5. app master和task均由rm调度、由nm管理
6. hdfs用于在其他entity间共享job文件
