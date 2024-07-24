# 快速开始

1. Maven项目导入该依赖。

   ```xml
   <dependency>
       <groupId>io.github.zwzrt</groupId>
       <artifactId>message-plus</artifactId>
       <version>0.1.1-beta</version>
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
   public interface MessagePlusBase {
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
        * @param message 消息对象
        * @return 是否允许发送消息
        */
       public boolean onMessageCheck(HttpServerRequest request, Message message);
       /**
        * 收到系统消息
        * @param senderId 发送者ID
        * @param message 消息内容
        */
       public void onMessageBySystem(String senderId, String message);
   }
   ```
