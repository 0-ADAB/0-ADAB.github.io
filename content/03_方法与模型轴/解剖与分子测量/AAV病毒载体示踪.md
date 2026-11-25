---
publish: true
aliases:
  - AAV示踪
  - 腺相关病毒载体示踪
  - AAV-mediated tracing
  - rAAV神经环路示踪
title: AAV病毒载体示踪
description: 利用重组腺相关病毒递送可检测报告分子，对选定神经元及其轴突投射或投射来源进行条件性标记的神经环路解剖方法。
created: 2026-10-16T10:29:19.122Z
tags:
  - 类型/方法
  - 层/观测
---

# AAV病毒载体示踪

> **一句话介绍：** AAV 病毒载体示踪（adeno-associated virus vector tracing）通过使特定位置或遗传条件下的细胞表达荧光／重组酶等报告分子，观察神经元胞体与轴突投射，回答“**哪些细胞向哪里投射**”或“**哪些细胞投射到这里**”；它通常**不直接证明突触接触、突触强度或行为因果**。(Harris et al., 2012, Curr Protoc Neurosci; Tervo et al., 2016, Neuron)

## 快速理解

可以把神经环路想象成一座城市中的线路网络。普通局部顺行 AAV 标记，相当于给“起点车站”所属的神经元及其线路染色，沿着轴突观察它们通往哪里；逆行转导型 AAV 则在“终点车站”设置可被输入纤维末梢摄取的标记，随后查找哪些远处的神经元胞体被标记。通过细胞类型特异的启动子、Cre/Flp 重组酶或交叉表达方案，还可以把可观察范围进一步限定到研究者关注的神经元亚群。(Harris et al., 2012, Curr Protoc Neurosci; Tervo et al., 2016, Neuron; Fenno et al., 2014, Nat Methods)

**区分四个容易混淆的层次：**

1. **局部转导（local transduction）**：注射位点附近的细胞获得并表达 AAV 载荷；实际细胞谱系取决于衣壳、表达调控元件和实验条件。
2. **顺行轴突标记（anterograde axonal labeling）**：在起始细胞表达的报告分子进入并显示其轴突和末梢；它**不要求病毒颗粒跨突触传播**。
3. **逆行转导（retrograde transduction）**：特定 AAV 衣壳在远端轴突末梢被摄取并使投射源胞体表达载荷；“逆行”描述这里的病毒转导路线，而非荧光蛋白简单地倒流。
4. **跨神经元／跨突触标记（transneuronal/transsynaptic tagging）**：某些有特别验证的工具，例如 AAV1 相关方案，可在特定条件下令下游细胞获得表达；这种特殊能力**不能套用到所有 AAV 载体**，且必须排除同时发生的逆行转导和非突触性转移。(Zingg et al., 2017, Neuron; Zingg et al., 2020, J Neurosci; Zingg et al., 2022, Curr Protoc)

**最重要的读图规则：**“从 A 区看到 B 区的标记轴突”支持解剖投射，“从 B 区逆行标记到 A 区的胞体”支持存在可被该工具识别的 B 投射来源；这两个结论都**不自动等于**“A 区某个细胞与 B 区某个细胞形成已证实的单突触功能连接”。(Oh et al., 2014, Nature; Cushnie et al., 2020, J Neurosci Methods)

## 原理与操作流程

### 1. 载体是什么：衣壳、载荷与标记信号

- \*\*重组 AAV（rAAV）\*\*一般由病毒蛋白衣壳、反向末端重复序列（ITR）夹持的表达盒组成；研究常用载体通常去除了野生型 AAV 的主要复制相关编码功能。衣壳影响细胞进入、组织转导和部分逆行摄取特征，载荷则决定细胞表达何种报告分子、传感器或效应器。(Haery et al., 2019, Front Neuroanat; Challis et al., 2022, Annu Rev Neurosci)
- **报告信号**可以是 GFP、tdTomato、mCherry 或经核定位／膜定位／轴突定位修饰的标记物；也可以先递送 Cre/Flp，再借助另一个重组酶依赖报告系统产生信号。记录到的荧光，本质上是**转基因产物及其在组织内的分布**，不是神经递质释放或突触电流的直接读数。(Harris et al., 2012, Curr Protoc Neurosci; Fenno et al., 2014, Nat Methods)
- **载荷容量有限**：常规单链 AAV 的有效包装规模约为 4.7 kb 的量级，过量设计可能导致截短与表达异常。自互补 AAV（scAAV）可改变表达起始动力学，但以更小的可装载有效载荷为代价；实际表达盒完整性应按构建体验证。(Wu et al., 2010, Mol Ther; Aschauer et al., 2013, PLoS One)

### 2. 常见示踪设计：回答不同方向的问题

