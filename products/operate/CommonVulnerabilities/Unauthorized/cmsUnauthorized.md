---
sidebar_position: 9
---
# 通用cms的未授权访问

**漏洞描述：**

一些通用的CMS存在通用未授权访问漏洞，导致攻击者可以直接访问，从而引发重要权限可被操作、数据库、网站目录等敏感信息泄露。

**漏洞案例：**

Active MQ  未授权访问漏洞
Atlassian Crowd 未授权访问漏洞
CouchDB 未授权访问漏洞
Docker 未授权访问漏洞
nacos 未授权访问漏洞
Dubbo 未授权访问漏洞
Druid 未授权访问漏洞
Elasticsearch 未授权访问漏洞
FTP 未授权访问漏洞
Hadoop 未授权访问漏洞
Jenkins 未授权访问漏洞
Jupyter Notebook 未授权访问漏洞
Kibana 未授权访问漏洞
Kubernetes Api Server 未授权访问漏洞
LDAP 未授权访问漏洞
MongoDB 未授权访问漏洞
Memcached 未授权访问漏洞
NFS 未授权访问漏洞
Rsync 未授权访问漏洞
Redis 未授权访问漏洞
RabbitMQ 未授权访问漏洞
Solr 未授权访问漏洞
Spring Boot Actuator 未授权访问漏洞
Spark 未授权访问漏洞
VNC 未授权访问漏洞
Weblogic 未授权访问漏洞
ZooKeeper 未授权访问漏洞
Zabbix 未授权访问漏洞
redmine 未授权访问漏洞
Proxool  未授权访问漏洞
jboss jmx-concle 未授权访问漏洞
Apache Solr 未授权访问漏洞

***案例1***

nacos 未授权访问漏洞

访问未授权地址https://xxx.xx.x.x/nacos/v1/auth/users?pageNo=1&pageSize=9
成功未授权查看用户列表信息

![](/img/products/yakit/cmsUnauthorized-1.png)

***案例2***

zabbix未授权访问

访问未授权地址https://xxx.xx.x.x/zabbix.php?action=problem.view&ddreset=1
可未授权访问后台

![](/img/products/yakit/cmsUnauthorized-2.png)

***案例3***

Elasticsearch 未授权访问漏洞

访问未授权地址https://xxx.xx.x.x/_nodes
查看节点数据

![](/img/products/yakit/cmsUnauthorized-3.png)

***案例4***

Jenkins 未授权访问漏洞

访问未授权地址https://xxx.xx.x.x/manage/

![](/img/products/yakit/cmsUnauthorized-4.png)

访问未授权地址https://xxx.xx.x.x/script/
可以执行系统命令：println "whoami".execute().text

![](/img/products/yakit/cmsUnauthorized-5.png)

***案例5***

Elasticsearch 未授权访问漏洞

访问测试网站，出现该以下关键字

![](/img/products/yakit/cmsUnauthorized-6.png)

访问下列api接口
/_plugin/head/ web管理界面
/_cat/indices
/_river/_search 查看数据库敏感信息
/_nodes 查看节点数据

其中一个接口为：

![](/img/products/yakit/cmsUnauthorized-7.png)
