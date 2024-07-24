# 前端接口

### 1、连接后端

使用WebSocket进行连接：

```javascript
var websocket = new WebSocket("ws://localhost:8081/messageplus/ws/"+id);
```

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

### 3、返回值

服务器返回的值为如下类型的JSON字符串，前端开发者可以使用JSON.parse()来转换为对象：

```java
{
    "code": "200", // 消息编码
    "type": "", // 消息类型
    "senderId": "", // 发送者ID
    "groupId: "", // 群组ID
    "receiverId": "", // 接收者ID
    "data": "" // 消息内容
}
```

消息类型有:

```java
SINGLE_SHOT, // 单发
MASS_SHOT, // 群发
SYSTEM_SHOT // 系统
```