| 设计 | 基本逻辑 | 直接可读出的结果 | 必须警惕 |
| --- | --- | --- | --- |
| **常规局部顺行 AAV** | 在 A 区转导源细胞并表达可填充胞体和轴突的报告蛋白 | A 区中被转导的细胞及其可见轴突在 B/C 等目标区的分布 | 纤维经过与末梢终止不能仅由区域内的光点判定；不是自动跨突触 |
| **逆行 AAV（如 rAAV2-retro）** | 在 B 区利用投射轴突末梢摄取，使上游 A/C 区投射源胞体表达报告蛋白 | 被该载体识别、向 B 区投射的候选细胞群 | 不同通路的摄取效率不等；注射区局部转导与顺行标记可能共存 |
| **投射 × 遗传交叉定位** | 将逆行 Cre/Flp 与源区 Cre/Flp 依赖报告载体结合，或与特定驱动动物组合 | 满足“位置／投射／遗传条件”交集的细胞及其投射 | 重组酶驱动范围、病毒共同转导率和非预期漏表达 |
| **特殊 AAV1 跨神经元标记** | 在已验证体系中，使用 AAV1 相关策略向下游神经元递送重组酶信号 | 特定条件下获得标记的候选下游细胞 | AAV1 可能兼具逆行转导；双向连接及非突触传播需要排查 |

(Harris et al., 2012, Curr Protoc Neurosci; Tervo et al., 2016, Neuron; Zingg et al., 2022, Curr Protoc; Han et al., 2023, Nat Commun)

### 3. “细胞类型特异”由谁决定？

靶向不是单靠“某种血清型”就自动获得的：**衣壳的转导倾向**、**启动子／增强子的表达选择性**、**Cre/Flp 等重组酶的真实分布**和**注射位置**共同决定最终标记群体。比如 hSyn 倾向于神经元表达，但不等于精确限定某一种神经元亚型；某个转基因驱动系也可能与预期标记分布不完全一致。(Aschauer et al., 2013, PLoS One; Haery et al., 2019, Front Neuroanat)

交叉遗传工具如 INTRSECT、ConVERGD 可以增加条件特征，提高群体定位能力，但这类“条件性的精密”仍需以组织学和阴性对照检验，不能仅根据表达盒名称接受其特异性。(Fenno et al., 2014, Nat Methods; Hughes et al., 2024, Nat Neurosci; Fischer et al., 2019, PNAS)

### 4. 从研究问题到数据的概念流程

1. **界定假说**：要测的是“源区输出去向”、“靶区输入来源”还是“同时具有某种分子身份和投射方向的细胞”。
2. **确定操作性定义**：预先界定脑区边界、细胞类型、投射终止区域、阳性标记阈值、拟做的阴性对照与排除条件。
3. **选择报告体系**：根据示踪方向、表达谱、研究物种、载荷大小和是否需要交叉遗传约束选择已发表验证的 AAV 设计。
4. **进行定点递送与适当表达期观察**：AAV 信号通常不是即刻成像读出；须依据所选载体和组织条件确定采样窗口，而不是将固定时间当作通用标准。
5. **组织学与三维定位**：检查源区、注射扩散、靶区轴突、被标记胞体，并在适用时结合连续切片、光片／双光子成像及脑图谱配准。
6. **质量控制与统计**：保留样本层级、批次与解剖信息，尽可能用独立标记或功能实验验证关键投射。(Harris et al., 2012, Curr Protoc Neurosci; Oh et al., 2014, Nature; Lin et al., 2018, Nat Methods)

这是一条**科研设计与核验路径**，不是可跨物种、跨脑区直接套用的标准化注射参数配方。

## 能回答什么，不能回答什么？

| 观察或推断 | AAV 示踪支持到什么程度 | 不能直接据此断言什么 |
| --- | --- | --- |
| 源区某类细胞有哪些远距轴突分布 | 使用局部报告载体可观察报告阳性轴突的空间走向和候选终止区 | 不能单凭荧光断言每条轴突在目标区形成有效突触 |
| 哪些胞体向某区域投射 | 逆行转导型 AAV 可标记能被该载体摄取并表达的投射源细胞 | 阴性标记不等于没有投射；阳性细胞数不等于全部投射神经元数 |
| 投射的空间组织和层次 | 可构建脑区级投射矩阵、层状终末分布及候选前馈／反馈模式 | 图谱层级往往包含归一化、阈值、配准和模型假设 |
| 单神经元轴突形态 | 稀疏标记配合三维重建可解析分支和多目标投射 | 稀疏样本的典型形态不能直接视为全部同类细胞的统计分布 |
| 候选跨突触下游神经元 | 仅部分经过专门验证的 AAV1／相关新工具能够在特定条件下提供证据 | 不能认为任意 AAV 载体均具有单突触、单向、无偏倚传播 |
| 神经环路中的因果作用 | 解剖结果可指导进一步光遗传、膜片钳、钙成像或干预设计 | 静态投射图**本身不证明**突触电流、方向性信息传递或行为必要性 |

(Oh et al., 2014, Nature; Harris et al., 2019, Nature; Lin et al., 2018, Nat Methods; Zingg et al., 2020, J Neurosci; Cushnie et al., 2020, J Neurosci Methods)

**直接读数、代理变量、解释层级：**

- **直接读数**：组织切片或透明化样本中的报告阳性胞体、纤维、末梢样结构的数量、位置、形状及荧光信号。
- **代理变量**：阳性轴突长度、投射体积、终末场密度、按区域统计的逆行阳性胞体数。它们依赖转导、表达、显微采样、背景扣除和分割算法，不能跨实验直接当作“连接强度”。
- **推断层**：脑区 A→B 的候选解剖投射，以及投射群体的特征；A 与 B 的确切突触配对或行为因果性须有附加证据。(Oh et al., 2014, Nature; Harris et al., 2019, Nature; Ruigrok, 2026, Cerebellum)

