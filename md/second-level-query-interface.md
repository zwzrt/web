# 二级查询接口

该接口的实现是为了让开发者无需在服务器重启或者消息增强器在Redis中的数据丢失后，重新进行群组信息的初始化。

开发者实现该接口后，当消息增强器无法找到对应的群组信息时，会调用这个接口。开发者可以返回自己存储的群组信息。

```java
/**
 * 查询群组二级接口类
 **/
public interface GroupInterface {
    /**
     * 开发者自定义的群组查询接口（二级）
     * @param groupId 群组ID
     * @return 群组
     */
    Group getGroupInCustom(String groupId);
}
```

当然，该接口的返回值为消息增强器定义的群组类，开发者可以调用以下方法来创建群组对象：

```java
/**
 * 创建群组
 * @param id 群组ID
 * @param createUserId 创建者ID
 * @param groupName 群组名称
 * @param clientIdList 成员ID（无需携带创建者ID）
 * @return 群组
 */
Group BuildGroup(String id, String createUserId, String groupName, List<String> clientIdList);
```

该方法可以通过Group.BuildGroup()调用。
