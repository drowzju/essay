

---

## 今天我们讨论的话题

- 软件开发应用 AI，从个人到组织，应该有哪些关键工作？流程建设重点和工作重心？
- 软研应用 AI，今天有哪些问题？
- 结合业界的思想和我们遇到的问题，如何评估我们的组织级 AI 应用能力？
- 我们后续的行动是什么？我们如何定义我们的技术要求？我们如何定义我们的建设方向？我们如何评估 AI 产出的质量？我们如何度量我们的效能水平？我们如何改变我们的组织，等等。

---

## AI 软件工程业界趋势和体系

### 现状：组织提效不显性，稳定性下降
当前，AI 辅助编码在开发者个体层面带来了显著的体感提升，但组织层面的整体提效却普遍面临瓶颈。这一现象在业界被称为 **Vibe Coding 生产力悖论**：Agent 代码生成速度呈指数级增长，但组织整体交付效率并未同步跃升。

历史上关于单点技术进步但因为组织方式不匹配而整体效率提升不明显的例子：
	The three evolutions of the Lowell Textile Mills. From left to right: the 1890 steam engine-powered mill, the 1900 electrical engine-powered mill, and finally the 1920 "unit drive" mill i.e. a ground up rebuild as an electrical assembly line.

![[Pasted image 20260613233945.png|697]]

DORA报告指出，开发者越来越信任AI:
![[Pasted image 20260613234114.png]]
个人效能提升显著高于组织绩效提升，同时AI也提升了交付的不稳定性：

![[Pasted image 20260613234054.png]]
当前AI对软件工程的影响呈现出典型的“局部加速—系统失配”，表现为个体提效明显，但组织收益不显性，同时代码产出加快但系统稳定性下降。

### 一、组织提效不显性的原因

AI主要提升的是编码与调试等**执行层环节效率**，但软件交付的瓶颈在需求澄清、架构设计、评审、测试、发布与跨团队协作等**系统性流程**，这些未被同步优化，导致整体仍受“最慢环节”约束。

更深层原因在于三类结构性错配：

- **流程错配**：编码提速但评审、联调、测试、现场交付调试，形成新的瓶颈。
- **上下文缺失**：缺乏统一企业级私有上下文与知识体系，AI只能局部优化，难以形成组织级协同收益。
- **认知陷阱（关键补充）**：AI接管“执行层认知”后，开发者往往将释放出的时间继续投入代码生产，而非提升“设计层认知”（架构、抽象、系统设计），导致组织没有发生认知升级，只发生产能放大，从而使复杂度增长快于能力增长。

因此，约15%-35%的个体提效容易停留在局部，而无法转化为组织级端到端效率提升。

（今年软研启动会上我曾经引用过一个案例，说明开发者的幻觉，即自己觉得提效明显但实际数据反馈不明显。这个随着大家实践深入应该已经普遍撞过一些墙，这不再是关键问题）

---

### 二、出码变快但稳定性下降的原因

代码产出加速若未配套治理体系，会系统性削弱稳定性：

- **验证税上升（关键补充）**：AI生成代码具有概率性特征，工程师必须额外投入验证与审查成本；部分研究甚至显示其事故率高于普通PR，使“提速收益被验证成本抵消”。
- **局部最优与架构漂移**：AI倾向生成“可运行即可”的局部解法，缺乏全局架构约束，导致技术债累积与系统耦合增强。
- **理解深度下降**：开发者对生成代码的认知下降，形成“可用但不完全理解”，提高后续维护与排障成本。
- **质量体系滞后**：测试、CI/CD与SRE能力未随变更频率扩展，使缺陷更易进入生产环境。

---



### 从 SDLC 到 ADLC 的关注点转移

面对 AI 的冲击，软件开发生命周期正经历从传统 SDLC 向智能体软件开发生命周期（A-SDLC / ADLC）的演进。对比两者，流程方法的强调重点发生了根本性转移，企业需要重点关注以下几个维度：

1. **从"代码编写"到"意图驱动"**：传统 SDLC 以代码为核心资产，而新范式下，意图驱动开发成为主流。人类的核心职责上移至"清晰表达意图"与"验证意图实现度"，执行层交由 Agent 完成。
2. **从"提示词技巧"到"上下文工程"**：上下文工程已被定位为生产必备的基础架构关切，涵盖知识组织、记忆管理与情境适配，彻底取代了单次的 Prompt 调优。
3. **从"人工审查"到"确定性裁判"**：面对概率性软件工程，传统 QA 体系失效。企业必须建立以编译器、自动化测试、基线对比机制为核心的确定性裁判体系，用外部客观验证机制锚定质量，防止 AI 拿"历史遗留"当借口。
4. **角色倒置**：开发者从"手工建造者"转变为"系统监督者"与"逻辑策展人"。

ADLC 将软件交付重构为六个并发阶段（意图→生成→验证→治理→部署→观测），以**并发、治理、赌注、循环、信号**为核心原则，本质是从串行管道走向 Agent 驱动的并发循环系统。

我们要注意：

- ADLC 的方向是如何让 Agent 能更有质量地完成更多的工作；
- 不是把 AI 工具引入了就是 ADLC；
- ADLC 不要强调把人从软件交付中移除。（上次阿里的分享这么讲，我觉得很危险）

更深一层看，个体 10x 不等于组织 10x。前面的1890 年代纺织厂的例子：工厂换上了电动机，但没有重新设计厂房布局和生产流程，导致电气化后 30 年产出几乎零增长——**我们换上了"电动机"，但"工厂"还没有重新设计**。组织级智能不会随个体使用 AI 工具自然涌现，它需要在**协调、信号提取、确定性保障**三个支柱上构建制度体系。这意味着：**流程工程（Process Engineering）** 才是核心——不是编码产品，而是把企业流程编码进 Agent 并推动组织变革管理，其中**领域专业知识比软件专业知识更关键**。目标必须从"节省时间"升维到"规模化价值"——否则"AI 生码率"陷阱不可避免。正如业界所言：问任何 CEO 首要目标是降本还是增收，几乎所有人都会说是收入；但几乎所有 AI 产品都在卖"省时、少人"——这中间的鸿沟，就是组织级能力建设的意义所在。

---

### 务实路径：建立组织级能力基线与渐进式演进

首先，我们须认清当前仍处于**个人普及向组织建设过渡**的阶段。**高生产力个体无法自动组成高生产力组织**。我们的重心已经不该是编码本身，而是**组织运转方式**（Process Engineering）——把企业流程注入到 Agent 并推动变革管理，其中领域专业知识比软件工程专业知识更关键。这意味着必须从"节省时间"升维到"规模化价值"——"AI 生码率"陷阱的根源，正在于用成本削减指标来衡量本该由收入增长驱动的目标。

其次，我们应该积极推动组织和人才的转型，逐步构建新的平台、度量、实践三大智能工程支柱。在度量体系上，必须坚决摒弃"AI 生码率"等过程指标陷阱，转向以"**业务价值 E2E 标准**"和"**有意义修改后接受率（meaningful-modification-acceptance-rate）**"为核心的质量密度指标，引导开发者保持健康的使用行为。

最后，在架构演进上，应采纳渐进式路径，按需引入上下文增强、质量门禁等，避免过早陷入 Agent 模式的复合错误率陷阱。当然，在模型能力达到临界点前，**半自动人机协作（60% 环节使用 AI，核心决策保留人类判断）** 是更具性价比的选择。

---

## 我们目前的问题

---

### 模型能力问题 / 基础环境问题

各开发团队反馈："多模态模型与国外差距较大；模型视觉能力未达预期；跨子系统整体理解能力不足；算力分配不均，白天高峰排队"

各个团队都有提及模型能力问题，尤其是**设计还原度问题**。算力负载/消耗监控手段、混合算力使用的运维运营措施，这些都比较欠缺。

不过，模型和基础算力等方面的问题更多有赖于采购和推动其他部门解决，不是我们本文讨论的重点。各团队可以持续反馈问题给专项项目经理黄宁，我们一起继续来推动。

---

### AI 执行偏离 / QA 手段保障缺失

各开发团队反馈："AI帮倒忙频发，代码缺陷率上升；验证速度跟不上AI执行速度；各环节缺少准入准出标准；人工审查负担随生码量同步上升"

---

#### 现象本质

#####  隐性验证税与角色异化

由于 AI 无法可靠发出不确定信号（即不知道自己"写错"了），工程师被迫对每次交互进行潜在欺骗检查。数据显示，**AI 生成代码的后续返工率较高，事故率比普通 PR 高 23.5%**。这导致开发者从创造性的"制造者（Maker）"沦为疲于奔命的"检查者（Checker）"，认知负荷呈指数级上升，形成沉重的隐性验证税。

#####  AI 生码率陷阱与代码即负债

