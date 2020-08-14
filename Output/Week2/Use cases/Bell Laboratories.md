# Bell Laboratories 推行InnerSource案例分析

***出自“Adopting InnerSource”***

1. 声音沟通的网络协议背景
   - 1993年3月，IETF发布一种多媒体信号协议，Session Initiation Protocol (SIP) ，获得快速发展。
   - SIP从最初设计为轻量级点对点会合协议将随着时间的推移演变为支持电信服务集中控制的电信级协议。
   - SIP对于企业的多个部门都很关键，都参与进来，形成企业InnerSource。
2. SIP背景

> SIP是一种多媒体信号协议。它的工作是通过在SIP网络上路由SIP请求来找到与之建立多媒体会话的目标接收者。

- *SIP user agents (UAs)* ：SIP端点，是用户与之交互以建立会话、接收传入会话的通知或关闭现有会话的构件。SIP用户代理的示例是移动电话和VoIP应用程序。

- *SIP registrar* ：一个网络服务器，它存储SIP URI和相应接收方UA的IP地址的映射。
- *SIP proxy* ：帮助路由SIP消息的网络服务器。
- *SIP redirect server* ：将传入的会话请求重定向到一组备用uri。
- *SIP back-to-back user agent (B2BUA)* ：是UA客户端（可以发起会话请求）和UA服务器（可以接受、拒绝或重定向会话请求）之间的一个连接。

3. Common SIP Stack (CSS) 项目

> Bell Lab的 SIP项目从1998-2006，持续了八年，经历了三个阶段。

- Phase 1 (1998–2000): The Foundational Years 
  - 探索SIP与其他传统电信基础设施的交互
  - 随着2000年SIP被迅速接受，Vijay开始考虑在公司内部广泛共享SIP代码。
    - 管理层总体上支持开源，包括需要共享代码库。
    - 随着SIP成为3GPP中的强制性信令协议，它成为公司销售的各种产品（当时是朗讯科技）的核心。
- Phase 2 (2001–2003): Opportunistic Partnering 
  - 代码从以下三种方式中受益：
    - *Linus’s 法则* ：越多人看到代码，缺陷越少（代码质量提高）
    - *专家的贡献*：来自不同部门的人提供宝贵的贡献
    - *增强了代码在不同平台上的可移植性*：这些代码被移植到Linux和Solaris之外的其他平台上；例如，开发人员将代码移植到Windows操作系统上，并将更改贡献给上游。
  - 3GPP批准SIP作为强制性信令协议，促使各业务部门寻求SIP协议栈来构建他们的产品。
  - 出现来自产品组的正式更改请求。
- Phase 3 (2004–2006): Corporate Open Source 
  - Common SIP Stack group
    - 维护一个独立的、通用的源代码库，这样所有的项目都可以从CSS获得它们的可交付成果。
    - 通过在公司内部建立对资源的认识，宣传技术和实施。 
  - 核心团队
  - 成长的社区

4. 思考，见解，和讨论
   - 广告和鼓励
     - 首席架构师和产品经理应该始终站在最前面，以确保公共资产在公司内部广为人知。
     - 需要一种自上而下的方法来帮助促进公共资产的使用。
   - 尖端技术
   - 基础项目