**关键非等价式：**“轴突在 B 区出现 ≠ 已证实与 B 区指定神经元形成突触”；“逆行未标记 ≠ 绝无输入”；“标记量更高 ≠ 生理影响必然更强”；“Cre 依赖 ≠ 绝对零漏表达”。(Cushnie et al., 2020, J Neurosci Methods; Botterill et al., 2021, eNeuro; Ruigrok, 2026, Cerebellum)

## 空间、时间尺度与适用对象

### 空间尺度

- **细胞—轴突层面**：组织学成像可定位被转导的胞体、轴突、分支与末梢样结构；足够稀疏的标记和高分辨成像还可供单神经元投射重建。(Lin et al., 2018, Nat Methods; Winnubst et al., 2019, Cell)
- **脑区—全脑层面**：系统化注射、连续切片成像和标准图谱配准可形成小鼠中尺度投射资源；所谓“连接矩阵”是依技术流程构建的结构指标，并非完整突触级连接组。(Oh et al., 2014, Nature; Hintiryan et al., 2016, Nat Neurosci)
- **突触层面**：常规 AAV 荧光标记本身不具有电子显微镜的突触结构判定力；若研究问题必须落到确定的前后突触细胞接触，应选用电子显微重建、适当的跨突触工具或电生理交叉验证。(Wickersham et al., 2007, Neuron; Petreanu et al., 2007, Nat Neurosci)

### 时间尺度

AAV 依赖基因转导与表达，适合**非即时、数周量级的解剖示踪观察**，部分方案可开展更长期的表达观察；可检测到胞体与远距轴突的具体时间取决于载体类型、表达调控元件、组织、年龄及测量方式，不能硬性套用同一等待天数。自互补设计可改变起始表达速度，但有载荷容量取舍。(Aschauer et al., 2013, PLoS One; Haery et al., 2019, Front Neuroanat)

### 物种、组织及外推

- **小鼠**是顺行图谱与逆行 AAV 方法证据最丰富的研究体系之一；转基因驱动系和标准脑图谱有利于细胞类型选择与复现。(Oh et al., 2014, Nature)
- **非人灵长类**已有逆行 rAAV2-retro 使用与评估，但不能从啮齿类的效率直接推定灵长类所有投射；恒河猴研究发现部分已知连接的标记缺失。(Cushnie et al., 2020, J Neurosci Methods)
- **同种动物的不同遗传背景**也可能改变某些衣壳的 CNS 转导效率，特别是系统递送载体。工程化 AAV-PHP.eB 等在所测试小鼠体系表现出增强转导，但这不等于所有品系和物种都能获得同样效率；局部／全身给药得到的转导谱不能混用。(Foust et al., 2009, Nat Biotechnol; Chan et al., 2017, Nat Neurosci; Hordeaux et al., 2018, Mol Ther)
- 对**人类活体**不能把动物病毒示踪图谱当作直接测得的人脑个体连接图；研究伦理、物种差异和组织样本条件使其主要保持在实验体系的方法论范畴。

## 质量控制与典型伪迹

下表的“核验动作”是**质量控制建议**，不应误写成已经通过实验验证的普遍充分条件。(Haery et al., 2019, Front Neuroanat; Challis et al., 2022, Annu Rev Neurosci)

| 可能的问题 | 为什么会使结论偏移 | 核验思路 |
| --- | --- | --- |
| **注射点偏移／跨脑区扩散** | 把相邻区域的投射混入源区或靶区 | 每只动物展示注射中心、范围及排除标准；必要时分层分析 |
| **局部转导与远程逆行标记混杂** | 靶区注射同时产生下游轴突标记，方向解释混乱 | 分别记录注射位点胞体、远端胞体和终末场；核查路径方向 |
| **血清型与回路偏好** | 不同细胞与通路接受转导的概率不同，阴性结果可能是假阴性 | 对同一靶区进行经验证的替代示踪法交叉检查，不把单一衣壳当作金标准 |
| **“经过纤维”误作终末** | 区域内的轴突不必在该处终止或形成突触 | 结合末梢形态、终末标志物与高分辨／电生理检查 |
| **表达量与光学强度差异** | 亮度受启动子、拷贝、组织透明化和成像条件影响 | 尽可能统一采集／阈值，保留原始图像、阴性背景与批次信息 |
| **Cre/Flp 或 DIO/FLEX 漏表达** | 意料之外的细胞也出现可检测信号，放大染色可能强化假阳性 | 加入 Cre 阴性或相应重组酶阴性对照，验证驱动系与报告基因交集 |
| **共转导／交叉策略不完全** | 有真实投射但其中一环未获得病毒，交集群体被低估 | 显示各组成信号和交集比例，报告阴性样本与失败样本 |
| **跨突触与逆行／非突触扩散混淆** | 在目标区观察到新标记胞体的来源可能不唯一 | 在单向回路测试，设置传递／逆行适当对照，谨慎用“跨突触”术语 |
| **组织成像与配准误差** | 切片不连续、脑区边界失配、亮度阈值不同改变投射矩阵 | 使用统一脑区图谱、人工抽查配准与区域标注，保留预处理版本 |
| **载荷超容或制备差异** | 基因组片段化或批次差异影响表达量和靶向谱 | 核实表达盒大小、载体身份与实验批次，避免只以标称滴度推断有效表达 |
| **细胞损伤与组织反应** | 注射本身可能改变局部组织状态及观测样本 | 设置操作和报告载体对照，记录组织状态及明显异常 |