当组织将"AI 生码率"作为考核指标时，会引发严重的"灌水激励"。团队倾向于让 AI 生成大量单元测试、注释、胶水代码等"容易 AI 生成但价值密度极低"的代码。这违背了**代码即负债**的本质——代码进入生产即产生维护成本，规模化生产代码等于规模化生产负债。

#####  认知债务与架构漂移

在面对复杂存量系统时，AI 往往缺乏全局架构感知，导致"按下葫芦浮起瓢"。这种 AI 管理不善、上下文丢失、Agent 行为不可靠所累积的隐性成本，被称为**认知债务**。它潜伏在交互历史中，一旦爆发就会导致系统级崩溃。

#####  上下文腐烂与模型幻觉

长时运行 Agent 极易遭遇**上下文腐烂（Context Rot）**，表现为持续累积的过时信息、指令膨胀导致的信噪比下降，以及多轮对话后的**意图漂移**。此外，模型幻觉的深层成因之一是**自我欺骗假说**——模型混淆了输入内容与自身生成的内容，导致看似合理但逻辑错误的输出。

---

#### 应对思路

##### 引入确定性裁判
必须将人类审查转化为机器验证。建立以编译器、测试、监控等外部客观验证机制为核心的**确定性裁判**体系。通过 hooks 在代码写入前后及会话结束时强制运行测试，防止 AI 跳过验证步骤，用自动化质量门禁替代人工肉眼 Review。

##### 垃圾回收式技术债务管理
摒弃传统的"集中清理"模式，采用**垃圾回收式技术债务管理**。将"黄金原则"编码入仓库，部署背景 Agent 定期扫描代码偏离情况、做架构走查、更新质量评级，并自动开启定向重构 PR，持续进行小额度自动化重构，防止冗余代码堆积。另外，考核上尽量避免"AI生码率"这种虚荣指标（也是我在研发中心和软研一再反对的，这种指标观察即可）。

##### 基线对比机制与机械强制执行

   - **基线对比机制**：开发前后各跑一次总验证，量化对比指标，客观判定改进或退化，彻底杜绝 AI 拿"历史遗留问题"当借口。
   - **机械强制执行**：通过自定义 linter、结构测试等"品味不变量"，将人类的架构品味编码为机器约束，防止架构漂移。
   - **QA 四块拼图**：构建 `Rule（软约束）→ Skill（标准化动作）→ Scripts（硬门禁）→ 总验证脚本（统一裁判）`的 Harness QA 体系，确保质量收口。

##### 上下文工程与渐进式信息暴露

   - **渐进式信息暴露**：解决上下文稀缺与过载。Agent 从"小而稳定的入口点"（如 `AGENTS.md`）开始，按需深入加载详细信息，而非一次性将全量代码塞入上下文窗口。
   - **上下文工程**：将上下文管理从"战术优化"升级为"基础架构关切"。通过 [[All In Code]] 和 LLM-Wiki 知识库解决上下文碎片化，让 Agent 在完整、结构化的知识供应链中工作，而非依赖零散的 Prompt 拼凑。
   - **[[Ralph Loop]]**：在 AI 循环机制中，每次迭代以全新上下文重启，避免长上下文带来的推理退化与幻觉累积。

---

### 需求和设计质量差

各开发团队反馈："需求边界不清，隐性需求多；上游偏差传递下游，返工成本高；设计评审AI采纳率偏低(0%)；联调周期因设计质量被进一步放大"

---

#### 现象本质

上游差，下游的生成就困难，效果就差。

一个非常大的隐患是——我们软研自己也会承认——过去的开发过程中，有多少是开发前没想清楚的、临到最后一刻发现有方案有疑问的情况？试想如果是让 AI 开发，这些问题不会自动消失，但因为开发者不编码了，没有沉浸的思考过程，可能问题反而不会被暴露，变成隐藏更深的技术债务。

假设上游没有定义某种极端异常分支（比如某存储产品和云存储接口类似但缺少关键容错特性，ICC 按照云存储逻辑对接会有丢数据风险）。人类程序员在写代码时会卡住，从而倒逼产品经理澄清需求或者架构师拉通方案；但 AI 会基于概率，自信地编造一个"看似合理但业务错误"的默认处理逻辑（例如直接返回成功或静默失败）。这段代码能跑通，单元测试也能过，但核心业务逻辑全错。由于 AI 生成代码极快，这种"**方向性垃圾**"会被大规模、快速地转化为生产环境中的**代码即负债**。

过去，程序员在 Review 代码时，大脑中会模拟代码的运行轨迹，很容易发现"这里的设计不符合实际业务场景"。现在，面对 AI 瞬间生成的数百行代码，人类往往只能进行"表面审查"——检查代码是否符合（可能本身就是错的）需求文档、语法是否正确、有没有明显的空指针。更危险的是**去技能化风险**：长期不亲自写复杂逻辑，开发者对系统底层和复杂业务链路的"体感"会衰退。当 AI 生成了一段"符合错误需求"的代码时，人类审查者可能已经丧失了察觉其设计缺陷的敏锐度。

---

#### 应对思路

要解决上游质量差带来的隐患，必须彻底改变 AI 原生开发的工作重心，将防线大幅前移：

1. 在让 AI 写一行代码之前，必须先通过人类的高阶"品味"把核心概念、API 契约和业务边界彻底想清楚。

2. 必须将人类的设计意图、业务约束提炼为机器可强制执行的**声明式架构**。通过编写 `architecture.md` 或 `AGENTS.md`，将"品味"编码为**品味不变量**（如自定义 Linter 规则、结构测试），作为 AI 生成的硬约束，防止 AI 在模糊地带自由发挥。

3. 推行 **All In Code** 和 **LLM-Wiki 知识库**，从源头切断"垃圾进"的可能（具体做法见前述知识工程章节应对）。

4. 开发者必须进化为**编排者/作曲家**。其核心价值不再是检查代码语法，而是**设计系统架构、定义验收标准、以及具备识别"方向性错误"的业务品味**。

---

### 知识工程问题

各开发团队反馈："知识库覆盖不全，更新跟不上迭代；行业知识沉淀不足，垂直匹配度低；关键信息未留存，每次需重新输入；AI缺乏持续记忆，增量开发无继承"

---

#### 现象本质

大华软件平台特有的行业知识对于 AI 是一种障碍。需求中的隐性知识、行业的术语理解对于 AI 是非常困难的。对于我们的存量工程的积累，特别是落在很多经验丰富开发者脑子里的知识（或者技术债务），AI 是无所知的。当前文档/网页比较离散，也缺少面向 AI 的准备。

大华软件平台深耕行业多年，积累了大量特有的行业术语、业务"黑话"以及特定场景下的"潜规则"。这些知识往往没有写在文档里，而是存在于资深开发者的脑子里，或者隐藏在历史代码的"奇技淫巧"（技术债务）中。假设需求中提到"按照行业标准的 XX 协议进行对接"。人类老员工立刻知道这里的"行业标准"特指大华内部针对某类客户魔改过的 V2.3 版本协议，信令、流媒体、智能事件都有各自的特殊要求。但 AI 只能检索到公开的 V1.0 标准协议，从而生成完全无法在真实业务中运行的代码。

当前企业的知识资产极度分散：需求在蜻蜓/TB/Confluence，API 定义在 Swagger/萤火虫，架构讨论在花茶群聊文档，代码在 Git。这种**上下文碎片化**导致 AI 只能看到冰山一角。更致命的是，现有的文档是"**给人看的**"，而不是"**给 AI 看的**"。人类文档中充满了"大家都知道"的省略语、未明说的上下文假设和模糊的自然语言。AI 缺乏人类的"常识脑补"能力，面对这种文档会产生严重的幻觉。

---

#### 应对思路

##### 资产代码化：All In Code 与 LLM-Wiki 知识库
   - 推行 **All In Code**，将需求、设计、API 契约甚至历史决策记录（ADR）全部纳入 Git 版本管理，使 Agent 在完整、统一的上下文中工作。
   - 构建 **LLM-Wiki 知识库**。这不是简单的文档堆砌，而是利用 **write-time-synthesis（摄入时合成）** 技术——在数据摄入阶段，就由 LLM 将离散的文档、代码、讨论记录进行信息整合、去重和结构化，实现"知识复利"。

##### 机器可读化：Agent 可读性与声明式架构
   - 将代码库和文档库优化的首要目标设定为 **agent-legibility（Agent 可读性）**——使代码库和知识库对 Agent 可直接推理、验证、修改。
   - 编写 **architecture.md** 和 **agents.md**。将大华特有的行业术语表、业务边界、架构约束提炼为机器可强制执行的"可执行清单"。例如，在 `agents.md` 中明确规定："当遇到 XX 行业术语时，必须映射到内部 YY 数据模型，严禁使用 ZZ 开源方案"。

