###  生产环境



| 服务名称     | 服务器IP      | 端口号 | 部署目录                                 | 配置路径                       |
| ------------ | ------------- | ------ | ---------------------------------------- | ------------------------------ |
| 运维接口-主  | 172.16.10.107 | 17506  | /bsn/yunwei	jar                       |                                |
| 运维接口-从  | 172.16.10.115 | 17506  | /bsn/yunwei	jar                       |                                |
| 运维管理系统 | 172.16.10.107 | 17503  | /home/tomcat-yunwei/war                  |                                |
| 账单定时任务 | 172.16.10.107 | 17510  | /home/tomcat-yunwei-bill	Tomcat/warcd |                                |
| 监控中心     | 172.16.10.109 | 17500  | /chainnet/tomcat-monitor	Tomcat/war   |                                |
| OPB 采集器   | 161.189.51.51 | 29021  | /bsn/go/src/node-collect/                | cd /bsn/opb/tx                 |
| OPB_定时监控 | 172.16.10.43  | 17504  | /bsn/tomcat-task                         | cd /bsn/tomcat-task_conf/conf/ |