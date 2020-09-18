# RocketMQ

## 官网：
https://rocketmq.apache.org/  

##  中文文档
https://github.com/apache/rocketmq/tree/master/docs/cn

##  阿里云
https://cn.aliyun.com/product/rocketmq

[https://help.aliyun.com/document_detail/124693.html?spm=a2c4g.11186623.6.586.1e6c2afaw1tvEF](https://help.aliyun.com/document_detail/124693.html?spm=a2c4g.11186623.6.586.1e6c2afaw1tvEF)



## Quick Start [ rocketmq-docker + rocketmq-console-ng ]

###  rocketmq-docker
https://github.com/apache/rocketmq-docker

###  rocketmq-console-ng
https://github.com/StyleTang/rocketmq-console-ng


#  环境搭建DOCKER


##  官方镜像
https://hub.docker.com/u/apacherocketmq


##  自定义镜像
https://hub.docker.com/repository/docker/ibackchina2018/rocketmq/general



**搭建NameSrv &  Broker**

```
docker run -d -v `pwd`/data/namesrv/logs:/home/rocketmq/logs --name rmqnamesrv -p 9876:9876 ibackchina2018/rocketmq:4.5.0-alpine sh mqnamesrv

```



```
docker run -d -v `pwd`/data/broker/logs:/home/rocketmq/logs -v `pwd`/data/broker/store:/home/rocketmq/store --name rmqbroker --link rmqnamesrv:namesrv -e "NAMESRV_ADDR=namesrv:9876" -p 10909:10909 -p 10911:10911 -p 10912:10912 ibackchina2018/rocketmq:4.5.0-alpine sh mqbroker
```





#  cli-admin-tool

https://rocketmq.apache.org/docs/cli-admin-tool/



```
bash mqadmin
```

```
bash mqadmin
OpenJDK 64-Bit Server VM warning: ignoring option PermSize=128m; support was removed in 8.0
OpenJDK 64-Bit Server VM warning: ignoring option MaxPermSize=128m; support was removed in 8.0
The most commonly used mqadmin commands are:
   updateTopic          Update or create topic
   deleteTopic          Delete topic from broker and NameServer.
   updateSubGroup       Update or create subscription group
   deleteSubGroup       Delete subscription group from broker.
   updateBrokerConfig   Update broker's config
   updateTopicPerm      Update topic perm
   topicRoute           Examine topic route info
   topicStatus          Examine topic Status info
   topicClusterList     get cluster info for topic
   brokerStatus         Fetch broker runtime status data
   queryMsgById         Query Message by Id
   queryMsgByKey        Query Message by Key
   queryMsgByUniqueKey  Query Message by Unique key
   queryMsgByOffset     Query Message by offset
   printMsg             Print Message Detail
   printMsgByQueue      Print Message Detail
   sendMsgStatus        send msg to broker.
   brokerConsumeStats   Fetch broker consume stats data
   producerConnection   Query producer's socket connection and client version
   consumerConnection   Query consumer's socket connection, client version and subscription
   consumerProgress     Query consumers's progress, speed
   consumerStatus       Query consumer's internal data structure
   cloneGroupOffset     clone offset from other group.
   clusterList          List all of clusters
   topicList            Fetch all topic list from name server
   updateKvConfig       Create or update KV config.
   deleteKvConfig       Delete KV config.
   wipeWritePerm        Wipe write perm of broker in all name server
   resetOffsetByTime    Reset consumer offset by timestamp(without client restart).
   updateOrderConf      Create or update or delete order conf
   cleanExpiredCQ       Clean expired ConsumeQueue on broker.
   cleanUnusedTopic     Clean unused topic on broker.
   startMonitoring      Start Monitoring
   statsAll             Topic and Consumer tps stats
   allocateMQ           Allocate MQ
   checkMsgSendRT       check message send response time
   clusterRT            List All clusters Message Send RT
   getNamesrvConfig     Get configs of name server.
   updateNamesrvConfig  Update configs of name server.
   getBrokerConfig      Get broker config by cluster or special broker!
   queryCq              Query cq command.
   sendMessage          Send a message
   consumeMessage       Consume message

See 'mqadmin help <command>' for more information on a specific command.
```



##  手动创建TOPIC


```
./mqadmin updateTopic -n localhost:9876  -b localhost:10911  -t tx-mq-TOPIC



```
**或者**

```
bash  mqadmin updateTopic -n localhost:9876  -b localhost:10911  -t tx-mq-TOPIC
```