##### 知识结构化：场景化知识库与渐进式信息暴露
   - 放弃传统的"陈述性"长篇文档，转向**场景化知识库**——以"场景+决策+约束"的格式存储知识，直接对齐 AI 的推理逻辑。
   - 面对海量的存量工程知识，采用**渐进式信息暴露（Progressive Disclosure）** 策略。为 Agent 提供"小而稳定的入口点"（如系统目录、核心概念索引），Agent 按需深入加载详细文档，而非一次性将几十万行代码和文档塞入上下文窗口导致"上下文腐烂"。

##### 持续维护
   - 知识工程不是一次性工作。前面AI执行偏离的应对已经讲过，部署背景 Agent 定期扫描代码与文档的偏离情况，知识工作应该在这个过程中考虑各种更新和校验机制。

---

### 人员技能提升和资产管理问题

各开发团队反馈："Skill/Agent缺乏统一开发规范；团队能力不足，缺少指导；对于AI时代该具备的能力方向也比较迷茫"



---

#### 现象本质

首先，语言大模型进入软件开发，很大的一个变化是我们的工作交互接口或者说协议上部分转向了“自然语言”和“概率推理生成”。灵活性的另一面就是一种不确定性和模糊性。这种不确定性和模糊性也就意味着定义标准化、规范性的困难。

其次，各个团队的业务压力极大，而确实很多技术是全新的。大家也都是刚拿到算力和工具进行开发。兼顾新技术的培训、新实践的落地需要额外的时间，这必然和当下紧张的任务排期冲突；

最后，行业能看到的实践也往往来自于互联网头部企业，在场景上也有很大的差别，直接照搬是比较困难的。而各团队在业务和技术沉淀上差异也比较大，一时还缺少有效的复用和共享。




---

#### 应对思路

##### 资产化治理
   - 一个优秀的 Skill 必须具备代码级的生命周期管理。它需要有明确的 Owner、版本历史、评估基准（Benchmark）和降级路径。
   - 建立类似代码 PR 的**轻量级 RFC 评审机制**。开发者提交新 Skill 或修改现有 Skill 时，必须通过自动化评估套件的回归测试，才能合入中央 Skill 仓库。构建 Prompt+Skill 的 CI/CD 流水线，支持灰度发布、A/B 实验和快速回滚。
   - 同时，虽然Agent/AI的自然语言交互和概率推理是不确定的，但是我们的质量检查手段可以结合一些硬性标准和固化脚本来应对。

##### 能力培养：本质是"投入分摊方式"问题
   - 这不是态度问题,是结构性的——任何新技术学习都需要前期投入产出比为负的阶段,而KPI/排期通常按短期产出考核,导致个体和团队没有"合法"的时间做这件事,只能"挤"或"不做".
   - **不要做成额外培训**,而是把学习嵌入到真实任务中——每次获得优秀实践，无论是内部的，还是外部的其他团队的，选1-2个真实但非关键路径的任务作为"试点",允许其周期适当放宽,产出包括交付物+可复用的Skill/经验沉淀,把学习成本转化为组织资产的一部分,而非纯消耗。
   - 设立小规模"赋能团队"(即使是兼职、轮岗形式),专门负责沉淀通用Skill、踩坑经验、最佳实践,降低其他团队的重复学习成本——本质是把分散的学习成本集中化、规模化。==软研各团队内部可以明确一些比如上下文工程师，Harness工程师/Loop工程师，飞轮架构师的角色定义，专注于关键资产的沉淀、校验和实践推广==.   （比如把团队里最懂业务、最爱写文档的老员工，赋能转型为**上下文工程师**。架构师们默认应该是上下文工程师；把团队里手最快的，最懂 CI/CD、最痛恨烂代码的 QA/DevOps，转型为 **Harness/Loop 工程师**。把团队里视野最广、关注长期 ROI 的技术专家，赋予**飞轮架构师**的职责。）
   - 部分任务，管理层需要明确给出"允许慢一点"的信号和空间,哪怕只是某个季度某几个项目,否则一线没有动力打破惯性。AI 价值实现不可避免地存在 J 曲线效应。在采用初期，由于学习曲线、**验证税**（审查 AI 代码的额外负担）以及管道适应，组织甚至会经历**约 15% 的生产力下降**，这个"转型学费期"通常**持续约 3 个月**。度过谷底后，才会迎来指数级增长。
   
##### 经验复制不是直接照搬
   - 头部企业的实践(比如某种Agent架构、某套Prompt工程方法论)是在特定场景、数据规模、技术栈下打磨出来的,直接迁移会因为业务场景、数据特点、团队能力错配而失败。但这不代表这些实践没有价值,而是缺少一个"提炼通用原则—结合自身场景再设计"的转译过程。
   - 区分**原则层**和**实现层**:头部实践中可复用的往往是设计原则(如"Agent要有明确的工具边界""复杂任务要拆解为可验证的子步骤""人机协作要有Checkpoint"),而具体实现(用什么框架、什么模型、什么Prompt结构)需要结合自身场景重新设计——这个转译过程本身需要被有意识地组织,而不是指望"拿来就用"
   - 鼓励各团队把自己摸索出的、哪怕是小范围验证的经验(包括失败的)结构化记录下来,形成内部可检索、可对比场景的案例集,这比外部大厂案例更贴近实际可用。不要怕场景小，功能简单，只要能解决问题，积极分享对自己对团队都有价值。我们的慧码社区应该更积极地去聚集案例和反馈
   - 推动**跨团队的小范围复用试验**:不追求一次性建立大一统平台,而是先让1-2个相邻业务的团队互相试用对方沉淀的Skill/Agent,验证可迁移性,再逐步扩大——复用能力本身需要从小范围开始验证和迭代,而不是设计出来的。

---

### 工具和效率度量问题

各开发团队反馈："工具系统多，比较离散;提效数据缺乏统一评估维度；全工程维度提效分析尚缺失；人机协作过程如黑箱，不可见"

---

#### 现象本质

- 开发环节多，工具和系统离散。这是大家可见的。AI 来之前，大华研发工具系统已是很多。AI 来之后，因为工具开发速率在理论上可以无限快，工具似乎会更加繁荣。越来越多的工具和平台到底如何能给开发者一站式体验，如何能给出标准的一致性的度量数据？
- AI 的收益到底有多少？在任何公司，这个问题都非常重要。我们会加很多定语，在 xxx 场景下的 yyy 环节，zzz 情况下达到 N% 的效率提升。而我们大华过去的度量体系恐怕也不能算是业界头部的水平，大家心里也有数。在今天AI进来后，度量体系面临更大挑战，能不能说清楚提效的结果，能不能看清流程的堵点和优化方向，其实也是有挑战。

	必须指出的是，新技术应用会有一个曲线，开始甚至可能会有效率的下降。这是符合客观规律的。
![[Pasted image 20260614104731.png]]
- 当前 AI Coding Agent（如 claude-code、cursor、codex、我们的 codebuddy）在开发者本地运行时，面临着严重的**端侧可观测性盲区**。可观测性其实有两面的问题：1）开发者到底在用Agent做什么？2）Agent到底在做什么，做的怎么样？

---

#### 应对思路

##### 系统的收编和工具共创


- 不追求绝对的"收编/统一工具"(这与工具繁荣趋势相悖,会持续打不完的仗),转向**统一接口层而非统一工具层**——定义一套各工具接入的标准数据/事件协议,工具可以继续百花齐放,但需按统一协议上报关键事件；
- 一站式体验的落点不在"减少工具数量",而在**汇聚层/聚合视图**:在工具之上建一层轻量聚合,让开发者从一个入口感知全局状态,底层工具仍各自独立演进。举个例子，如果开发者用的是codebuddy，我们的慧码作为插件，把所有的rule/skill标准体系、外部系统对接、度量采集内置掉，集成给codebuddy，开发者只感知codebuddy。如果开发者自己做了个工作台，我们的慧码插件被他集成，则在体验有差异之外，一样有一致性的技术规范；
- 该协议应作为新工具/Agent接入的"准入门槛"之一,从源头控制离散度的增长,而非事后治理存量；
- 同时鼓励大家共创工具，开源社区方式推进。但需要HR协助做好激励机制，因为这部分都是在自身业务之外的投入。

另外，必须指出的是，虽然我们大华过去的系统多、工具多，但现在我们反而认为这个问题可以不再显得那么严重了——完全可以快速把这些变成MCP，变成命令行并进一步作为skill为Agent所用。


##### AI时代提效度量体系的系统性阐述

###### 先承认现实分布,再谈统一度量

度量体系若不先承认"提效因场景而异"这一前提,任何统一指标都会沦为各说各话。需建立**场景分层基线**:

- **绿地/简单场景**:提效35%-40%,可作为AI能力上限的参考基准
- **遗留/复杂场景**:受上下文碎片化、技术债拖累,提效约10%,这才是大多数存量项目的真实水平
- 同时也要考虑J曲线（详见前述人员技能章节"能力培养"应对中的分析），转型学费期的效率下降是否在预期之内