(Aschauer et al., 2013, PLoS One)

**证据支持的典型反例与边界：**

- **逆行假阴性**：灵长类 rAAV2-retro 实验中，若干已知直接输入区域没有被标记，说明不能用单一载体的“未见阳性胞体”排除解剖通路。(Cushnie et al., 2020, J Neurosci Methods)
- **Cre 非依赖背景**：关于 DIO/FLEX 的两组研究分别从载体机制和野生型动物实验报告漏表达及放大染色后的非预期信号，提示必须设置阴性对照，而不是假定条件表达天然完美。(Fischer et al., 2019, PNAS; Botterill et al., 2021, eNeuro)
- **衣壳的物种／品系外推失败**：系统性转导增强变体 AAV-PHP.B 在部分小鼠品系或灵长类不复制同样的 CNS 效率，说明“高效率”的研究结论须绑定物种、遗传背景、给药路线。(Deverman et al., 2016, Nat Biotechnol; Hordeaux et al., 2018, Mol Ther)
- **跨突触方向性不纯**：AAV1 的顺行跨神经元应用可伴随逆行摄取，因此在双向联络网络中，得到下游阳性细胞不必意味着严格顺行的单突触起源。(Zingg et al., 2022, Curr Protoc)

### 建议报告的最低信息集

论文／节点里至少记录：动物种属及品系、年龄范围、性别、脑区与解剖界限、衣壳身份、报告载荷与启动子、重组酶驱动系、注射方式／范围、表达观察窗口、组织学及成像方法、数据筛选阈值、样本与批次层级、阴性／阳性对照、异常样本排除依据。该清单用于促进**方法透明与可复查**，不等价于任何学会认证标准。(Haery et al., 2019, Front Neuroanat; Ruigrok, 2026, Cerebellum)

## 代表性实验或应用

### 1. 大规模顺行投射图谱：Allen 小鼠脑连接资源

Oh 等整合 AAV-EGFP 局部投射标记、连续双光子成像和标准脑图谱配准，系统描述脑区级的长程轴突投射，形成可复用的中尺度结构资源；后来 Harris 等在皮层—丘脑层级上进一步引入细胞类型和层次信息，用投射模式提出网络层级模型。(Oh et al., 2014, Nature; Harris et al., 2019, Nature)

**支持**：可规模化比较的脑区投射分布。**限制**：配准、注射覆盖、光学分割、阈值和模型分类都影响最终矩阵；同一项目后续扩展不是完全独立的外部重复。

### 2. 跨团队的皮质—纹状体中尺度投射研究

Hintiryan 等系统绘制皮质—纹状体投射并据此辨别纹状体内部的不同投射域。与 Allen 图谱的广泛结构观察构成**跨团队、不同研究问题下的方法汇合**，但两个图谱的分区、采集体系与分析规则并不完全一致，不能把其数字直接拼接成无偏倚的一张统一网络。(Hintiryan et al., 2016, Nat Neurosci; Oh et al., 2014, Nature)

### 3. 逆行工程衣壳与回路选择性：rAAV2-retro → AAV11

Tervo 等开发 rAAV2-retro，以改善向投射源神经元递送报告分子和效应器的能力；Cushnie 等随后在恒河猴回路中评估了其**部分已知输入缺失**以及下游终末场标记问题。Han 等提出 AAV11，并在不同投射回路发现与 rAAV2-retro 互补的标记偏好。(Tervo et al., 2016, Neuron; Cushnie et al., 2020, J Neurosci Methods; Han et al., 2023, Nat Commun)

**支持**：逆行 AAV 是受衣壳与回路条件制约的可扩展分子工具。**不能证明**：某种衣壳可以完整、等概率地回收任意靶区所有真实输入神经元。

### 4. 细胞类型 × 投射的单神经元形态重建

Lin 等的双 AAV 稀疏标记方案将细胞类型和投射信息相结合，以更容易分辨单个神经元的全脑轴突形态；Winnubst 等的大规模单神经元投射重建揭示相似脑区内部也存在复杂投射差异。(Lin et al., 2018, Nat Methods; Winnubst et al., 2019, Cell)

**支持**：单细胞形态与长程分支结构。**限制**：这是标记与重建样本，不是对所有同类神经元的无偏抽样，也不代表完整电镜突触图。

### 5. 特殊的 AAV1 顺行跨神经元标记与随后争议澄清

Zingg 等在皮质—上丘相关通路使用 AAV1 介导的顺行跨神经元标记，后续从突触偏好等方面进行方法学检验。2022 年的流程文献明确指出 AAV1 仍有逆行传播问题，尤其不宜在互返投射占主导的线路中直接把阳性下游细胞解释为严格单向突触靶细胞。(Zingg et al., 2017, Neuron; Zingg et al., 2020, J Neurosci; Zingg et al., 2022, Curr Protoc)

**支持**：某些条件下的下游细胞标记。**限制**：不同类型的跨神经元转移证据仍需独立验证；AAV1 的结论不能推广为全部 rAAV 的共性。

