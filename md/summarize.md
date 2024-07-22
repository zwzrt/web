# 消息增强器（message-plus）

---

#### 介绍

基于WebSocket的消息增强器，支持单发、群发及系统功能；支持集群架构的服务架构，以及数据持久化（持久化基于Redis实现，使用中请开发者注意Redis的持久化配置或重新去数据库做持久化）；支持失败消息的持久化及重发功能。

#### 软件架构
Maven + SpringBoot + WebSocket + Redis

#### 下载项目

[Gitee](https://gitee.com/modmb/message-plus)

[GitHub](https://github.com/zwzrt/message-plus)

#### 使用说明

1.  如果你想要测试一下，可以去我的仓库中的message-plus-text拉取代码来测试。(https://github.com/zwzrt/message-plus-test.git、 https://gitee.com/modmb/message-plus-test.git)
2.  如果使用过程出现bug或者存在不足，可以向red_coral20240606@163.com发送邮箱，我们将会积极修复并提供更强大的功能。
3.  在大流量的情况下，可能出现同时调用一个session导致的写冲突，引发异常。

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request

#### 特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  Gitee 官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解 Gitee 上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是 Gitee 最有价值开源项目，是综合评定出的优秀开源项目
5.  Gitee 官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  Gitee 封面人物是一档用来展示 Gitee 会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