意义:后续所有"N%提效"的表述,必须先标注场景类型,否则数字本身无意义、不可比较——这是反馈二"场景标签必须标准化"的具体内容来源。


###### 最小公共指标集需要纳入"协作模式"维度

当前务实状态是"60%环节用AI、完全委托Agent仅0%-20%"（详见前述"务实路径"章节），半自动协作是主流且更具性价比。这意味着反馈二中的最小公共指标集,不能只衡量"AI做了多少",还要衡量**协作结构本身**:

新增指标维度:

- **AI参与度**(环节占比,而非任务占比)
- **人工介入深度**(修正/补充上下文的工作量)

意义:防止度量体系隐含"全自动=更好"的错误导向,从数据层面支持"半自动模式比盲目全自动更具性价比"的判断,同避免"用节省时间生产更多垃圾代码"的认知陷阱——这一点直接呼应了反馈二中"效率指标必须与质量指标联动"的要求,且给出了具体的联动方式。

###### 质量指标必须显性扣除"验证税"

基于前述"AI 执行偏离"章节的现象分析，这里给出度量层面的量化方法：**净效率 = 表面效率提升 - 验证税成本**。

- AI生成代码事故率比普通PR高23.5%（详见前述"隐性验证税与角色异化"），这部分隐性成本(工程师对AI输出的"潜在欺骗检查")必须从PR合并速度提升中扣除
- 缺陷率、返工率(反馈二已列指标)在AI场景下应拆分为**"AI相关"与"非AI相关"**两类分别统计,否则无法定位提效是真实还是转移成本

意义:避免组织被"PR合并更快"的表面数据误导,确保净时间节省是真实的、可信的。

###### 用Token效率比替代代码行数/PR数量

反馈二中"最小公共指标集"的核心新增指标应是**Token效率比**(完成一个有效任务的平均Token消耗),取代失效且易被"灌水"的代码行数/PR数量:

- 与"任务耗时"指标搭配,形成"时间账"+"经济账"双维度
- "有效任务"的判定需结合质量指标(缺陷率、是否被保留/回退),防止"快速消耗大量Token但产出无效代码"被误判为高效

意义:这是反馈二"统一维度、不统一数值"原则的具体落地——Token效率比是跨场景通用的"维度",但其数值会因场景复杂度(绿地vs遗留)合理浮动。

###### 全工程分析需验证"J曲线是否传导到组织层"

反馈三的核心产出是"定位瓶颈、验证局部提效是否传导为整体提效"。结合J曲线和验证税:

- 端到端数据链路打通后,首要验证问题应是:**个人层面15%-35%的提效,是否在组织层面被验证税、返工、流程瓶颈抵消甚至转为负值**
- 这正是"个体提效明显、组织提效不显性"现象的量化检验入口——全工程分析的第一个里程碑,不是追求覆盖率,而是回答这一个问题
##### 人机协作的可观测

- 建立**端侧埋点标准**,对Coding Agent的会话定义统一可采集的数据结构(任务类型、交互轮次、采纳/拒绝率、生成代码量、最终是否被保留等),作为各Agent(claude-code/cursor/codebuddy等)接入的"最小可观测契约"
- 区分两层可观测目标:**过程可观测**(开发者意图、任务上下文)用于理解使用模式;**结果可观测**(生成质量、采纳情况、后续是否引发问题)用于评估Agent能力——两者数据来源和采集时机不同,不能混为一谈
- 优先做"轻量、非侵入"的采集(如插件/Hook层面记录关键事件),避免要求开发者额外操作,降低落地阻力


---

## 成熟度模型定义

分成几个维度：

- **基础设施**（I for Infrastructure）：算力模型管理，调度分配
- **知识工程**（K for Knowledge）
- **流程引擎**（E for Engine）
- **评估治理**（E for Evaluation）
- **组织人才**（P for People）

因为我们软件平台不会花太多精力在 Infra 这一层，所以我只取后四个维度，简称为 **KEEP 模型**。

---

### 成熟度等级定义

| 阶段     | 命名                        | 价值主张   | 核心特征                                                                                                                          |
| ------ | ------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------- |
| **L1** | 辅助提效（AI Assisted）         | 释放个体潜能 | 个体使用 AI 工具提升效率，AI 作为"更好的工具"。价值体现在个体开发者的生产力提升、重复性工作的自动化、学习曲线的缩短。                                                               |
| **L2** | 领域集成（Domain Integrated）   | 构建组织智能 | 将 AI 能力系统化集成至特定研发领域和流程。价值从个体层面上升到组织层面：形成可复用的领域知识资产、建立团队级 AI 能力标准、AI 投入生产环节产生可衡量的组织级效益。                                        |
| **L3** | Agent 协同（Agentic Synergy） | 倍增协作效能 | 人机协同模式建立，Agent 承担明确业务交付角色与任务。价值在于人力杠杆的倍增：每个工程师通过 Agent 协同能够承担更大范围的工作，团队的有效产能显著超越传统模式。                                         |
| **L4** | 自主代理（Autonomous Agents）   | 实现自主交付 | Agent 具备"管理者"能力，能根据任务场景自主设计、编排多 Agent 分工协作。从 Human in the Loop 转变到 Human out of the Loop：端到端的自动化交付释放了人类的战略创造力，组织的交付能力与团队规模脱钩。 |

---

### KEEP 成熟度矩阵

| 维度              | L1 辅助提效<br>释放个体潜能                                               | L2 领域集成<br>构建组织智能                                                  | L3 Agent 协同<br>倍增协作效能                                                                                          | L4 自主代理<br>实现自主交付                                                                                                                                  |
| --------------- | --------------------------------------------------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **知识工程**<br>（K） | · 仅使用公开知识，无领域整合<br>· 文档未结构化，人工检索为主<br>· 无工程化知识管理手段              | · 领域各自知识库建设<br>· Context Engineering 实践启动<br>· 有 AI 案例库沉淀          | · 跨领域知识体系构建<br>· 领域 Skill 库与质量管理体系                                                                             | · 知识飞轮：多 Agent 共享与贡献<br>· Agent 具备"管理者"级别知识综合能力<br>· Agent 自优化经验自动沉淀；自进化知识生态系统：自主识别盲区并自我扩展                                                         |
| **流程引擎**<br>（E） | · 传统流程嵌入 AI 辅助工具<br>· 流程人主导，AI 工具可选<br>· Vibe Coding 探索式使用      | · AI 集成 DevOps 关键环节<br>· 智能代码审查与测试生成<br>· AI 代码质量基线与技术债管理          | · 自适应的流程规范（Spec 驱动）<br>· 领域 Harness 配置管理平台<br>· 领域 Harness Engineering 实践<br>· Agent 承担明确研发角色，绩效与 Token 效率纳入度量 | · AgentOps 与 VPT 效能度量驱动持续优化<br>· Agent 具备自主设计与规划能力<br>· 多 Agent 自主编排协同与 Token 优化<br>· 飞轮自我进化与配置盲区自动发现<br>· 自进化飞轮基础设施：自动化评估与在线优化反馈回路<br>· 成本与效益智能优化 |
| **评估治理**<br>（E） | · 基本 AI 使用规范与禁止项<br>· AI 内容人工审核<br>· 简单日志记录，缺系统风险评估             | · 治理框架含访问控制与审计<br>· AI 代码安全扫描与合规检查                                 | · Agent 权限边界定义与强制执行<br>· Harness 层安全设计与沙箱隔离，Agent 执行质量验收标准<br>· Agent 行为完整可追溯审计                                | · 自主编排场景下的权限矩阵与监控<br>· 认知债务评估与管控<br>· Agent 自优化安全约束与自动回滚<br>· AI 可信度评级与影响评估<br>· 人机共治，人保留最终控制权                                                     |
| **组织人才**<br>（P） | · 传统组织加 AI 工具培训<br>· 基本 Prompt Engineering 技能<br>· 个人探索，无系统能力建设 | · AI CoE 推广实践与培训体系<br>· 开发者学习 Context Engineering<br>· AI 使用效率纳入度量 | · 角色转型：Harness Engineer 等<br>· 开发者转型为 Agent 协作监督者<br>· 人机协同工作规范与评估标准                                           | · Agent Orchestrator/Evaluator 新岗<br>· 组织运转接近自动化软件工厂<br>· 基于价值创造与 Token 效率考核<br>· 飞轮架构师：飞轮的设计者与守护者<br>· 创新孵化平台：由超级个体 + 多 Agent 组成的完整生产与创新团队        |


举例：
- 缺少agent规范算是流程引擎相关领域的问题，因为这是定义工作流水线、开发流程的要素。
- 需求设计质量问题更多可以算是知识工程的问题。因为很多是缺少有效的行业、工程的上下文。但也兼具流程引擎问题，比如可能需要借助流程引擎的spec的定义来约束这些过程。
- 建立CoE是组织人才领域的问题。

