# PayPal推行InnerSource案例分析

***出自“Adopting InnerSource”***

1. 背景

   - 2014年，PayPal雇佣开源狂热分子Danese Cooper，致力于开发PayPal的开源战略。
   - 2015年，Danese在PayPal内部开始宣传InnerSource
     - 使用GitHub企业版实现代码透明化
     - 少数团队有跨团队协作的需求
   - 公司内部的工程文化还是围绕代码所有权（ownership ）, 认为团队外的开发者不具备对本团队代码进行修改的资格。

2. InnerSource 在PayPal代表什么

   - 鼓励使用Pull request代替feature request。
   - 审核代码并对需要修改的代码提供意见的Trusted Committers。
   - 由可以被存档和搜索的书写式沟通代替言语沟通。
   - 适当的外在奖励，以克服沉默，启动协作工作。

3. CheckOut 实验

   - CheckOut团队是PayPal的最繁忙的核心团队，由25名开发者。
   - PayPal收购的新公司（团队）习惯于使用Pull request
   - CheckOut团队面临更大的需求开发和交付压力，因此转向InnerSource
     - 采用GitHub Enterprise 公开代码
     - 识10%的开发者作为Trusted Committers
     - 申请CTO对实验时间的支持
   - 效果
     - 工作量从65%降到5%
     - 代码质量提升
     - 记录下来的讨论帮助开发者更清楚该如何模块化
     - 识别团队外部适合成为Trusted Committers的开发者，进而分担审核压力
     - 大家对这种开发方式都很满意
   - 终止原因
     - 过渡强调了“Engineer to Engineer ”的工作流，忽视了产品管理负责人(PMO)的角色。
     - 产品管理负责人在之前的开发流程中负责指派并追踪任务，并认为这种方式最高效的。

4. Onboarding 实验

   - Onboarding指PayPal签订新客户的过程。
   - 与客户的第一次交互，要求易于理解且不引起摩擦。
   - 按照不同地区进行裁剪是避免摩擦产生的方法，但低效。
   - 区域销售工程师（RSE）开始希望直接参与调整他们所在地区的Onboarding体验，通过编写代码来实现定制的功能，而不是等待其他人编写代码。
   - 为潜在RSEs举行一次性集中培训，让他们快速了解Onboarding架构和代码库。
     - 两周时间
     - 口头进行
     - 成本较大
   - 突出了使用可存档和查找的书写式沟通的重要性和必要性
     - 一次性投入多次受益

5. 执行保护罩（Executive Air Cover ）

   - InnerSource仅能取得非常有限的成功的原因：
     - 按进度完成任务的压力
     - 大家认为InnerSource不能实现或者价值并没有投入的成本大
   - 需要一个更高层面的执行层的保护来允许 InnerSource以一种更科学的方式进行试验，PayPal’s CTO 
     - 挑选核心适合InnerSource的代码库：Symphony 
     - 保障协作
     - 允许对InnerSource的效应进行一个长期的研究

6. 印度InnerSource团队

   - 培训Trusted Committers和外部团队的开发者
   - 因为跨时区，所以进行书写式沟通

7. Symphony 实验

   - 培训
     - *Introduction to InnerSource* 
     -  *The* *Role of the Contributor* 
     - *Trusted Committership* 
     - *InnerSource for Product Managers* 

   - Contributing.md 文件

     ![image-20200813194541076](/Users/amy/Library/Application Support/typora-user-images/image-20200813194541076.png)

   - Check-Ins 的节奏

     - 15-minute check-ins 
     - 识别推行InnerSource的潜在问题
       - 试图优化的伪内源推进过程
       - 员工流动，保留人员
       - 报告工作量的量度
       - 需求调度的困难
       - 打回贡献

8. InnerSource的节奏

   - 通过指导过程生成有用的文档，无需额外努力
   - 产品所有团队对其软件复杂性的新见解，以及将其模块化
   - 识别和培训远程人才
   - 开发人员的满意度是最重要的

9. InnerSource在PayPal的未来

   - 经验总结
     - 同行的支持和培训是相当重要的
     - 定期的自查可以帮助InnerSouce推行走在正确的轨道上
     - 量度很重要
     - 扩展InnerSource需要规划
   - 小战术
     - 以“双赢”的心态迎接InnerSource
     - 跟产品拥有团队打交道的时候要耐心
     - Pull request被合并后重新构建基础
     - 清楚并适应发布周期
   - Q & A
     - Q: InnerSource能在最初有很多阻力的情况下推行吗？
     - A：是的，但这需要认真的培训、管理层的支持，以及及时努力，在克服挫折的过程中消除InnerSource淡化现象。
     - Q: 像敏捷这样的内部资源可以和其他的计划一起工作吗？
     - A: 对！与敏捷相协调的唯一问题是，标准的敏捷建议在物理上共同部署团队往往会导致太多的知识口头传递。地理位置不同的团队倾向于建立更好的文档，这是异步编写通信模式的结果。
     - Q: 什么样的培训或辅导最有效？
     - A: 面对面培训仍然是最有效的，但它不可扩展。在线培训更优。
     - Q: 什么样的外在奖励能最好地克服沉默？
     - A: 对Paypal来说，开明的自我利益是最好的动力。找到将加强合作与职业发展联系起来的方法，将是继续将内部资源作为一种方法的关键。
     - Q: 最有用的指标是什么？
     - A: 既然你是你所衡量的，你就要确保你在追踪那些强化你想要鼓励的关键行为的指标。现在，InnerSource在PayPal内部的工作方式已经得到了更好的理解，一个度量套件正在开发中。它着重于计算有效的协作、指导、质量的提高和速度的提高，这是由于以指导/代码评审建议的形式增加了可操作的文档。
     - Q: 成功的内部资源会遇到哪些文化障碍？我们将如何减轻这些障碍？
     - A: 随着本章中所遇到和描述的各种挑战的缓解措施，很明显，将内部资源整合到具有一定历史和明确定义的文化的复杂组织中需要勤奋、耐心和技巧。但正是这些品质也让这项工作获得了回报。

   