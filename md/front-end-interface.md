# 前端接口

### 1、连接后端

使用WebSocket进行连接：

```javascript
var websocket = new WebSocket("ws://localhost:8081/messageplus/ws/"+id);
```

其中的"localhost:8081"切换为自己的地址，ID为用户的标识符。

插件增强器会先调用开发者实现的onOpen()方法，使用该方法返回的ID作为最终标识符。

### 2、发送请求

```java
/**
 * 发送单发类消息
 * @param receiverId 用户ID
 * @param msg 消息体
 */
@PostMapping("/messageplus/send/single")
void sendSingleMessage(@RequestParam("id1") String myId, @RequestParam("id2") String receiverId, @RequestBody Object msg);
/**
 * 发送群发类消息
 * @param groupId 群组ID
 * @param msg 消息体
 */
@PostMapping("/messageplus/send/mass")
void sendMassMessage(@RequestParam("id1") String senderId, @RequestParam("id2") String groupId, @RequestBody Object msg);
/**
 * 发送系统类消息
 * @param msg 消息体
 */
@PostMapping("/messageplus/send/system")
void sendSystemMessage(@RequestParam("id1") String myId, @RequestBody Object msg);
```
