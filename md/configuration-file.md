# 配置文件

1. 如果想要使用持久化功能（提前需要你的项目具有Redis），可以配置如下来打开：

   ```yml
   messageplus:
     serviceId: ... # 服务ID，需要唯一，为空时会自动生成
     persistence: true # 开启持久化
     message:
     	message-persistence: true # 消息持久化（默认开启，需要开启persistence才可以生效）
     	expiration-time: -1 # 消息持久化的过期时间
     	concurrent-number: 1 # 并发量
   ```