---



---

## 差距洞察分析和软件平台能力自评

### 评估方法

基于前文提出的 **KEEP 成熟度模型**，对照前文梳理的各领域问题，对软件平台当前 AI 原生开发能力进行自评。

**评分标准**：L1=1分，L2=2分，L3=3分，L4=4分

**权重分配**：

| 维度      | 权重  | 理由                      |
| ------- | --- | ----------------------- |
| 知识工程（K） | 30% | 大华行业知识壁垒高，上下文碎片化是当前最大瓶颈 |
| 流程引擎（E） | 25% | 决定 AI 能否系统化融入研发流程       |
| 评估治理（E） | 25% | 质量保障是 AI 落地的底线          |
| 组织人才（P） | 20% | 长期能力建设，但非当前最紧迫          |

---

### 各维度详细评估

#### 1. 知识工程（K）—— 当前等级：L1+ → L2-

| 评估项    | L1→L2 进展                 | 当前状态                                           | 得分  |
| ------ | ------------------------ | ---------------------------------------------- | --- |
| 知识整合   | 从仅使用公开知识 → 领域知识库建设启动     | 各领域已建立 蜻蜓(Confluence) /SVN/Git知识库，行业知识有过结构化整理  | 1.5 |
| 文档结构化  | 从人工检索为主 → 开始探索 AI 友好格式   | 部分团队试点 AGENTS.md（或其他如CLAUDE.md），文档开始考虑 AI 可读性  | 1.3 |
| 知识管理手段 | 从无工程化手段 → LLM-Wiki 方案设计中 | 架构部LLM-Wiki 概念验证完成，write-time-synthesis 技术路线确定 | 1.5 |

**已有成果**：
- 部分产品线建立了行业知识库
- 开始推行 AGENTS.md 和 architecture.md 实践
- LLM-Wiki 技术方案已完成 POC

**待补差距**：
- 行业特有知识（术语、"黑话"、"潜规则"）显式化程度不足
- 知识资产仍分散，缺少统一的 All In Code 实践
- 渐进式信息暴露机制尚未建立

**年度目标**：L2 稳定 → L3 起步（建立跨领域知识体系，Skill 库与质量管理体系，规范All In Code 实践）

---

#### 2. 流程引擎（E）—— 当前等级：L2-

| 评估项     | L1→L2 进展                      | 当前状态                                       | 得分  |
| ------- | ----------------------------- | ------------------------------------------ | --- |
| AI 工具嵌入 | 从可选工具 → DevOps 关键环节集成         | codebuddy 深度集成，慧码等工具覆盖代码审查、测试生成            | 2.0 |
| 流程主导    | 从人主导 → AI 参与流程编排              | 部分团队试点实现 Spec 驱动，Agent 承担明确角色              | 1.7 |
| 探索程度    | 从 Vibe Coding → 领域 Harness 实践 | 普遍已有 Harness Engineering 概念，部分团队落地 QA 四块拼图 | 1.8 |

**已有成果**：
- 慧码平台集成代码审查和测试生成能力
- codebuddy 成为主流开发工具，日均使用率高
- 部分团队落地了 Rule → Skill → Scripts → 总验证的 Harness 体系
- 开始推行 Spec 驱动的开发流程

**待补差距**：
- Skill 开发规范尚未统一，缺少 RFC 评审机制
- 人机协作边界需进一步清晰化
- 工具链整合度待提升，减少各自为战

**年度目标**：L2 稳定 → L3 深化（自适应流程规范，领域 Harness 配置管理平台）

---

#### 3. 评估治理（E）—— 当前等级：L1+ → L2-

| 评估项 | L1→L2 进展 | 当前状态 | 得分 |
|--------|-----------|----------|------|
| 使用规范 | 从基本规范 → 治理框架建设 | AI 使用规范覆盖安全、合规，访问控制和审计机制设计中 | 1.6 |
| 内容审核 | 从人工审核 → AI 辅助 + 人工复核 | AI 代码安全扫描工具试点，人工 Review 流程优化中 | 1.5 |
| 风险评估 | 从简单日志 → 基线对比机制探索 | 部分团队试点开发前后基线对比，质量门禁概念验证中 | 1.4 |

**已有成果**：
- AI 使用规范已覆盖安全和合规要求
- 代码安全扫描工具进入试点阶段
- 基线对比机制在部分产品线验证
- Token 效率比指标体系设计中

**待补差距**：
- 确定性裁判体系（编译器/测试/hooks 强制执行）尚未全面部署
- 隐性验证税仍较重，需进一步降低 AI 生成代码的事故率
- 准入准出标准需统一
- 端侧可观测性方案待落地

**年度目标**：L2 稳定（Harness 层安全设计与沙箱隔离，Agent 执行质量验收标准建立）

---

#### 4. 组织人才（P）—— 当前等级：L1+ → L2-

| 评估项 | L1→L2 进展 | 当前状态 | 得分 |
|--------|-----------|----------|------|
| 组织形态 | 从传统组织 → AI CoE 筹备中 | AI CoE 筹备组成立，推广实践和培训体系规划中 | 1.6 |
| 技能建设 | 从基本 Prompt → Context Engineering 学习 | 团队开始学习 Context Engineering，内部培训启动 | 1.5 |
| 能力建设 | 从个人探索 → 系统化能力建设规划 | 新角色定义（上下文工程师、Harness 工程师）讨论中，能力模型设计中 | 1.4 |

**已有成果**：
- AI CoE 筹备组成立，正在制定推广计划
- Context Engineering 内部培训材料编制中
- 新角色定义进入讨论阶段（上下文工程师、Harness 工程师）
- 部分先行者已探索出可复制的最佳实践

**待补差距**：
- 新角色（上下文工程师、Harness 工程师、飞轮架构师）需正式定义和落地
- 能力培养需从"师徒制"转向"品味与架构传承"
- Half-Stack 组织重构需试点推进
- AI 使用效率需纳入正式度量体系

**年度目标**：L2 稳定（角色转型启动，开发者转型为 Agent 协作监督者，人机协同工作规范建立）

---

### 综合评分

| 维度 | 权重 | 当前得分 | 加权得分 | 年度目标得分 |
|------|------|----------|----------|-------------|
| 知识工程（K） | 30% | 1.43 | 0.43 | 2.5 → 0.75 |
| 流程引擎（E） | 25% | 1.83 | 0.46 | 2.8 → 0.70 |
| 评估治理（E） | 25% | 1.50 | 0.38 | 2.5 → 0.63 |
| 组织人才（P） | 20% | 1.50 | 0.30 | 2.5 → 0.50 |
| **总计** | **100%** | — | **1.57** | **2.58** |

**当前综合等级**：**L1+ → L2-（辅助提效向领域集成过渡）**

**解读**：
- 已度过纯 L1 阶段，在多个维度取得实质性进展
- 流程引擎表现最好（有了一些工具系统，codebuddy 深度使用）
- 知识工程和组织人才相对滞后，需重点投入
- 整体处于 L2 门槛，正在向 L2 稳定迈进

**年度目标**：**L2 稳定 → L3 起步**（Agent 协同阶段）
- 建立跨领域知识体系，完善 Skill 库
- 实现自适应流程规范和领域 Harness 平台
- 角色转型启动，人机协同工作规范建立
- 为 L3 的 Agent 协同奠定基础

---

### 工作方向

基于差距分析和年度目标（L2 稳定 → L3 起步），建议按以下优先级推进：

| 行动项                                                | 对应维度 | 预期效果                                  |
| -------------------------------------------------- | ---- | ------------------------------------- |
| 发布知识工程相关规范，盘点现有知识资产，建立 LLM-Wiki 知识库，推行 All In Code | K    | 解决上下文碎片化，为其他建设打基础                     |
| 部署确定性裁判体系（hooks + 自动化测试完备）                         | E    | 降低隐性验证税，保障质量底线                        |
| 建立 Skill 开发规范，完善评审和管理机制                            | E    | 统一工具链，促进复用                            |
| 启动 AI CoE，正式定义研发团队新角色                              | P    | 系统化能力建设                               |
| 探讨Token 效率比度量，质效看板上线                               | E    | 数据驱动持续优化                              |
| 推行 Half-Stack 组织重构试点                               | P    | 提升小团队作战能力                             |
| 领域 Harness 治理规范和工程实践落地                             | E    | 包括政府、企业、基础、海外、西安、成都的各团队都有完善的自适应流程规范落地 |

**年度关键成果目标**：
-  知识工程：跨领域知识体系建立，分级分类的知识库体系全面运作
-  流程引擎：Skill 生态成熟，构建Harness 体系支撑 人-Agent 协同
-  评估治理：确定性裁判体系全面部署，探索Token 消耗效率等评估方式
-  组织人才：新角色落地，CoE运作。Half-Stack 或者研发中心所讲的开发占比 > 10%（通过事实上的任务输出结果可证明）


