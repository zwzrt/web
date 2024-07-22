# 快速开始

1. Maven项目导入该依赖。

   ```xml
   <dependency>
       <groupId>io.github.zwzrt</groupId>
       <artifactId>message-plus</artifactId>
       <version>0.0.62-beta</version>
   </dependency>
   ```

2. 启动类添加@EnableMessagePlus来启动增强器。

   ```java
   @SpringBootApplication
   @EnableMessagePlus // 开启message增强
   public class ChatTestApplication {
       public static void main(String[] args) {
           SpringApplication.run(ChatTestApplication.class, args);
       }
   }
   ```

3. 实现MessagePlusBase接口

   ```java
   /**
    * 消息接收实现类
    * @author mo
    **/
   @Service
   public class MyMessagePlusBase implements MessagePlusBase {
       /**
        * 连接建立成功调用的方法
        * @return 有返回，则使用返回值作为标识，否则使用sid作为标识
        */
       public String onOpen(Session session, String sid);
       /**
        * 连接关闭调用的方法
        */
       public void onClose(String sid);
       /**
        * 收到消息时的权限校验
        * @param request HTTP请求信息
        * @param sendId 发生者ID
        * @return 是否允许发送消息
        */
       public boolean onMessageCheck(HttpServerRequest request, String sendId);
       /**
        * 收到系统类型的消息后调用的方法
        * @param senderId 发送者ID
        */
       public void onMessageBySystem(String senderId, Object message);
       /**
        * 收到收件箱的单发消息
        * @param senderId 发送者ID
        * @param receiverId 接收者ID
        * @return 是否成功
        */
       public boolean onMessageByInboxAndSingle(String senderId, String receiverId, Object message);
       /**
        * 收到收件箱的群发消息
        * @param senderId 发送者ID
        * @param groupId 群组ID
        * @param receiverId 接收者ID
        * @return 是否成功
        */
       public boolean onMessageByInboxAndByMass(String senderId, String groupId, String receiverId, Object message);
       /**
        * 处理过程中发生错误
        */
       public void onError(Session session, Throwable error);
   }
   ```

4. 使用MessagePlusUtils工具类来单发消息或者群发消息。

5. 在当前版本即时没有开启持久化的情况下也不在需要去调用MessagePlusUtils.createGroup(createUserId,  name,  client_ids)来创建、导入群组，你只需要实现GroupInterface接口即可（需要被Bean容器管理）。

6. 如果想要使用持久化功能（提前需要你的项目具有Redis），可以配置如下来打开：

   ```yml
   messageplus:
     serviceId: ... # 服务ID，需要唯一，为空时会自动生成
     persistence: true # 开启持久化
     message:
     	message-persistence: true # 消息持久化（默认开启，需要开启persistence才可以生效）
     	expiration-time: -1 # 消息持久化的过期时间
   ```
