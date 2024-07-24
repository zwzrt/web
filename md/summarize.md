<img src="../logo2.png" align="center" alt="logo"/>

# 消息增强器（message-plus）

---

#### 介绍

基于WebSocket的消息增强器，支持单发、群发及系统功能；支持集群架构的服务架构，以及数据持久化（持久化基于Redis实现，使用中请开发者注意Redis的持久化配置或重新去数据库做持久化）；支持失败消息的持久化及重发功能。

#### 软件架构
Maven + SpringBoot + WebSocket + Redis

#### xxxxxxxxxx /** * 发送单发类消息 * @param receiverId 用户ID * @param msg 消息体 */@PostMapping("/messageplus/send/single")void sendSingleMessage(@RequestParam("id1") String myId, @RequestParam("id2") String receiverId, @RequestBody Object msg);/** * 发送群发类消息 * @param groupId 群组ID * @param msg 消息体 */@PostMapping("/messageplus/send/mass")void sendMassMessage(@RequestParam("id1") String senderId, @RequestParam("id2") String groupId, @RequestBody Object msg);/** * 发送系统类消息 * @param msg 消息体 */@PostMapping("/messageplus/send/system")void sendSystemMessage(@RequestParam("id1") String myId, @RequestBody Object msg);java

[Gitee](https://gitee.com/modmb/message-plus)

[GitHub](https://github.com/zwzrt/message-plus)

#### 使用说明

1.  如果你想要测试一下，可以去我的仓库中的message-plus-text拉取代码来测试。(https://github.com/zwzrt/message-plus-test.git、 https://gitee.com/modmb/message-plus-test.git)
2.  如果使用过程出现bug或者存在不足，可以向red_coral20240606@163.com发送邮箱，我们将会积极修复并提供更强大的功能。
