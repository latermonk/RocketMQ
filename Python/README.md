#  rocketmq-client-python
[https://github.com/apache/rocketmq-client-python](https://github.com/apache/rocketmq-client-python)




## Install `librocketmq`

##  Install rocketmq-client-python

```
pip install rocketmq-client-python
```
##  Samples test

### Producer

```
from rocketmq.client import Producer, Message

producer = Producer('PID-XXX')
producer.set_name_server_address('127.0.0.1:9876')
producer.start()

msg = Message('YOUR-TOPIC')
msg.set_keys('XXX')
msg.set_tags('XXX')
msg.set_body('XXXX')
ret = producer.send_sync(msg)
print(ret.status, ret.msg_id, ret.offset)
producer.shutdown()
```


### PushConsumer


```
import time

from rocketmq.client import PushConsumer, ConsumeStatus


def callback(msg):
    print(msg.id, msg.body)
    return ConsumeStatus.CONSUME_SUCCESS


consumer = PushConsumer('CID_XXX')
consumer.set_name_server_address('127.0.0.1:9876')
consumer.subscribe('YOUR-TOPIC', callback)
consumer.start()

while True:
    time.sleep(3600)

consumer.shutdown()
```

