# InnerSource 协作的度量评估方案

> 相比传统的软件开发方式，如目标驱动和敏捷开发，InnerSource，即内源，的一大优势就是打破知识壁垒，促进团队间的协作。为了更好的理解并评估推行InnerSource后开发团队在协作方面的变化，我们需要寻找合适的度量方法并制定合理的评估方案。
>
> > Capraro等人（一个德国的InnerSource研究团队）发表在Mining Software Repositories 2018上的文章“[The patch-flow method for measuring inner source collaboration](https://www.researchgate.net/profile/Michael_Dorner/publication/326562219_The_patch-flow_method_for_measuring_inner_source_collaboration/links/5b83fb8f92851c1e1235980e/The-patch-flow-method-for-measuring-inner-source-collaboration.pdf)”中提出了一种基于Patch Flow度量InnerSource协作的方法。文中将Patch定义为外部开发者对项目提交的代码贡献，如下图所示。组织单元会随着不同公司组织结构以及实施内源的项目所属团队有所变化。
> >
> > <img src="https://github.com/noname2018/Internship2020/blob/master/Output/Week5/figur/patch flow.png" width="50%">
>
> > 公司内部一般都会有明确的组织部分划分。Capraro等人在度量内源协作时也将公司的组织结构考虑进来，其方法可以对不同粒度上的内源协作进行度量。下图是在分别是在粗粒度和细粒度展示内源协作。构建不同的Patch流图允许实践者和管理者可以分析公司不同等级的团队间的内源协作。 
> >
> > <img src="https://github.com/noname2018/Internship2020/blob/master/Output/Week5/figur/lidu.png" width="80%">
>
> ​	*上图出自“The patch-flow method for measuring inner source collaboration”*
>
> 受该文章的启发，本方案将开发者以及开发团队基于代码变更的交互以图的方式进行表示，再借鉴图论里面的经典量度对开发团队和个体开发者在推行InnerSource过程中的协作进行度量。

1. 数据准备
   - 提取组织结构信息：这部分信息可以通过查找公司官网和其他可信在线文档以及调研公司内部的知情员工。可能的组织结构如下图所示。这一部分仅需要收集拟分析的参与内源项目的组织单元的信息。
   
     <img src="https://github.com/noname2018/Internship2020/blob/master/Output/Week5/figure/organization.png" alt="avatar" style="zoom:100%;" />
   
     *上图出自“The patch-flow method for measuring inner source collaboration”*
   
   - 提取代码贡献：对于使用分布式版本控制系统的团队，代码贡献就是Commit。
   
   - 识别代码贡献者的身份信息：根据以往研究，开发者习惯于在git和GitHub或者GitLab上使用不同的帐户。因此我们需要对这部分数据进行预处理，推荐使用Audris Mockus团队在2019年发表在ESEM期刊上的文章[2]中介绍的方法。该方法应该是目前最先进的，具体细节如下图所示：
   
     <img src="https://github.com/noname2018/Internship2020/blob/master/Output/Week5/figure/merge identities.png" alt="avatar" style="zoom:100%;" />
   
     *上图出自“ALFAA: Active Learning Fingerprint based Anti-Aliasing for correcting developer identity errors in version control systems”*
   
   - 将代码贡献和InnerSource项目相匹配。
   
   - 将代码贡献者和所属的组织单元相匹配：这部分信息需要对开发者的隶属关系又一个清楚的了解。
   
   - 将InnerSource项目和所属的组织单元相匹配：获取组织结构信息后，这一环节的匹配比较简单。
   
2. 实验方法
   
   > 我们使用社交网络分析（Social Network Analysis）对公司内源团队在开发过程中发生的协作进行可视化。
   
   - 我们的粒度按照公司的组织结构由低到高依次进行。
   
   - 节点与节点之间的边表示Patch流，由Commit所有者指向代码接收方。边的权重代表Commit的个数。
   
   - 不同于Capraro等人仅考虑跨团队的Patch流，对任一内源项目，我们将团队内开发者对其做贡献也量化在社交网络图中。因为通过对比团队内Patch流（不协作）和团队间Patch流也可以作为项目内源化的一个度量，如下图所示。
   
     <img src="https://github.com/noname2018/Internship2020/blob/master/Output/Week5/figure/commit-net.png" width="50%">
   
   - 个体开发者协作可视化：
   - 推荐使用[Gephi](https://gephi.org)软件对内源协作的社交网络进行可视化展示。
   
   > 我们使用社交网络分析（Social Network Analysis）对公司内源团队的开发者在内源式开发过程中发生的协作进行可视化。开发者与开发者之间的协作在内源项目开发过程中主要体现在代码审核、mentoring、以及issue和mailinglist中的讨论。因此我们需要收集并预处理这几个方面的数据（下面以代码审核为例）。 
   
   - 每一个节点代表一个开发者。
   
   - 节点与节点之间的边代表代码审核(code review)活动，由代码被审核者指向审核者，权重代表审核次数。
   
   - 属于同一个团队（可以是想要观察的组织粒度）的开发者用同一颜色表示，如下图所示。
   
     <img src="https://github.com/noname2018/Internship2020/blob/master/Output/Week5/figure/review-net.png" width="60%">
   
3. 评估指标

   - 团队
     - 协作贡献活跃度：所观察团队的开发者向其他团队的内源项目做贡献的活跃度。该量度可以比较团队参与内源项目主动进行协作的活跃度，进而识别那些不愿意参与其他内源项目的团队。
     - 协作贡献接收度：所观察团队的开发者接收来自其他团队向其所拥有的内源项目做贡献的接收度。该量度可以比较团队所拥有的内源项目对其他团队的吸引力，进而甄别出那些不太受欢迎的内源项目进行调整。
     - 协作亲密度：不同的团队两两之间对各自内源项目做贡献的程度。由于组织关系、企业文化、以及部门功能划分等，不同团队之间的协作力度是不一样的。我们可以通过协作亲密度识别到在内源推进过程中协作紧密的团队，并探究促成这种紧密协作的原因，并进一步在其他团队间进行推广。

   - 内源项目
     - 内源率：可以通过外部贡献比上总接收的贡献进行刻画。该量度可以定位内源推行后依然没有打破部门墙的项目，方便管理者进行分析和调控。
   - 社区发现
     - 社区：社交网络图的一个子集，它形成了一个独立的、连贯的子网络， 可以用基于modularity的社区划分获得。社区内应该有很多边缘，而社区之间的边缘应该更少。所识别到的社区代表在内源项目开发中协作关系密切的团队。

   - 中心性：并非所有节点的创建都是相等的。有些节点在网络中扮演着一个巨大的角色，要么通过拥有许多连接，要么通过战略定位帮助连接网络的远程部分。事实上，节点的重要性和影响力有很多种方式。在我们的分析中，我们将重点放在五个不同的中心性度量上，每个度量捕获不同的动态。这些中心性指标已被广泛应用于社会学、经济学、计算机科学等各个领域。没有一个绝对正确的中心性参数。与其他数据科学技术一样，必须根据我们在基础领域的专家知识来解释这些量。
     - 中心度(Degree Centrality)：一个节点的中心度是连接到它的节点数目，也就是与该节点至少有一次交互的节点的数量。
     - 加权中心度(Weighted Degree Centrality) ：与节点关联的边的权重之和，是节点的交互总数。
     - 特征中心度(Eigenvector Centrality)：这是带有反馈回路的加权中心度。与“重要”的人建立联系也会让你变得更重要。在这个尺度上，你因为认识一个重要的人而得到充分的赞扬，即使你不太了解他们。理论上这可以衡量你的网络有多强大，不管你是否在充分利用你的网络。
     - PageRank 中心度(PageRank Centrality)：这是另一个带有反馈循环的加权中心度。这一次，你只得到你的“公平份额”的相邻节点的重要性。也就是说，你的相邻节点的重要性在他们的邻居之间被分割开来，这和你与邻居的互动次数成正比。从直观上讲，pagerank可以捕捉到您利用网络联系人的效率。在我们的小说中，pagerank中心度很好地捕捉到了叙述的节奏。事实上，当两个重要角色相互作用时，情节就会发生很大的发展。
     - 中间中心度(Betweenness Centrality)：中间中心度标识了在网络中起战略作用的节点，这意味着信息通常会通过该节点传播。这种中间位置给了那个人权力和影响力。中间中心度是经过给定节点的短路径数的原始计数。例如，如果一个节点位于两个大型社区之间的瓶颈上，那么它将具有很高的中间性。

4. 后续可以增强的地方

   - 更细的协作粒度：开发者提交的commit所花费的时间和精力是不同的。不同类型的Commit对于内源项目的作用也是不同的。我们可以通过基于规则或者自动化工具对Commit的类型进行划分，如Feature，Bug Fixing，Testing，Documentation, Code Style, Refactor等。然后在此基础再按照上面的量化方案对参与内源的团队和开发者的协作进行量度和评估。
   - 更多的数据源：内源软件开发过程中会产生丰富的数据，如commit, code review, pull request, issue, 以及mailinglist discussion等，这些数据的应用都会丰富我们刻画内源协作。

参考文献：

1. Capraro Maximilian, Michael Dorner, and Dirk Riehle. "The patch-flow method for measuring inner source collaboration." 2018 IEEE/ACM 15th International Conference on Mining Software Repositories (MSR). IEEE, 2018.
2. Sadika Amreen, Audris Mockus, Russell Zaretzki, Christopher Bogart, and Yuxia Zhang. 2020. ALFAA: Active Learning Fingerprint based Anti-Aliasing for correcting developer identity errors in version control systems. Empirical Software Engineering (03 Jan 2020). https://doi.org/10.1007/s10664-019-09786-7 