==年度建设方略和成果，将体现在《大华软件平台AI原生开发技术白皮书2026》==。

---

## 后续行动

### 总体行动说明

- **one spec**：一套技术规范，定义知识工程、评估体系、工具流程等具体规范要求
- **one board**：一套质效看板，体现从算力到团队到个人到业务成效的质量效率指标体系
- **one market**：一个 AI 资产市场，沉淀 spec、skill、mcp、rule 等资产
- **one runtime**：一个开发 Agent Runtime。解决 spec 规范沉淀、过程个人度量数据采集、外部系统对接等功能
- **one group**：定义一个核心工作组（旧时代经验者+新生力量），架构+业务+AI 新生凶猛力量，明确大华软件平台 AISE 技术走向，作为我们AI4SE的CoE。
![[essay/ai_native_software_dev_org_model.png]]
这些工作内容的关系：
- 核心工作组看护一套技术规范，
- 基于技术规范落地一个 runtime，
- 基于 runtime 沉淀标准化研发活动和度量数据；
- 基于优秀实践形成 AI 资产市场；
- 基于度量数据打造 AI 质效看板。


这样软研会是一套体系。各自的工具建设会有，但不必要的、有冲突的不做，有必要做的必须统一接口标准和度量收口。鼓励开源共创，集体维护。




---


### 组织人才

这部分不多讲了。需要请HR帮忙多关注一下。

#### CoE虚拟组织
建立CoE虚拟组织。除了王葛亮，架构师组织和原有团队TL之外，重点吸纳一线AI原生开发的新生力量。

#### 人才认知和新角色定义
明确以下几类人才定义，和我们的任职资格匹配：
- 上下文工程师: 本质是知识/项目上下文管理，特别是代码仓的All In Code。建议各个团队明确角色，对团队知识进行管理；
- Harness工程师/Loop工程师：致力于推动团队的Agent能够高质量完成长程工作。是我们这个时代的效能专家；
- 飞轮架构师：端到端推动组织的工程能力，尤其是AI自主完成的能力。除了自身工作外，可能还需要关注到比如测试团队/环境部署的情况/客户端等资源团队的瓶颈等。

#### 长期话题
结合着任职等一系列工作，继续讨论：怎么评价人使用 AI 的能力？怎么构建团队的能力基线?

继续推进优秀实践分享。

#### 7月份的黑客松
筹备中。


### 知识工程

首先是建立《软件平台知识代码化下沉》规范，明确All in Code的最佳实践：
- 在代码仓库构建好本地上下文，引入包括architecture.md在内的结构化的Markdown文档；
- 将架构规范、API 设计要求、数据库变更规范等全局知识，转化为可执行的 YAML 规则或静态扫描脚本（即本文提到的“GC式技术债管理”的底层规则），与代码同源管理
(6月完成规范，各团队实践闭环)

对于存量系统，强制迁移到统一知识库也不现实：
- 构建联邦化知识检索。通过MCP链接存量的知识。包括萤火虫等一系列系统；
（已在进行中）


新的知识库构建：
- LLM wiki。面向个人和团队，提供LLM wiki能力。重点在于知识图谱关联/新知识发现
- RAG。统一建设。提供向量检索增强。
（方案进行中）

跨部门协作：
- API First. 先把协议管理落实；
- 后续建立跨团队知识库目录，可以按需申请。
（API协议管理已有。知识库跨团队资源目录化管理规划中）    

代码库知识的长期维护，需要结合一些背景智能体。包括的话题包括更新/和代码的一致性/依赖团队组件的刷新同步机制等。


总结来说，“All in Code”背景下的知识工程，就是**用 Git 托管知识，用 MCP 联邦孤岛，用 API 契约隔离团队，用 Agent 自动化维护生命周期。**

### 流程引擎


整个引擎体系其实核心就三个东西：
- one board 一个统一效能看板
- one runtime 一个标准agent运行时
- one market 一个统一AI资产市场

#### One Board AI原生效能看板

我们会整合包括Agent Runtime采集数据，IT算力看板数据，API key数据，TB，萤火虫，慧码资产等数据，成为未来人机协同，AI原生开发的研发过程度量全体系看板。

![[Pasted image 20260614152825.png]]

![[Pasted image 20260614152842.png]]

![[Pasted image 20260614153135.png]]

![[Pasted image 20260614153145.png]]

![[Pasted image 20260614153152.png]]
![[Pasted image 20260614153203.png]]

![[Pasted image 20260614153208.png]]


![[Pasted image 20260614153234.png]]
![[Pasted image 20260614153241.png]]

![[Pasted image 20260614153249.png]]


后续还需要通过效能看板识别跨团队瓶颈，特别是等待时间异常，自动化能力瓶颈，推动对应团队分析。


这些不是终局，我们做产品，最终回答的还是产品面世的速度和质量：

![[Pasted image 20260614160337.png]]

#### One Runtime: 慧码Agent Runtime

为什么要有自己的Runtime？

其实前面我们讲过很多问题，包括AI的概率性推理带来的不可预期，包括AI开发后的质量保证难的问题，包括Agent等AI资产的标准化、体系化建设的问题。这些问题都可以通过Agent Runtime来解决。

通过Agent Runtime运行在我们的通用编程智能体或者特定智能体侧，结合Hook机制，可以做到：
- 提供包括和其他系统如慧码AI资产市场，萤火虫的交互；
- 识别开发者具体的任务和token消耗的对应情况；
- 开发者有没有不太适合AI做的工作交给了AI；
- 某次开发过程Agent的结果不好，它到底做了什么，调用了哪些工具，改了哪些文件？

基于这些，我们才有可能：
- 规范标准开发行为；
- 建立AI ROI 系统，明确针对任务的AI投入消耗是否合理，如何改进；
- 跟踪开发者和团队的AI应用水平；
- 评估Agent的行为质量，分析其存在的问题，持续改进。

![[agent_runtime_governance_architecture.png]]

#### One market: 慧码市场

我们会建设统一的skill/MCP/rule市场。向上提供到研发中心，向下搜集各个团队优秀产出。
市场本身会有评价评估体系，推荐机制等。
功能开发中，不再赘述。

#### 其他系统：萤火虫，TB，WeTrack， WeOR...

原有的存量系统各有其价值。在今天应该把它们变成一个个MCP接入到我们的Agent Runtime。

- 萤火虫：软件平台的产品组件资产/协议管理平台
- TB：项目协作平台
- WeTrack：缺陷管理平台
- WeOR：定制需求平台

#### Everything Builder, 内部开源&生命周期管理


除了三个一之外，我们还是应该鼓励大家各团队积极探索工具、平台。
但这里会有一些矛盾之处：
- 业务团队不太可能持续投入公共性质的工具平台系统的开发和维护；
- 但我们软研又事实上没有足够的资源团队来承接所有的探索类开发（研究院和工程院也不可能）；
- 业务团队做了好东西，也想共享给别的团队，但是什么时候该推广？过早了不成熟，过晚了可能又有重复开发；
- 项目共享之后带来接不完的需求，做还是不做？

我的解决方式是： 1）开源社区方式运作，明确生命周期和退出机制；2）做好奖励和分享。我去年就讲慧码应该是个社区，在今年这个时刻，我觉得是时候了。让我们成为Everything Builders！

（该流程机制建议PQA一起参考业界实践整理细化下）
###### 社区化运作机制：“慧码”社区

- **统一的准入标准：** 建立一个公共仓库，每个项目需要提供一份标准的 `README.md`（包含 BLUF 格式的简介、快速开始、架构设计）。
- **角色定义：**
    - **Maintainer（维护者）：** 工具的初始作者或核心贡献者（来自业务团队）。拥有代码合并权限，负责架构把控。
    - **Contributor（贡献者）：** 任何提交过 PR/MR 或修复过 Bug 的研发人员。
    - **Sponsor（赞助者）：** 平台工程团队指定的接口人，负责提供基础设施支持（如 CI/CD 流水线、内部云资源）。
- **协作模式：** 全面采用 PR/MR 模式。业务线 A 发现业务线 B 做的工具缺一个功能，不应该要求 B 团队排期开发，而是 A 团队直接阅读代码并提交 PR。
###### 明确的生命周期与退出机制（防范技术债）

工具平台必须贴上“保质期”标签，分为四个阶段：
- **阶段一：沙盒期（Sandbox）**
    - **规则：** 业务团队自由探索，自行利用空闲资源开发。不承诺 SLA（服务级别协议），不强制推广。
    - **退出：** 长期无更新、无人使用的项目，系统自动标记为 `Archived`（只读归档）。
- **阶段二：孵化期（Incubating）**
    - **规则：** 工具在跨团队（至少两个以上业务线）产生价值。需要在社区登记，平台工程团队开始介入，协助提供标准化的部署资源（如容器集群、网关接入）。要求完善 API 文档和使用手册（可沉淀至内部 AI-Wiki 知识库）。