### 6. 方法学负结果、外推检验与新工具

Fischer 与 Botterill 等以不同方法报告重组酶依赖 AAV 漏表达；Hordeaux 等以跨品系／物种资料指出系统递送的衣壳优势不总是通用。2025 年 Rivera 等又提出由 AAV 递送、但主要**依靠工程蛋白**实现顺行跨突触标记的 ATLAS，提示“载体用 AAV”不意味着“跨突触的是 AAV 颗粒”。2026 年的综述强调更广泛的病毒示踪误读与谨慎复核要求。(Fischer et al., 2019, PNAS; Botterill et al., 2021, eNeuro; Hordeaux et al., 2018, Mol Ther; Rivera et al., 2025, Nat Methods; Ruigrok, 2026, Cerebellum)

**支持**：多种独立方法揭示了定位精度、方向性和外推限制。**限制**：ATLAS 仍有适用对象与效率边界；方法评论不是一项新的独立重复实验。

## 与其他方法的关系

| 方法 | 与 AAV 示踪的互补性 | 需要谨慎区分 |
| --- | --- | --- |
| **常规非病毒顺／逆行示踪剂**（如 CTB、荧光微球、PHA-L） | 用不同摄取和运输机制交叉验证注射区与投射来源、排查病毒转导偏好 | 某种非病毒标记也有独立的摄取偏差，不是绝对金标准 |
| **糖蛋白缺失狂犬病毒及单级逆行跨突触工具** | 在适当辅助系统下回答候选突触前输入；较常规 AAV 逆行转导接近“一级突触前细胞”问题 | 病毒复制、辅助系统与样本窗口带来不同选择偏倚；“逆行病毒”不等于“任何时候都是跨突触病毒” |
| **ATLAS 等工程蛋白跨突触标记** | 提供限定实验体系内的顺行单级跨突触候选方案 | 虽可经 AAV 表达，但蛋白跨突触机制与病毒颗粒跨突触不同；需评估细胞类型适用性 |
| **光遗传辅助膜片钳／CRACM** | 测量源区轴突刺激引起的突触后电流，补充单纯结构标记不能提供的生理连接证据 | 光刺激可产生网络间接效应，需专门阻断和细胞定位控制 |
| **电镜／突触超微结构重建** | 对特定细胞接触提供更细的突触形态层级验证 | 取样体积、耗时、跨尺度配准限制全脑覆盖 |
| **组织透明化、全脑连续成像、计算配准** | 将局部 AAV 报告扩展成连续轴突图与可对照的脑区级资源 | 影像连续性与荧光清晰度不自动赋予突触传递证据 |
| **分子细胞图谱／单细胞测序** | 为投射群体赋予转录身份、把连接形态与分子型关联 | RNA 身份不等于轴突真实终止位置，也不等于功能因果性 |

(Wickersham et al., 2007, Nat Methods; Wickersham et al., 2007, Neuron; Petreanu et al., 2007, Nat Neurosci; Murakami et al., 2018, Nat Neurosci; Rivera et al., 2025, Nat Methods)

**方法选择原则：** 想找“源区投往哪里”，优先规划顺行轴突示踪；想找“靶区由谁投来”，优先考虑逆行转导／传统逆行标记；想找“确切突触前后搭档”，应引入经过条件验证的单级跨突触方法或突触结构证据；想验证“有效的生理信号或行为作用”，再加入电生理、活动记录与干预实验。没有一种 AAV 成像结果能独立覆盖这些所有层级。(Harris et al., 2012, Curr Protoc Neurosci; Tervo et al., 2016, Neuron; Petreanu et al., 2007, Nat Neurosci)

## 相关节点

以下是**候选相关节点词**（均为普通文本；本次仅提供了本节点模板，无法验证 Vault 中对应文件是否存在及其公开状态，所以不生成未经核实的 Obsidian 双链）：

- **示踪方向与连通性**：顺行示踪、逆行示踪、跨突触示踪、神经环路解剖连接、结构连接组、突触连接、轴突运输。
- **载体与靶向原理**：腺相关病毒（AAV）、病毒衣壳血清型、AAV2-retro、AAV11、Cre-loxP 系统、Flp-FRT 系统、细胞类型特异性启动子。
- **互补测量方法**：光遗传学、膜片钳记录、狂犬病毒单突触示踪、组织透明化、光片显微镜、脑图谱配准、电子显微镜连接组学。
- **证据与偏倚**：可重复性、假阴性、测量有效性、选择偏倚、相关与因果、交叉验证。

**人工审核重点：** 先确认已有的“病毒示踪／顺行示踪／逆行示踪”节点命名与是否拆分子节点，再核对上述候选的真实 Vault 路径、公开计划及别名；确认后才补 Wikilink。检查是否将“跨突触 AAV1 标记”独立设为方法节点，以免与常规非跨突触 AAV 示踪混成同一操作性定义。

## 参考资料

**编排规则**：正文使用 `(作者 et al., 年份, 期刊简称)`；同一年同作者组而期刊不同的论文，以期刊简称区分。每篇均提供可单独访问的 DOI 入口；“资料性质”说明是原始实验、方法论文还是综述，“主要支持与限制”强调不可外推的部分。以下参考资料按**证据主题**组织，不按引用先后强行排序。

