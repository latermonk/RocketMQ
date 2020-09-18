# RocketMQ

## 官网：
https://rocketmq.apache.org/  

##  中文文档
https://github.com/apache/rocketmq/tree/master/docs/cn



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