- **阶段三：核心收口（Graduated / Core）**
    - **标准：** 工具成为全量研发流程中的关键节点（如代码扫描、统一配置中心）。
    - **动作：** **所有权转移（Handover）。** 平台工程团队正式接管该系统，将其纳入核心公共基础设施，由专门的 SRE 和平台工程师负责其高可用性（SLA 99.9%）。原业务作者可转为架构委员会成员。
- **阶段四：强制退役（Deprecated / Sunset）**
    - **规则：** 当有更优秀的官方收口系统出现，或底层技术栈被淘汰时。
    - **动作：** 发布“日落计划”（提供 3-6 个月的迁移窗口）。窗口期结束后，平台团队有权强行下线其运行环境，避免祖传代码无人维护。
###### 激励与分享：打造技术文化

业务开发做公共工具没有直接的业务 KPI 收益，因此激励机制必须补位。

- **精神与荣誉激励（社区认可）：**
    - 建立内部的开源贡献榜单。
    - 为活跃的 Maintainer 和 Contributor 颁发专属头衔（例如“年度 Everything Builder”、“核心架构贡献者”）。
        
- **绩效与晋升通道（物质与职级）：**
    - **在绩效考核中设置专项权重：** 明确规定在公共平台建设上的 PR 数量和质量，可为评定 S/A 级绩效的强加分项。
    - 在高级技术专家/架构师的晋升答辩中，“跨团队的技术影响力”或“主导内部开源工具”应作为硬性准入条件。
        
- **知识分享闭环：**
    - 定期举办内部技术沙龙（如“慧码”开发者大会）。邀请优秀工具的作者进行宣讲。
    - 鼓励作者将踩坑经验和设计思路写成深度技术文章，作为团队的优质知识资产。



待参考：
（先记录一下，还没时间看）
https://github.com/wecode-ai/Wegent
https://github.com/alibaba/loongsuite-pilot






### 评估治理

AI原生软件开发的评估治理体系,目标是让"AI生成的代码和过程是否可信、是否达标"变得可衡量、可追溯、可持续改进,而不是停留在人工抽查和事后补救。这部分工作将以一系列规范文档为产出主线,6月底完成初稿,后续在试点中迭代。

评估治理覆盖四个层次。第一层是单环节产出质量,即对每次AI生成的代码片段本身进行把关,通过代码 Review Agent 自动检查代码风格、潜在缺陷、设计合理性,通过安全合规扫描 Agent 检测敏感信息泄露、已知漏洞模式和合规红线,形成第一道质量闸门。第二层是Agent工作过程的规范性,例如单元测试覆盖率、关键路径是否补充测试、是否遵循既定的编辑协议和验证回路等,这些不是事后检查代码本身,而是检查Agent"做事的方式"是否达标,确保过程本身可信。第三层依托Agent Runtime采集的度量数据,把Token消耗、工具调用次数、任务耗时等资源维度纳入治理范围,使资源消耗本身成为可分析、可优化的对象,而不是黑箱成本。第四层是面向集成/整合系统的专项治理,关注架构层面的技术债务——模块边界是否清晰、依赖关系是否健康、是否存在AI快速迭代带来的架构腐化,这一层需要架构师参与定期评估。

四个层次的数据最终都会汇入运营看板,治理问题(如覆盖率不达标的模块、Token消耗异常的任务、架构债务热点)和治理成果(如缺陷率下降、重复代码减少)在看板上可视化呈现,形成"发现问题—推动改进—验证效果"的可见闭环,持续驱动整体质量演进。

![[ai_eval_governance_four_dimensions.png]]


工作方式上,核心思路是从传统的"集中清理"转向"垃圾回收式"的常态化技术债务管理。具体做法是把团队认可的"黄金原则"(如命名规范、模块边界约定、禁止的反模式)编码为可被Agent识别和执行的规则,部署一个后台运行的常驻Agent,定期扫描代码库,识别偏离黄金原则的代码、更新各模块的质量评级,并将结果同步到看板。在能力成熟后,这个常驻Agent可以进一步升级为主动治理者——针对识别出的偏离,自动生成定向重构PR,以小批量、低风险的方式持续修复,而不是积累到某个时间点再做一次大规模重构。这种方式的核心优势是把技术债务管理从"周期性的痛苦项目"变成"系统的日常代谢",代码库始终保持在一个可控的健康水位,避免冗余代码和架构腐化随AI开发速度加快而加速累积。


![[gc_style_tech_debt_management.png]]

接下来的工作拆解包括:
- 明确质量/安全等一系列技术规范，并形成可执行规则;
- 设计代码Review Agent和安全扫描Agent的接入方式;
- 定义UT覆盖率等过程质量规范的具体阈值;
- 设计Runtime度量数据到看板的采集与展示链路;
- 以及设计常驻治理Agent的扫描频率和PR生成机制


---

## 总结

- 我们分析了行业的 AISE 现状；
- 以 Agent 来完成更多软件开发执行工作为方向，软件开发生命周期走向了 ADLC；
- 我们分析了软件平台当前 AISE 过程感知到的问题，并按问题领域进行了分析；
- 我们定义软件平台的 AISE 成熟度模型，结合之前的问题给出了我们的评级；
- 我们向下一个阶段前进，需要完成的工作是什么。

AI 软件工程的本质，是从"管理代码生产"走向"管理智能生产"。在这场范式革命中，真正贵的不是 Token，而是失控。我们必须正视认知陷阱，构建适配自身的上下文工程与确定性裁判体系，才能在 AI 浪潮中将大华软件平台研发的个体生产力真正转化为组织级的竞争壁垒。


---

## 参考资料

(建议有精力可以点开看一下……)