| 正文引用 | 作者、年份及论文题名 | 期刊与卷页 | DOI／永久链接 | 资料性质 | 主要支持与限制 |
| --- | --- | --- | --- | --- | --- |
| `(Harris et al., 2012, Curr Protoc Neurosci)` | Harris JA, Oh SW, Zeng H (2012). Adeno-associated viral vectors for anterograde axonal tracing with fluorescent proteins in nontransgenic and cre driver mice. | Curr Protoc Neurosci, Ch. 1, Unit 1.20 | [DOI](https://doi.org/10.1002/0471142301.ns0120s59) | 方法流程 | 顺行 AAV 标记与 Cre 驱动小鼠流程；是操作性资料，不证明任何特定脑区具有功能性突触连接。 |
| `(Oh et al., 2014, Nature)` | Oh SW, Harris JA, Ng L, et al. (2014). A mesoscale connectome of the mouse brain. | Nature 508:207–214 | [DOI](https://doi.org/10.1038/nature13186) | 大规模原始研究／资源 | AAV-EGFP 顺行投射与连续双光子成像构建小鼠脑中尺度投射矩阵；注射范围和投射阈值影响估计。 |
| `(Hintiryan et al., 2016, Nat Neurosci)` | Hintiryan H, Foster NN, Bowman I, et al. (2016). The mouse cortico-striatal projectome. | Nat Neurosci 19:1100–1114 | [DOI](https://doi.org/10.1038/nn.4332) | 独立团队投射图谱 | 皮质—纹状体投射的中尺度组织；与 Allen 图谱构成跨团队方法汇合，而非逐一连接的完全独立复制。 |
| `(Harris et al., 2019, Nature)` | Harris JA, Mihalas S, Hirokawa KE, et al. (2019). Hierarchical organization of cortical and thalamic connectivity. | Nature 575:195–202 | [DOI](https://doi.org/10.1038/s41586-019-1716-z) | 原始研究／资源扩展 | 利用细胞类型与皮层层次约束的 AAV 投射图谱推断解剖层级；前馈／反馈含模型判据。 |
| `(Tervo et al., 2016, Neuron)` | Tervo DGR, Hwang BY, Viswanathan S, et al. (2016). A Designer AAV Variant Permits Efficient Retrograde Access to Projection Neurons. | Neuron 92:372–382 | [DOI](https://doi.org/10.1016/j.neuron.2016.09.021) | 载体开发／原始验证 | 工程化 rAAV2-retro 增强多条通路的逆行转导；效率不是所有细胞类型与通路通用的常数。 |
| `(Cushnie et al., 2020, J Neurosci Methods)` | Cushnie AK, El-Nahal HG, Bohlen MO, et al. (2020). Using rAAV2-retro in rhesus macaques: Promise and caveats for circuit manipulation. | J Neurosci Methods 345:108859 | [DOI](https://doi.org/10.1016/j.jneumeth.2020.108859) | 跨物种原始评价 | 恒河猴部分已知输入未被逆行标记，且可见顺行终末标记；不能据阴性标记排除投射。 |
| `(Han et al., 2023, Nat Commun)` | Han Z, Luo N, Ma W, et al. (2023). AAV11 enables efficient retrograde targeting of projection neurons and enhances astrocyte-directed transduction. | Nat Commun 14:3792 | [DOI](https://doi.org/10.1038/s41467-023-39554-7) | 替代载体原始比较 | AAV11 与 rAAV2-retro 逆行偏好随回路而异；一些脑区验证不等于广泛物种通用。 |
| `(Aschauer et al., 2013, PLoS One)` | Aschauer DF, Kreuz S, Rumpel S (2013). Analysis of Transduction Efficiency, Tropism and Axonal Transport of AAV Serotypes 1, 2, 5, 6, 8 and 9 in the Mouse Brain. | PLoS One 8:e76310 | [DOI](https://doi.org/10.1371/journal.pone.0076310) | 血清型对照实验 | 血清型、脑区和细胞类型影响转导与轴突运输；不能把单一血清型标签当作绝对细胞特异性。 |
| `(Foust et al., 2009, Nat Biotechnol)` | Foust KD, Nurre E, Montgomery CL, et al. (2009). Intravascular AAV9 preferentially targets neonatal neurons and adult astrocytes. | Nat Biotechnol 27:59–65 | [DOI](https://doi.org/10.1038/nbt.1515) | 原始实验／发育阶段比较 | 静脉给药 AAV9 的 CNS 靶向受年龄及给药方式影响；不是局部示踪的固定转导规律。 |
| `(Wu et al., 2010, Mol Ther)` | Wu Z, Yang H, Colosi P (2010). Effect of Genome Size on AAV Vector Packaging. | Mol Ther 18:80–86 | [DOI](https://doi.org/10.1038/mt.2009.255) | 载体基因组测定 | AAV 装载容量有限，过大载荷可能截短；实际应用需验证载荷完整性。 |
| `(Fenno et al., 2014, Nat Methods)` | Fenno LE, Mattis J, Ramakrishnan C, et al. (2014). Targeting cells with single vectors using multiple-feature Boolean logic. | Nat Methods 11:763–772 | [DOI](https://doi.org/10.1038/nmeth.2996) | 交叉遗传工程 | Cre/Flp 等逻辑组合提高群体靶向的条件性；仍要检查重组系统本身的表达范围。 |
| `(Fischer et al., 2019, PNAS)` | Fischer KB, Collins HK, Callaway EM (2019). Sources of off-target expression from recombinase-dependent AAV vectors and mitigation with cross-over insensitive ATG-out vectors. | PNAS 116:27001–27010 | [DOI](https://doi.org/10.1073/pnas.1915974116) | 伪迹机理与改进 | 说明 FLEX/DIO 的重组酶非依赖性漏表达来源；并非所有构建体具有相同漏表达程度。 |
| `(Botterill et al., 2021, eNeuro)` | Botterill JJ, Khlaifia A, Walters BJ, et al. (2021). Off-Target Expression of Cre-Dependent Adeno-Associated Viruses in Wild-Type C57BL/6J Mice. | eNeuro 8:ENEURO.0363-21.2021 | [DOI](https://doi.org/10.1523/ENEURO.0363-21.2021) | 独立方法学反例 | 野生型小鼠出现 DIO 载体非预期表达，抗体放大更易显现；强调 Cre 阴性对照。 |
| `(Haery et al., 2019, Front Neuroanat)` | Haery L, Deverman BE, Matho KS, et al. (2019). Adeno-Associated Virus Technologies and Methods for Targeted Neuronal Manipulation. | Front Neuroanat 13:93 | [DOI](https://doi.org/10.3389/fnana.2019.00093) | 方法综述／设计建议 | 集中比较衣壳、给药、调控元件与靶向系统；总结性建议并非统一实验结果。 |
| `(Challis et al., 2022, Annu Rev Neurosci)` | Challis RC, Kumar SR, Chen X, et al. (2022). Adeno-Associated Virus Toolkit to Target Diverse Brain Cells. | Annu Rev Neurosci 45:447–469 | [DOI](https://doi.org/10.1146/annurev-neuro-111020-100834) | 系统性工具综述 | 概括衣壳与载荷双层工程及细胞选择性；不能替代特定回路的本地验证。 |
| `(Lin et al., 2018, Nat Methods)` | Lin R, Wang R, Yuan J, et al. (2018). Cell-type-specific and projection-specific brain-wide reconstruction of single neurons. | Nat Methods 15:1033–1036 | [DOI](https://doi.org/10.1038/s41592-018-0184-y) | 双 AAV 稀疏标记方法 | 以投射限定的稀疏标记重建单神经元形态；抽样重建不能直接解释为总体连接概率。 |
| `(Winnubst et al., 2019, Cell)` | Winnubst J, Bas E, Ferreira TA, et al. (2019). Reconstruction of 1,000 Projection Neurons Reveals New Cell Types and Organization of Long-Range Connectivity in the Mouse Brain. | Cell 179:268–281.e13 | [DOI](https://doi.org/10.1016/j.cell.2019.07.042) | 单神经元投射资源 | 跨脑区的单神经元树突／轴突形态显示细胞间差异；不是对每条突触的 EM 证实。 |
| `(Zingg et al., 2017, Neuron)` | Zingg B, Chou XL, Zhang ZG, et al. (2017). AAV-Mediated Anterograde Transsynaptic Tagging: Mapping Corticocollicular Input-Defined Neural Pathways for Defense Behaviors. | Neuron 93:33–47 | [DOI](https://doi.org/10.1016/j.neuron.2016.11.045) | 特定体系跨突触原始研究 | 在指定回路使用 AAV1 相关跨神经元标记；不等于常规 AAV 示踪天然具有严格顺行突触特异性。 |
| `(Zingg et al., 2020, J Neurosci)` | Zingg B, Peng B, Huang J, et al. (2020). Synaptic Specificity and Application of Anterograde Transsynaptic AAV for Probing Neural Circuitry. | J Neurosci 40:3250–3267 | [DOI](https://doi.org/10.1523/JNEUROSCI.2158-19.2020) | 后续原始机制验证 | 对 AAV1 跨突触标记的突触偏好及局限开展实验；不能把标记数量视为普遍的突触强度定量。 |
| `(Zingg et al., 2022, Curr Protoc)` | Zingg B, Dong HW, Tao HW, Zhang LI (2022). Application of AAV1 for Anterograde Transsynaptic Circuit Mapping and Input-Dependent Neuronal Cataloging. | Curr Protoc 2:e339 | [DOI](https://doi.org/10.1002/cpz1.339) | 方法流程／适用边界 | 明确 AAV1 可伴随逆行传播，双向回路难于消歧；属特殊转神经元方案而非默认属性。 |
| `(Deverman et al., 2016, Nat Biotechnol)` | Deverman BE, Pravdo PL, Simpson BP, et al. (2016). Cre-dependent selection yields AAV variants for widespread gene transfer to the adult brain. | Nat Biotechnol 34:204–209 | [DOI](https://doi.org/10.1038/nbt.3440) | 衣壳工程原始研究 | 系统给药脑转导变体的筛选；不是逆行示踪或突触传递验证。 |
| `(Chan et al., 2017, Nat Neurosci)` | Chan KY, Jang MJ, Yoo BB, et al. (2017). Engineered AAVs for efficient noninvasive gene delivery to the central and peripheral nervous systems. | Nat Neurosci 20:1172–1179 | [DOI](https://doi.org/10.1038/nn.4593) | 衣壳工程原始研究 | AAV-PHP.eB/PHP.S 等扩展系统靶向的可能性；部分优势依赖遗传背景。 |
| `(Hordeaux et al., 2018, Mol Ther)` | Hordeaux J, Wang Q, Katz N, et al. (2018). The Neurotropic Properties of AAV-PHP.B Are Limited to C57BL/6J Mice. | Mol Ther 26:664–668 | [DOI](https://doi.org/10.1016/j.ymthe.2018.01.018) | 跨品系／物种反例 | 系统 AAV-PHP.B 在特定小鼠品系的 CNS 优势不可径直外推至其他品系或灵长类。 |
| `(Hughes et al., 2024, Nat Neurosci)` | Hughes AC, Pittman BG, Xu B, et al. (2024). A single-vector intersectional AAV strategy for interrogating cellular diversity and brain function. | Nat Neurosci 27:1400–1410 | [DOI](https://doi.org/10.1038/s41593-024-01659-7) | 新型交叉遗传方法 | ConVERGD 实现更复杂的条件性表达；不是连接或行为因果的自动保证。 |
| `(Rivera et al., 2025, Nat Methods)` | Rivera JF, Huang H, Weng W, et al. (2025). ATLAS: a rationally designed anterograde transsynaptic tracer. | Nat Methods 22:1101–1111 | [DOI](https://doi.org/10.1038/s41592-025-02670-x) | 替代工具／原始验证 | 利用工程蛋白介导特定体系的顺行跨突触报告；不是普通 AAV 颗粒自身的跨突触能力，广泛外推仍需检验。 |
| `(Wickersham et al., 2007, Neuron)` | Wickersham IR, Lyon DC, Barnard RJO, et al. (2007). Monosynaptic Restriction of Transsynaptic Tracing from Single, Genetically Targeted Neurons. | Neuron 53:639–647 | [DOI](https://doi.org/10.1016/j.neuron.2007.01.033) | 方法对照／原始研究 | 糖蛋白缺失狂犬病毒的单级逆行跨突触连接追踪；工具机理与 AAV 投射示踪不同。 |
| `(Wickersham et al., 2007, Nat Methods)` | Wickersham IR, Finke S, Conzelmann KK, Callaway EM (2007). Retrograde neuronal tracing with a deletion-mutant rabies virus. | Nat Methods 4:47–49 | [DOI](https://doi.org/10.1038/nmeth999) | 逆行病毒追踪方法 | 缺失突变狂犬病毒可作逆行形态标记；不要与具辅助系统的单级跨突触狂犬追踪混同。 |
| `(Petreanu et al., 2007, Nat Neurosci)` | Petreanu L, Huber D, Sobczyk A, Svoboda K (2007). Channelrhodopsin-2-assisted circuit mapping of long-range callosal projections. | Nat Neurosci 10:663–668 | [DOI](https://doi.org/10.1038/nn1891) | 功能连接方法 | 轴突光刺激结合膜片钳验证功能性输入；与结构可达性不同，需控制刺激扩散及多突触影响。 |
| `(Murakami et al., 2018, Nat Neurosci)` | Murakami TC, Mano T, Saikawa S, et al. (2018). A three-dimensional single-cell-resolution whole-brain atlas using CUBIC-X expansion microscopy and tissue clearing. | Nat Neurosci 21:625–637 | [DOI](https://doi.org/10.1038/s41593-018-0109-1) | 成像互补／原始方法 | 说明组织透明化扩增与全脑观察能力；并非专为 AAV 投射开展的直接重复验证。 |
| `(Ruigrok, 2026, Cerebellum)` | Ruigrok TJH (2026). Viral Tracing Gone Viral: Expanded Possibilities Call for Increased Caution in Describing Cerebellar Network Connections. | Cerebellum 25:147 | [DOI](https://doi.org/10.1007/s12311-026-02089-w) | 新近方法学批判综述 | 强调病毒示踪的方向、伪迹与连接误判风险；主要举证来自小脑回路，不是独立的 AAV 载体性能试验。 |

### 文献使用与核验说明

1. **原始实验优先于综述引申**：对方向性、跨突触性、漏表达、品系差异分别引用了直接研究；综述用于方法概览，不将作者建议冒充普遍实证。
2. **“多篇文献”不等于“同一结果已独立复现”**：Allen 项目内部 2014 与 2019 的扩展、AAV1 同一研究团队的后续研究与其他团队图谱，应分开标为资源扩展、机制复核或跨团队方法汇合。
3. **新近来源定位**：2024 年交叉靶向研究、2025 年 ATLAS 原始论文及 2026 年小脑病毒示踪批判综述，分别代表工具进展、替代方案及边界评论，**均不代表常规 AAV 示踪已经具备无偏的突触级解剖能力**。
4. **未做的验证**：未获得完整 Obsidian Vault，无法验证同名节点、现有双链及拟公开状态；未获得实验原始图像／批次记录，无法核查任何特定实验室的数据重复性。

**审核与发布状态：** 此页为人工待审初稿，`publish: false`。待人工核查来源、双链、命名体系及个别应用方案后，再由你决定是否发布；本次未写入 Obsidian，也未触发 Quartz Syncer。
