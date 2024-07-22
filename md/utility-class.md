# MessagePlusUtils工具类

该工具类非常重要，开发者对消息增强器的操作几乎都来自这里：

```java
/**
 * 消息增强器工具类
 * @author mo
 **/
public class MessagePlusUtils {
    /**
     * 给指定用户发送消息
     */
    public static boolean sendMessage(String id, String msg);
    /**
     * 创建群组（主要用于主动创建群组，若实现了二级查询接口，则无需调用此接口）
     * @param createUserId 创建者ID
     * @param name 群组名称
     * @param client_ids 群成员ID
     * @return 群组ID
     */
    public static Group createGroup(String createUserId, String name, List<String> client_ids);
    /**
     * 加入群组
     * @param userId 用户ID
     * @param session 用户session（为空则代表不在线）
     * @param groupId 群组ID
     */
    public static int joinGroup(String userId, Session session, String groupId);
    /**
     * 群发（包括自己）
     * @param groupId 群组ID
     * @param message 消息内容
     * @return 失败用户ID
     */
    public static List<String> sendMessageToGroup(String groupId, String message);
    /**
     * 群发（不包括自己）
     * @param userId 用户ID
     * @param groupId 群组ID
     * @param message 消息内容
     * @return 失败用户ID
     */
    public static List<String> sendMessageToGroupBarringMe(String userId, String groupId, String message);
    /**
     * 获取总在线人数
     */
    public static Long getOnLinePeopleNum();
    /**
     * 获取对应ID群组
     */
    public static Group getGroupById(String groupId);
    /**
     * 获取指定ID的session
     */
    public static Session getSessionByClientId(String clientId);
    /**
     * 用户是否在线
     * @param userId 用户ID
     * @return "0"-本地在线 "-1"-不在线 "服务器ID"-其它服务器在线
     */
    public static String isOnLine(String userId);
    /**
     * 查询指定用户的未接收消息（该方法主要用于集群架构中跨服务使用，框架自己调用，开发者一般不需要）
     * @param userId 用户ID
     */
    public static List<Message> getNewMessage(String userId);
	/**
     * 提示指定用户存在新消息（该方法主要用于集群架构中跨服务使用，框架自己调用，开发者一般不需要）
     * @param userId 用户ID
     */
    public static void hasNewMessage(String userId);
}
```