1.     Development Trends and Architecture Evolution of AI Agents ..., accessed June 9, 2026, [https://www.alibabacloud.com/blog/602529](https://www.alibabacloud.com/blog/602529)

2.     AI-Native Software Engineering: Enduring Principles, New Pace, accessed June 9, 2026, [https://www.sei.cmu.edu/events/ai-native-software-engineering-enduring-principles-new-pace/](https://www.sei.cmu.edu/events/ai-native-software-engineering-enduring-principles-new-pace/)

3.     The AI-native engineering flow. Special thanks to Mona Soliman ..., accessed June 9, 2026, [https://medium.com/data-science-at-microsoft/the-ai-native-engineering-flow-5de5ffd7d877](https://medium.com/data-science-at-microsoft/the-ai-native-engineering-flow-5de5ffd7d877)

4.     Building an AI-Native Engineering Team – Codex | OpenAI ..., accessed June 9, 2026, [https://developers.openai.com/codex/guides/build-ai-native-engineering-team](https://developers.openai.com/codex/guides/build-ai-native-engineering-team)

5.     Harness design for long-running application development \ Anthropic, accessed June 9, 2026, [https://www.anthropic.com/engineering/harness-design-long-running-apps](https://www.anthropic.com/engineering/harness-design-long-running-apps)

6.     LLMOps blueprint for closed-source large language models - Grid Dynamics, accessed June 9, 2026, [https://www.griddynamics.com/blog/llmops-platform-blueprint](https://www.griddynamics.com/blog/llmops-platform-blueprint)

7.     LLMOps Architecture : A Detailed Explanation - Truefoundry, accessed June 9, 2026, [https://www.truefoundry.com/blog/llmops-architecture](https://www.truefoundry.com/blog/llmops-architecture)

8.     LLMOps workflows on Databricks, accessed June 9, 2026, [https://docs.databricks.com/aws/en/machine-learning/mlops/llmops](https://docs.databricks.com/aws/en/machine-learning/mlops/llmops)

9.     LLMOps: running large language models in production - Quix, accessed June 9, 2026, [https://quix.io/blog/llmops-running-large-language-models-in-production](https://quix.io/blog/llmops-running-large-language-models-in-production)

10.  What is prompt versioning? Best practices for iteration without ..., accessed June 9, 2026, [https://www.braintrust.dev/articles/what-is-prompt-versioning](https://www.braintrust.dev/articles/what-is-prompt-versioning)

11.  Best LLMOps Platforms for Enterprise AI Teams: 2026 Guide - Atlan, accessed June 9, 2026, [https://atlan.com/know/best-llmops-platforms/](https://atlan.com/know/best-llmops-platforms/)

12.  PromptOps vs LLMOps vs AIOps: differences and when to use each | PromptOperations.ai, accessed June 9, 2026, [https://promptoperations.ai/guide/promptops-vs-llmops/](https://promptoperations.ai/guide/promptops-vs-llmops/)

13.  Prompt vs Context vs Harness Engineering: Key Differences - Atlan, accessed June 9, 2026, [https://atlan.com/know/harness-engineering-vs-prompt-engineering/](https://atlan.com/know/harness-engineering-vs-prompt-engineering/)

14.  Building a Git-Based Prompt Versioning System with Python & Jinja | by Ben Batman, accessed June 9, 2026, [https://medium.com/@benbatman2/building-a-git-based-prompt-versioning-system-with-python-jinja-bb1d37d9ee4b](https://medium.com/@benbatman2/building-a-git-based-prompt-versioning-system-with-python-jinja-bb1d37d9ee4b)

15.  What is Prompt Management? And how to version, control & deploy prompts in productions, accessed June 9, 2026, [https://langwatch.ai/blog/what-is-prompt-management-and-how-to-version-control-deploy-prompts-in-productions](https://langwatch.ai/blog/what-is-prompt-management-and-how-to-version-control-deploy-prompts-in-productions)

16.  Harness Engineering: Why the Way You Wrap AI Matters More Than Your Prompts in 2026, accessed June 9, 2026, [https://www.aimagicx.com/blog/harness-engineering-replacing-prompt-engineering-2026](https://www.aimagicx.com/blog/harness-engineering-replacing-prompt-engineering-2026)

17.  I Built PromptOps: Git-Native Prompt Management for Production LLM Workflows - Medium, accessed June 9, 2026, [https://medium.com/@jision/i-built-promptops-git-native-prompt-management-for-production-llm-workflows-ae49d1faa628](https://medium.com/@jision/i-built-promptops-git-native-prompt-management-for-production-llm-workflows-ae49d1faa628)

18.  Harness Engineering: How to Build Reliable AI Agents by Engineering the System, Not the Model | deepset Blog, accessed June 9, 2026, [https://www.deepset.ai/blog/harness-engineering](https://www.deepset.ai/blog/harness-engineering)

19.  Engineering Blog | Harness Blog Primary Category, accessed June 9, 2026, [https://www.harness.io/blog-category/engineering-blog](https://www.harness.io/blog-category/engineering-blog)

20.  人人都是程序员？百度、阿里同天向个人免费开放AI编码助手, accessed June 9, 2026, [https://m.mp.oeeee.com/a/BAAFRD000020240403930344.html](https://m.mp.oeeee.com/a/BAAFRD000020240403930344.html)

21.  文心快码Baidu Comate - Open VSX Registry, accessed June 9, 2026, [https://open-vsx.org/extension/BaiduComate/comate](https://open-vsx.org/extension/BaiduComate/comate)

22.  [2402.04141] Multi-line AI-assisted Code Authoring - arXiv, accessed June 9, 2026, [https://arxiv.org/abs/2402.04141](https://arxiv.org/abs/2402.04141)

23.  Trae: A New Free AI-Powered Code Editor from ByteDance | DigitalOcean, accessed June 9, 2026, [https://www.digitalocean.com/community/tutorials/trae-free-ai-code-editor](https://www.digitalocean.com/community/tutorials/trae-free-ai-code-editor)

24.  CodeCompose: AI for Code Authoring at Meta | PDF | Metadata - Scribd, accessed June 9, 2026, [https://www.scribd.com/document/655659809/CodeCompose-A-Large-Scale-Industrial-Deployment-of-AI-assisted-Code-Authoring](https://www.scribd.com/document/655659809/CodeCompose-A-Large-Scale-Industrial-Deployment-of-AI-assisted-Code-Authoring)

25.  Multi-line AI-assisted Code Authoring - arXiv, accessed June 9, 2026, [https://arxiv.org/pdf/2402.04141](https://arxiv.org/pdf/2402.04141)

26.  Google Antigravity vs Continue: Evaluating AI Coding Assistants for Enterprise Legacy Codebases, accessed June 9, 2026, [https://www.augmentcode.com/tools/google-antigravity-vs-continue](https://www.augmentcode.com/tools/google-antigravity-vs-continue)

27.  Unveiling Trae: ByteDance's AI IDE and Its Extensive Data Collection System - Unit 221B, accessed June 9, 2026, [https://blog.unit221b.com/dont-read-this-blog/unveiling-trae-bytedances-ai-ide-and-its-extensive-data-collection-system](https://blog.unit221b.com/dont-read-this-blog/unveiling-trae-bytedances-ai-ide-and-its-extensive-data-collection-system)

28.  Why is nobody talking about how Trae is a sophisticated data collection tool first, ide second? P1 : r/TraeIDE - Reddit, accessed June 9, 2026, [https://www.reddit.com/r/TraeIDE/comments/1m5o9sz/why_is_nobody_talking_about_how_trae_is_a/](https://www.reddit.com/r/TraeIDE/comments/1m5o9sz/why_is_nobody_talking_about_how_trae_is_a/)

29.  AI and productivity: A year-in-review with Microsoft, Google, and GitHub researchers - DX, accessed June 9, 2026, [https://getdx.com/podcast/ai-and-productivity-a-year-in-review/](https://getdx.com/podcast/ai-and-productivity-a-year-in-review/)

30.  DORA.dev, accessed June 9, 2026, [https://dora.dev/](https://dora.dev/)

31.  How to measure AI's impact on developer productivity - DX, accessed June 9, 2026, [https://getdx.com/blog/ai-measurement-hub/](https://getdx.com/blog/ai-measurement-hub/)

32.  How Google measures developer productivity - DX, accessed June 9, 2026, [https://getdx.com/blog/how-google-measures-developer-productivity/](https://getdx.com/blog/how-google-measures-developer-productivity/)

33.  How to Improve Developer Productivity: Metrics and Tips - Atlassian, accessed June 9, 2026, [https://www.atlassian.com/blog/loom/developer-productivity](https://www.atlassian.com/blog/loom/developer-productivity)

34.  Measuring the productivity impact of AI coding tools: A practical guide for engineering leaders | Swarmia, accessed June 9, 2026, [https://www.swarmia.com/blog/productivity-impact-of-ai-coding-tools/](https://www.swarmia.com/blog/productivity-impact-of-ai-coding-tools/)

35.  State of AI-assisted Software Development 2025 - DORA, accessed June 9, 2026, [https://dora.dev/dora-report-2025/](https://dora.dev/dora-report-2025/)

36.  DORA: ROI of AI-assisted Software Development report - Google Cloud, accessed June 9, 2026, [https://cloud.google.com/resources/content/dora-roi-of-ai-assisted-software-development](https://cloud.google.com/resources/content/dora-roi-of-ai-assisted-software-development)

37.  New DORA Report Claims Strong Engineering Foundations Drive AI Return on Investment, accessed June 9, 2026, [https://www.infoq.com/news/2026/05/dora-roi-ai-assisted-dev-report/](https://www.infoq.com/news/2026/05/dora-roi-ai-assisted-dev-report/)

38.  Alibaba Cloud's Path To AI-Native - Forrester, accessed June 9, 2026, [https://www.forrester.com/blogs/alibaba-clouds-path-to-ai-native/](https://www.forrester.com/blogs/alibaba-clouds-path-to-ai-native/)

39.  International Workshop on Data Intensive Software Engineering (DISE) - conf.researchr.org, accessed June 9, 2026, [https://conf.researchr.org/home/fse-2026/dise-2026](https://conf.researchr.org/home/fse-2026/dise-2026)

40.  Software Engineer / Researcher, AI-Native database systems - ByteDance Careers, accessed June 9, 2026, [https://joinbytedance.com/search/7499642155158554898](https://joinbytedance.com/search/7499642155158554898)

41.  China AI Native Industry Insights – 20251113 – Tencent | Baidu | ByteDance, accessed June 9, 2026, [https://ainativefoundation.org/china-ai-native-industry-insights-20251113-tencent-baidu-bytedance-more/](https://ainativefoundation.org/china-ai-native-industry-insights-20251113-tencent-baidu-bytedance-more/)

42.  【实习】面向复杂软件工程项目的Agentic AI Coding关键技术研究-TRAE, accessed June 9, 2026, [https://jobs.bytedance.com/campus/m/position/detail/7628619579603601669?recomId=179ab948-42bd-11f1-a7b0-fa163e5bb591&sourceJobId=7628830878386391349&spread=B3RU5SF](https://jobs.bytedance.com/campus/m/position/detail/7628619579603601669?recomId=179ab948-42bd-11f1-a7b0-fa163e5bb591&sourceJobId=7628830878386391349&spread=B3RU5SF)

43.  How Tencent Built QClaw in 5 Days Using AI: A Technical Deep Dive, accessed June 9, 2026, [https://qclawsg.qq.com/blog/tencent-qclaw-development-ai.html](https://qclawsg.qq.com/blog/tencent-qclaw-development-ai.html)

44.  字节跳动AI工具箱扩容Trae国内版搅动AI编程江湖 - 21财经, accessed June 9, 2026, [https://m.21jingji.com/article/20250304/d14819b7e2b68daf7e78dddbd90d69b4.html](https://m.21jingji.com/article/20250304/d14819b7e2b68daf7e78dddbd90d69b4.html)
