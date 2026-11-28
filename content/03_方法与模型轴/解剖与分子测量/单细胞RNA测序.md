---
publish: true
aliases:
  - 单细胞转录组测序
  - 单细胞RNA-seq
  - scRNA-seq
title: 单细胞RNA测序
description: 通过分离单个细胞并测量其RNA表达谱，研究细胞类型、分子状态与群体异质性；其统计分类不自动证明功能、位置或因果机制。
created: 2026-10-16T11:04:50.994Z
tags:
  - 类型/方法
  - 层/观测
---

# 单细胞RNA测序

> **一句话介绍：** 单细胞RNA测序（single-cell RNA sequencing，scRNA-seq）是在单个细胞来源的RNA分子上建立测序文库，获得每个细胞的基因表达谱，从而比较组织中的**细胞分子身份、状态及其异质性**；它直接测量的是经捕获、建库和测序得到的RNA信号，而非细胞功能、突触连接或因果作用。(Tang et al., 2009, Nat Methods; Luecken & Theis, 2019, Mol Syst Biol)

## 快速理解

传统的总体RNA测序（bulk RNA-seq）把许多细胞的RNA混合起来，给出整体平均表达；单细胞RNA测序则尝试保留“每个细胞单独来自哪里”的标签。打个比方：前者告诉你整个合唱团的声音，后者尝试区分每位成员的声部。但这种“声部”是从RNA数据中分析得到的，**不是显微镜下直接看到了所有细胞的解剖与生理特征**。(Tang et al., 2009, Nat Methods; Macosko et al., 2015, Cell; Heumos et al., 2023, Nat Rev Genet)

在神经科学里，一份脑组织样本可能包含不同类型的兴奋性和抑制性神经元、星形胶质细胞、小胶质细胞、少突胶质细胞及其他细胞。scRNA-seq可通过表达模式提出细胞分类、稀有群体或状态变化的**候选解释**，随后用位置、蛋白、形态、电生理或扰动证据来验证。(Zeisel et al., 2015, Science; Tasic et al., 2016, Nat Neurosci; Gouwens et al., 2020, Cell)

**必须区分四个层级：**

1. **原始观测：** 细胞条形码、分子标签、测序reads、基因计数或转录本估计；这些读数仍受捕获效率和技术噪声影响。(Islam et al., 2014, Nat Methods; Zheng et al., 2017, Nat Commun)
2. **统计描述：** 降维、聚类、标记基因、差异表达、细胞组成与批次校正。(Luecken & Theis, 2019, Mol Syst Biol; Heumos et al., 2023, Nat Rev Genet)
3. **模型推断：** 转录组类型、细胞状态连续谱、伪时间、RNA velocity、潜在细胞通讯等；每类推断有特定前提。(Trapnell et al., 2014, Nat Biotechnol; La Manno et al., 2018, Nature)
4. **独立实验证明：** 解剖定位、蛋白表达、电生理性质、形态、突触连接及功能因果，需要补充相应方法。(Cadwell et al., 2016, Nat Biotechnol; Moffitt et al., 2018, Science; Gouwens et al., 2020, Cell)

## 原理与操作流程

### 1. 信号来源：测到什么

实验对象通常是从组织中分离的完整单细胞；常见测量目标是能被特定文库化学方法捕获的RNA，主要为mRNA。RNA经历逆转录、扩增与测序等步骤，之后通过参考基因组/转录组比对或定量构建“基因 × 细胞”的表达矩阵。原始reads、UMI计数与推断的真实分子丰度并非同一件事。(Tang et al., 2009, Nat Methods; Islam et al., 2014, Nat Methods; Zheng et al., 2017, Nat Commun)

\*\*细胞条形码（cell barcode）\*\*用于识别分子所属的候选细胞，\*\*唯一分子标识符（UMI）\*\*用于在特定假设下帮助辨认PCR重复来源。UMI可降低扩增带来的重复计数偏差，**但不能找回未被捕获的RNA**，也不使所有计数自动成为绝对细胞内分子数。(Islam et al., 2014, Nat Methods)

### 2. 技术路线的关键区别

| 路线 | 数据特性与典型用途 | 代价和解释边界 |
| --- | --- | --- |
| **全长/高覆盖路线（如 Smart-seq2）** | 适合单细胞较深的表达测量；在适合的深度和方案下可分析部分转录本结构 | 常偏重较少量细胞，技术与成本条件影响可比性；并不保证穷尽所有剪接事件。(Picelli et al., 2013, Nat Methods) |
| **液滴或其他高通量条码路线（如 Drop-seq、inDrops、Chromium）** | 能并行分析大量细胞，适合细胞群普查；许多常用实现以3′或5′端计数为主 | 通常牺牲完整转录本覆盖；还需控制空液滴、双细胞、环境RNA及测序稀疏性。(Macosko et al., 2015, Cell; Klein et al., 2015, Cell; Zheng et al., 2017, Nat Commun) |
| **细胞核RNA测序（snRNA-seq）** | 从分离的单个细胞核中测量RNA；对部分难解离或冻存的成人脑组织特别有价值 | 采集的是**核内RNA**，不是完整细胞RNA；内含子reads、细胞质转录本缺失与细胞组成偏差须单独考虑。(Lake et al., 2016, Science; Habib et al., 2017, Nat Methods; Bakken et al., 2018, PLOS One) |

**概念边界：** snRNA-seq与scRNA-seq常被合称单细胞/单核转录组，但二者的生物学取样单位和被观测分子不同。脑组织尤其不能把细胞核里未检出某些树突、轴突或细胞质富集RNA直接解释成该神经元在整体上不表达这些基因。(Bakken et al., 2018, PLOS One; Ding et al., 2020, Nat Biotechnol)

### 3. 从样本到结论的分析链

**研究问题与实验设计 → 样本及供体/动物组织处理 → 单细胞或单核获取 → 文库测序 → 细胞识别与计数矩阵 → 质量控制 → 标准化 → 批次评估/数据整合 → 降维与聚类 → 注释与独立验证 → 组间统计/生物学解释。** 该流程用于说明证据形成过程，不代表所有研究只能使用一种算法或统一阈值。(Luecken & Theis, 2019, Mol Syst Biol; Heumos et al., 2023, Nat Rev Genet)

- **从raw reads到矩阵：** 检查条形码和基因归属；液滴数据需鉴别实际细胞与空液滴，snRNA-seq需明确是否将内含子reads纳入定量。(Lun et al., 2019, Genome Biol; Bakken et al., 2018, PLOS One)
- **从矩阵到结构：** 先做基因/细胞质量评估，再选择归一化、特征和低维表示；聚类数、UMAP形状与边界均受分析策略影响。(Hafemeister & Satija, 2019, Genome Biol; DenAdel et al., 2025, Am J Hum Genet)
- **从聚类到细胞类型：** 综合多个marker、已发表图谱、脑区与发育阶段，必要时与组织学、原位检测或其他模态对应；应保留不确定标签，不把每个聚类一律升格为新细胞类型。(Tasic et al., 2018, Nature; Hodge et al., 2019, Nature; Heumos et al., 2023, Nat Rev Genet)
- **从差异到生物学效应：** 区分细胞丰度变化与同一细胞类型内的表达变化，并将供体/动物作为合适的独立生物学重复单位。(Crowell et al., 2020, Nat Commun; Zimmerman et al., 2021, Nat Commun; Squair et al., 2021, Nat Commun)

### 4. 对神经组织特别重要的前分析偏差

组织解离可能触发应激与即时早期基因等非目标表达变化，且易损失形态复杂或脆弱的细胞；核测序可缓解部分解离问题，却引入核/胞质表达差异，不能视为“没有偏差的版本”。(van den Brink et al., 2017, Nat Methods; Bakken et al., 2018, PLOS One; Ding et al., 2020, Nat Biotechnol)

2026年10月的脑组织方法学研究还报告，在其**小鼠单核实验体系**中，取材方式、固定处理与测序平台可改变某些神经元群体的检出和差异表达结果；该文属于刚发表的可引用**早期在线版本**，这些观察应作为额外风险提示而非跨物种、跨平台统一定律。(Ning et al., 2026, BMC Neurosci)

## 能回答什么，不能回答什么？

| 问题 | 可以支持的证据 | 不能直接推出的结论 |
| --- | --- | --- |
| 组织内有哪些分子表达群体？ | 基于测得转录组提出的细胞类型/状态候选及标记基因 | 每个聚类必为独立、稳定且功能分离的细胞类型 |
| 何种基因在某细胞群体中更常检出？ | 有实验设计和统计约束的表达差异、表达率变化 | RNA表达一定对应等量蛋白、受体活性或突触功能 |
| 疾病/干预是否伴随细胞状态改变？ | 供体层面控制后的细胞类型内差异表达、状态与组成变化 | 表达差异由某单个基因直接造成，或是疾病因果机制 |
| 不同脑区/物种有何对应细胞类型？ | 基因表达模式的跨区域或跨物种映射、同源候选 | 细胞的投射模式、形态和电生理在两物种中完全相同 |
| 细胞可能沿哪条发育轨迹变化？ | 基于模型和取样状态的伪时间/方向性假说 | 真正测到了单个细胞随时间转变的连续录像 |
| 两类细胞是否可能通过配体—受体通信？ | 配体/受体转录本共表达与先验网络的**候选相互作用** | 分子真实接触、信号转导成功，或者已经形成突触 |
| 细胞原先位于组织何处、连向何处？ | **常规解离式 scRNA-seq本身通常无法保留** | 单凭转录组定位可证明原位细胞接触或神经通路连接 |
| UMAP上的两群点相距很近说明什么？ | 在选定嵌入算法下表达模式的局部关系 | 真实解剖距离、进化距离或确定的发育谱系距离 |

对细胞状态/分化轨迹可采用伪时间排序和RNA velocity，但**伪时间不是钟表时间**；velocity依赖转录本加工动力学等假设，矢量方向不能脱离模型条件解释为真实未来命运。(Trapnell et al., 2014, Nat Biotechnol; La Manno et al., 2018, Nature)

对脑疾病的单核数据，基因差异与细胞类型变化尤其应考虑病例组成、供体差异、死亡后间隔、脑区取样和细胞回收偏差。单核图谱为发现候选机制提供强工具，但疾病因果关系必须由额外研究确立。(Mathys et al., 2019, Nature; Chen et al., 2024, Nat Med; Heumos et al., 2023, Nat Rev Genet)

## 空间、时间尺度与适用对象

**观测单元与分辨率：** 分析单元为被成功分离、标记并检出的单细胞或细胞核；观察层次为其RNA表达谱，而非单个突触、树突棘或远端轴突的完整转录组。细胞级不等于在原组织中自动具备细胞级**空间定位**。(Bakken et al., 2018, PLOS One; Moffitt et al., 2018, Science; Rodriques et al., 2019, Science)

**时间尺度：** 常规实验形成取样时点的**分子快照**。发育/衰老纵向规律通常借助不同时间点样本、不同供体或计算模型推断；不能把横断面的伪时间重排误称为直接追踪同一细胞的历史。(Trapnell et al., 2014, Nat Biotechnol; Yang et al., 2026, Nature)

**对象与样本：** 可用于细胞系、发育组织、动物脑、人类手术或尸检样本及类器官，但脑区、物种、年龄、疾病状态和组织保存/处理条件必须分别描述。snRNA-seq常适合成熟神经元及冻存组织，仍需评估其核内读数的偏好。(Lake et al., 2016, Science; Habib et al., 2017, Nat Methods; Ding et al., 2020, Nat Biotechnol)

**规模与权衡：** 高通量系统扩大了可采细胞数量，方便寻找稀有表达群，但单细胞检测深度、样本代表性、供体数量与RNA种类覆盖并不能简单地同时最大化；“测了很多细胞”不能替代“有足够独立生物样本”。(Macosko et al., 2015, Cell; Zheng et al., 2017, Nat Commun; Zimmerman et al., 2021, Nat Commun)

**脑区与物种外推：** 同一大类神经元在小鼠与人类皮层可以具有保守的转录组框架，也存在比例、层位和基因表达方面的分歧；图谱标签是可修订的分析分类，不等于跨物种统一的完备细胞本体。(Hodge et al., 2019, Nature; Siletti et al., 2023, Science)

## 质量控制与典型伪迹

### 1. 从实验到分析的风险检查表

| 风险 / 伪迹 | 表现与误判后果 | 推荐的检查与验证方式 |
| --- | --- | --- |
| **解离应激与细胞选择性损失** | 即时早期/应激相关RNA升高；某些脆弱或大型神经元比例偏低 | 明确处理组别、记录组织处理，必要时用snRNA-seq或原位检测交叉核验。(van den Brink et al., 2017, Nat Methods; Ding et al., 2020, Nat Biotechnol) |
| **细胞核与完整细胞的测量差异** | 核内未剪接RNA更显著、细胞质mRNA不足、跨方案marker不一致 | 明确内含子计数策略和表达口径；同一类型的匹配细胞/核比较。(Bakken et al., 2018, PLOS One) |
| **空液滴与环境RNA污染** | 空液滴被认成细胞，或一类细胞的RNA在其他细胞中产生假阳性 | 查看原始计数和背景谱，用适合数据的空液滴识别与污染校正做敏感性分析。(Lun et al., 2019, Genome Biol; Young & Behjati, 2020, GigaScience) |
| **双细胞/多细胞（doublets/multiplets）** | 混合表达被错误当成稀有过渡细胞或混合细胞类型 | 联合实验设计、样本混合信息及计算检测；同类型双细胞尤其难识别。(Wolock et al., 2019, Cell Syst; McGinnis et al., 2019, Cell Syst; Stoeckius et al., 2018, Genome Biol) |
| **低质量细胞与错误阈值** | RNA少、降解、线粒体RNA占比异常或基因数偏低；严苛过滤也会删掉真实细胞群 | 在样本、细胞类型和技术平台的背景下判定，不将某一个固定线粒体百分比/UMI阈值视为所有脑组织通用。(Luecken & Theis, 2019, Mol Syst Biol; Heumos et al., 2023, Nat Rev Genet) |
| **测序稀疏、技术零值与真实零值混淆** | 低表达基因未被检出；过度插补可制造并不存在的共表达模式 | 报告检测深度、特征覆盖与过滤口径，慎用补值，不把所有零计数统一解释为生物学缺失。(Islam et al., 2014, Nat Methods; Heumos et al., 2023, Nat Rev Genet) |
| **批次效应与过度整合** | 供体/平台分组形成伪聚类；过强校正又可能抹去真实病理或年龄差异 | 检查批次与生物条件是否混杂；同时评估混合度和生物信号保留；差异表达优先回到可解释的原始计数层面。(Stuart et al., 2019, Cell; Luecken et al., 2022, Nat Methods) |
| **过度聚类、循环验证（double dipping）** | 同一数据既用来定义簇又据此宣称其marker“显著”，夸大细胞类型数目 | 多分辨率稳健性检查、外部数据或跨模态验证、独立样本检查。(DenAdel et al., 2025, Am J Hum Genet; Gouwens et al., 2020, Cell) |
| **伪重复与差异表达假阳性** | 把同一供体采到的许多细胞当成互相独立的实验个体，P值虚小 | 按供体/动物汇总同类细胞的pseudobulk，或采用能处理层级结构的统计模型；报告生物学重复。(Crowell et al., 2020, Nat Commun; Zimmerman et al., 2021, Nat Commun; Squair et al., 2021, Nat Commun) |
| **细胞组成与细胞状态混淆** | 细胞类型占比变化被误写为某细胞类型内部的表达变化，或反之 | 对composition和within-cell-type表达分别建模、明确统计分母与供体层级。(Crowell et al., 2020, Nat Commun; Heumos et al., 2023, Nat Rev Genet) |

### 2. 标准化、整合与细胞注释不是一个步骤

- **标准化**主要处理测序深度和RNA捕获差异等问题。对UMI计数，可以使用合适的计数模型和方差稳定策略；不同算法的统计假设不同，不存在对所有方案和目标都必胜的单一方法。(Hafemeister & Satija, 2019, Genome Biol; Heumos et al., 2023, Nat Rev Genet)
- **数据整合/批次校正**意在兼容不同样本或平台的技术变化；**整合结果适合某些可视化/注释任务，不意味着可不加验证地用于组间表达检验**。特别在“疾病组=某一批次”时，算法不能从根本上修复设计混杂。(Stuart et al., 2019, Cell; Luecken et al., 2022, Nat Methods)
- **细胞注释**应结合marker组合、参考图谱、脑区与实验类型；关键稀有亚型须检查重复样本和空间/形态证据，避免用单一基因、二维UMAP孤立小岛或算法自动标签确立新细胞类型。(Tasic et al., 2018, Nature; DenAdel et al., 2025, Am J Hum Genet; Thompson et al., 2025, Nat Neurosci)

### 3. 健全的差异表达和可重复性报告

研究中一个供体/一只动物可提供大量细胞，但来自同一个体的细胞通常不独立，因此**生物学重复数通常由独立供体/动物及实际随机化设计决定，不由细胞总数直接决定**。在跨供体比较时，按供体×细胞类型汇总计数（pseudobulk）是重要且常被推荐的分析路线之一；不同设计也可选择合适的混合效应模型，并检查重复数和模型适配。(Crowell et al., 2020, Nat Commun; Zimmerman et al., 2021, Nat Commun; Squair et al., 2021, Nat Commun)

为避免伪重复，应分别报告**样本/供体数、每个样本的细胞数、组织区域、组别/批次分配、校正项、原始及过滤后细胞数量、统计模型和多重检验方案**；并在跨平台整合后复查细胞标签是否仍保持合理的生物信号。(Luecken & Theis, 2019, Mol Syst Biol; Heumos et al., 2023, Nat Rev Genet)

### 4. 最低限度的节点和论文审核清单

- [ ] 能追溯供体/动物和原始数据（取样、脑区、年龄、样本状态、批次、是否冻存）。
- [ ] 区分scRNA-seq、snRNA-seq、3′/5′标签与全长方案；记录参考版本及内含子计数口径。
- [ ] 提供每个样本的质量控制结果，而不只给合并后一个数值。
- [ ] 检查环境RNA、空液滴和doublets，说明任何校正操作的依据。
- [ ] 聚类、批次校正、细胞命名结果经过敏感性分析；不要用UMAP视觉外观作为主要统计证据。
- [ ] 差异表达以适当的生物学重复和显著性控制为基础。
- [ ] 对“新细胞类型”“疾病机制”“轨迹方向”“细胞通讯”等更强推断标注验证状态。
- [ ] 原始数据、代码/软件版本、细胞注释词表及排除规则可回溯。

## 代表性实验或应用

| 研究方向 | 有代表性的研究与贡献 | 不能越过的边界 |
| --- | --- | --- |
| **技术起点：单个细胞的整体转录组** | 单细胞mRNA测序的早期实现；之后出现线性扩增、全长策略及UMI定量思想。(Tang et al., 2009, Nat Methods; Hashimshony et al., 2012, Cell Rep; Picelli et al., 2013, Nat Methods; Islam et al., 2014, Nat Methods) | 单细胞测序≠捕获细胞的每一条RNA。 |
| **高通量细胞普查** | Drop-seq、inDrops及条码液滴技术推动大规模细胞类型调查。(Macosko et al., 2015, Cell; Klein et al., 2015, Cell; Zheng et al., 2017, Nat Commun) | 细胞数量增加不自动提高每细胞覆盖与供体代表性。 |
| **小鼠皮层/海马分类** | 在多脑区建立细胞转录组分类，鉴别主要神经元/非神经元亚群及区域差异。(Zeisel et al., 2015, Science; Tasic et al., 2016, Nat Neurosci; Tasic et al., 2018, Nature) | 分类依赖取样脑区、测序深度和聚类标准，不能单凭簇数作跨论文比较。 |
| **人脑与小鼠跨物种对应** | 人脑单核测序及跨物种皮层比较显示保守与分歧同时存在。(Lake et al., 2016, Science; Hodge et al., 2019, Nature) | 同源候选不自动意味着相同的突触生理或行为角色。 |
| **大型脑图谱** | 小鼠全脑转录组+空间图谱、人类全脑细胞多样性调查、跨多研究整合脑细胞图谱。(Siletti et al., 2023, Science; Yao et al., 2023, Nature; Chen et al., 2024, Nat Med) | 跨平台整合是建模；跨研究可比性与参考标签不确定性仍需检查。 |
| **疾病相关细胞状态** | 阿尔茨海默病人脑单核数据揭示多种细胞群的疾病相关表达信号。(Mathys et al., 2019, Nature) | 供体层面相关性和病理共变不能直接证明某基因导致疾病。 |
| **分子-空间联合解析** | 下丘脑视前区的分子、空间、功能信息整合；人类海马单核与空间RNA图谱的联合分析。(Moffitt et al., 2018, Science; Thompson et al., 2025, Nat Neurosci) | 空间定位和标签转移存在分辨率、分割和模型假设，不能自动推导神经突触边。 |
| **分子-电生理-形态对应** | Patch-seq把单细胞表达与电生理/形态联系起来，后续大规模多模态工作建立更稳健的皮层抑制性细胞分类。(Cadwell et al., 2016, Nat Biotechnol; Gouwens et al., 2020, Cell) | 分子群体与生理类型不总是一一对应，应保留连续谱和异质性。 |
| **成年至衰老的细胞状态** | 2026年人类前额叶全生命周期snRNA-seq图谱联合空间与统计模型讨论年龄相关的细胞状态变化。(Yang et al., 2026, Nature) | 各年龄供体的横断面差异不等于同一细胞被长期追踪；群体年龄和细胞命运不可混为一谈。 |
| **分析陷阱的方法学复核** | 通过跨平台基准、伪重复检验、过度聚类评估及神经组织前分析偏差研究改善证据质量。(Ding et al., 2020, Nat Biotechnol; Squair et al., 2021, Nat Commun; DenAdel et al., 2025, Am J Hum Genet; Ning et al., 2026, BMC Neurosci) | 基准对比通常仅涵盖测试平台和样本条件，不能移植成通用阈值。 |

**对重复性最重要的判断：** 细胞大类与部分转录组特征通过多个脑区、技术与团队获得相互支持，足以说明方法能稳定发现重要的细胞分子差异；但是**某个聚类的精确数量、命名、细胞比例、疾病相关基因名单**仍强烈依赖取样、平台、统计设计与注释决策，并非单凭已有大型图谱就可认为无争议。(Zeisel et al., 2015, Science; Tasic et al., 2018, Nature; Siletti et al., 2023, Science; Luecken et al., 2022, Nat Methods)

## 与其他方法的关系

| 方法 | 如何互补 | 不可互相代替之处 |
| --- | --- | --- |
| **bulk RNA-seq** | 以组织整体/群体平均表达为参照，便于较深的组间对比 | bulk混合了细胞组成与状态；scRNA-seq则往往有较稀疏的单细胞读数。 |
| **snRNA-seq** | 脑组织、冻存或难解离样本中提供核内表达谱，补足可获得细胞类型 | 核内RNA与完整细胞RNA不能直接当作同一测量。(Bakken et al., 2018, PLOS One; Ding et al., 2020, Nat Biotechnol) |
| **空间转录组 / MERFISH / Slide-seq** | 把分子类型投回组织位置、层次与邻域，并用于验证细胞表达位置 | 具体技术在基因覆盖、空间分辨率、敏感性上各有权衡；相邻不等于突触连接。(Chen et al., 2015, Science; Rodriques et al., 2019, Science; Thompson et al., 2025, Nat Neurosci) |
| **CITE-seq / 单细胞蛋白检测** | 在可支持的体系中并行取得部分表面蛋白/表位与RNA信息 | 有限抗体面板和测量特性不能代表全蛋白质组。(Stoeckius et al., 2017, Nat Methods) |
| **Patch-seq / 电生理 / 形态学** | 将转录组类型与放电性质、内在生理和形态结合 | 电生理和形态测量有取样偏向，也不能自动证明细胞间突触连接。(Cadwell et al., 2016, Nat Biotechnol; Gouwens et al., 2020, Cell) |
| **AAV病毒载体示踪 / 单突触狂犬病毒示踪** | 在分子定义的细胞类型基础上研究轴突投射或候选直接突触前输入 | RNA标记无法替代结构连接图谱；示踪结果也不直接等于基因表达或因果功能。 |
| **谱系追踪、时间分辨采样、扰动实验** | 对命运与因果假说施加独立约束，验证伪时间或候选调控因子 | 伪时间/velocity主要是从横截面数据作模型推断；扰动才能检验特定机制。(Trapnell et al., 2014, Nat Biotechnol; La Manno et al., 2018, Nature) |

**建议的证据组合：** 探索性scRNA/snRNA-seq → 明确表达类型和候选状态 → 使用空间RNA/原位蛋白校验位置 → 对关键细胞群结合Patch-seq、解剖示踪或扰动研究。这个顺序是可选的研究策略，不是每个问题必做的固定流水线。(Moffitt et al., 2018, Science; Gouwens et al., 2020, Cell; Thompson et al., 2025, Nat Neurosci)

## 相关节点

- **同分类可考虑联动：** AAV病毒载体示踪；单突触狂犬病毒示踪（分子细胞分类 vs. 区域投射/候选突触前输入）。
- **上位与紧邻方法候选：** 单核RNA测序（snRNA-seq）、空间转录组、单细胞多组学、CITE-seq、Patch-seq、原位杂交、RNA velocity、伪时间分析、单细胞数据整合、转录组细胞类型注释。
- **证据与推理候选：** 细胞类型与细胞状态、批次效应、独立生物学重复、伪重复、差异表达分析、可重复性、技术偏差、结构连接与功能连接、因果推断。

## 参考资料

文献表采用正文作者—年份—期刊简称标识，并提供文章题名、期刊卷期、DOI、证据类型与**该论文在本节点所能支持的结论及边界**。期刊年份以正式卷期年份为准；不同研究不因样本大或发表较新就自动具有更高因果证据等级。2026年10月刚在线发表的Ning等研究属于已同行评审的早期在线版本，后续最终版的卷页和编辑修改仍待确认。

| 正文引用 | 作者、年份与论文题名 | 期刊卷页／文章号 | DOI／永久链接 | 资料性质 | 主要支持与限制 |
| --- | --- | --- | --- | --- | --- |
| (Tang et al., 2009, Nat Methods) | Tang F et al. (2009). _mRNA-Seq whole-transcriptome analysis of a single cell._ | Nat Methods 6:377–382 | [DOI](https://doi.org/10.1038/nmeth.1315) | 单细胞测序奠基原始研究 | 单个细胞RNA测序可行；不能代表当前高通量单细胞平台性能。 |
| (Hashimshony et al., 2012, Cell Rep) | Hashimshony T et al. (2012). _CEL-Seq: single-cell RNA-Seq by multiplexed linear amplification._ | Cell Rep 2:666–673 | [DOI](https://doi.org/10.1016/j.celrep.2012.08.003) | 方法原始研究 | 较早的分子条码与线性扩增框架；不同于现代高通量液滴体系。 |
| (Picelli et al., 2013, Nat Methods) | Picelli S et al. (2013). _Smart-seq2 for sensitive full-length transcriptome profiling in single cells._ | Nat Methods 10:1096–1098 | [DOI](https://doi.org/10.1038/nmeth.2639) | 方法原始研究 | 高覆盖/全长策略；与3′/5′ UMI捕获路线存在用途和吞吐权衡。 |
| (Islam et al., 2014, Nat Methods) | Islam S et al. (2014). _Quantitative single-cell RNA-seq with unique molecular identifiers._ | Nat Methods 11:163–166 | [DOI](https://doi.org/10.1038/nmeth.2772) | 定量方法原始研究 | UMI帮助控制扩增误差；不能修复RNA捕获前的丢失。 |
| (Trapnell et al., 2014, Nat Biotechnol) | Trapnell C et al. (2014). _The dynamics and regulators of cell fate decisions are revealed by pseudotemporal ordering of single cells._ | Nat Biotechnol 32:381–386 | [DOI](https://doi.org/10.1038/nbt.2859) | 推断方法与功能验证原始研究 | Monocle伪时间排序可产生转变假说；伪时间本身非真实时间或已证因果。 |
| (Zeisel et al., 2015, Science) | Zeisel A et al. (2015). _Cell types in the mouse cortex and hippocampus revealed by single-cell RNA-seq._ | Science 347:1138–1142 | [DOI](https://doi.org/10.1126/science.aaa1934) | 脑细胞图谱原始研究 | 小鼠皮层与海马细胞多样性；类别依赖地区/样本与分析方法。 |
| (Macosko et al., 2015, Cell) | Macosko EZ et al. (2015). _Highly parallel genome-wide expression profiling of individual cells using nanoliter droplets._ | Cell 161:1202–1214 | [DOI](https://doi.org/10.1016/j.cell.2015.05.002) | 高通量方法/视网膜图谱 | Drop-seq高通量表达分类；检出细胞数并不等于独立供体数。 |
| (Klein et al., 2015, Cell) | Klein AM et al. (2015). _Droplet barcoding for single-cell transcriptomics applied to embryonic stem cells._ | Cell 161:1187–1201 | [DOI](https://doi.org/10.1016/j.cell.2015.04.044) | 液滴方法原始研究 | inDrops方法与细胞状态分析；最初适用实验体系不同于成人脑。 |
| (Chen et al., 2015, Science) | Chen KH et al. (2015). _Spatially resolved, highly multiplexed RNA profiling in single cells._ | Science 348:aaa6090 | [DOI](https://doi.org/10.1126/science.aaa6090) | 原位成像方法原始研究 | MERFISH在原位测量RNA及位置；不等于所有RNA或直接突触测量。 |
| (Tasic et al., 2016, Nat Neurosci) | Tasic B et al. (2016). _Adult mouse cortical cell taxonomy revealed by single cell transcriptomics._ | Nat Neurosci 19:335–346 | [DOI](https://doi.org/10.1038/nn.4216) | 脑细胞类型学原始研究 | 小鼠视觉皮层细胞转录分类并验证部分生理特征；分类对数据深度敏感。 |
| (Lake et al., 2016, Science) | Lake BB et al. (2016). _Neuronal subtypes and diversity revealed by single-nucleus RNA sequencing of the human brain._ | Science 352:1586–1590 | [DOI](https://doi.org/10.1126/science.aaf1204) | 人脑单核图谱原始研究 | snRNA-seq应用于人脑细胞分类；核内表达并非完整细胞表达。 |
| (Cadwell et al., 2016, Nat Biotechnol) | Cadwell CR et al. (2016). _Electrophysiological, transcriptomic and morphologic profiling of single neurons using Patch-seq._ | Nat Biotechnol 34:199–203 | [DOI](https://doi.org/10.1038/nbt.3445) | 多模态方法原始研究 | 联结单神经元RNA、电生理及形态；样本规模和选择偏差需考虑。 |
| (Zheng et al., 2017, Nat Commun) | Zheng GXY et al. (2017). _Massively parallel digital transcriptional profiling of single cells._ | Nat Commun 8:14049 | [DOI](https://doi.org/10.1038/ncomms14049) | 高通量条码方法原始研究 | 可并行测量大量细胞表达；其3′计数策略与全长测序不等价。 |
| (Habib et al., 2017, Nat Methods) | Habib N et al. (2017). _Massively parallel single-nucleus RNA-seq with DroNc-seq._ | Nat Methods 14:955–958 | [DOI](https://doi.org/10.1038/nmeth.4407) | 脑单核高通量方法研究 | 证明高通量核测序适用于部分冻存脑组织；需检查核RNA与脑区取样偏倚。 |
| (van den Brink et al., 2017, Nat Methods) | van den Brink SC et al. (2017). _Single-cell sequencing reveals dissociation-induced gene expression in tissue subpopulations._ | Nat Methods 14:935–936 | [DOI](https://doi.org/10.1038/nmeth.4437) | 前分析伪迹原始研究 | 组织解离可诱导应激表达；具体伪迹依赖组织/处理条件。 |
| (Stoeckius et al., 2017, Nat Methods) | Stoeckius M et al. (2017). _Simultaneous epitope and transcriptome measurement in single cells._ | Nat Methods 14:865–868 | [DOI](https://doi.org/10.1038/nmeth.4380) | 多模态方法原始研究 | CITE-seq将部分蛋白表位与转录组联合测量；有限抗体集合不等于蛋白全谱。 |
| (Bakken et al., 2018, PLOS One) | Bakken TE et al. (2018). _Single-nucleus and single-cell transcriptomes compared in matched cortical cell types._ | PLOS One 13:e0209648 | [DOI](https://doi.org/10.1371/journal.pone.0209648) | 细胞/细胞核直接比较原始研究 | 证实细胞与核测量存在差异；内含子计数影响snRNA可辨类型。 |
| (Tasic et al., 2018, Nature) | Tasic B et al. (2018). _Shared and distinct transcriptomic cell types across neocortical areas._ | Nature 563:72–78 | [DOI](https://doi.org/10.1038/s41586-018-0654-5) | 跨脑区脑细胞图谱原始研究 | 皮层不同区域类型既共享又有差异；不能用单一区域定义全脑。 |
| (Moffitt et al., 2018, Science) | Moffitt JR et al. (2018). _Molecular, spatial, and functional single-cell profiling of the hypothalamic preoptic region._ | Science 362:eaau5324 | [DOI](https://doi.org/10.1126/science.aau5324) | 多模态脑区图谱原始研究 | 联合空间与分子标记验证脑区细胞异质性；行为相关≠单细胞功能因果。 |
| (La Manno et al., 2018, Nature) | La Manno G et al. (2018). _RNA velocity of single cells._ | Nature 560:494–498 | [DOI](https://doi.org/10.1038/s41586-018-0414-6) | 推断模型与方法原始研究 | 用未剪接/已剪接RNA提出状态变化方向；结果依赖动力学假设。 |
| (Stoeckius et al., 2018, Genome Biol) | Stoeckius M et al. (2018). _Cell Hashing with barcoded antibodies enables multiplexing and doublet detection for single cell genomics._ | Genome Biol 19:224 | [DOI](https://doi.org/10.1186/s13059-018-1603-1) | 多样本混合/质控原始研究 | 抗体条码辅助样本归属及部分多细胞识别；不能检出全部同来源双细胞。 |
| (Luecken & Theis, 2019, Mol Syst Biol) | Luecken MD & Theis FJ (2019). _Current best practices in single-cell RNA-seq analysis: a tutorial._ | Mol Syst Biol 15:e8746 | [DOI](https://doi.org/10.15252/msb.20188746) | 方法学综述与教程 | 整理质控、归一化、可视化与整合注意事项；非统一强制阈值或独立实验证明。 |
| (Lun et al., 2019, Genome Biol) | Lun ATL et al. (2019). _EmptyDrops: distinguishing cells from empty droplets in droplet-based single-cell RNA sequencing data._ | Genome Biol 20:63 | [DOI](https://doi.org/10.1186/s13059-019-1662-y) | 计算质控原始研究 | 区分含细胞液滴与环境RNA背景；识别依赖背景估计和数据特性。 |
| (Wolock et al., 2019, Cell Syst) | Wolock SL et al. (2019). _Scrublet: Computational Identification of Cell Doublets in Single-Cell Transcriptomic Data._ | Cell Syst 8:281–291.e9 | [DOI](https://doi.org/10.1016/j.cels.2018.11.005) | 双细胞检测方法研究 | 计算识别部分异常混合表达，尤其对异质双细胞有效；同质双细胞可漏检。 |
| (McGinnis et al., 2019, Cell Syst) | McGinnis CS et al. (2019). _DoubletFinder: Doublet Detection in Single-Cell RNA Sequencing Data Using Artificial Nearest Neighbors._ | Cell Syst 8:329–337.e4 | [DOI](https://doi.org/10.1016/j.cels.2019.03.003) | 双细胞检测方法研究 | 人工最近邻框架识别doublets；依赖数据结构，非完美分类器。 |
| (Stuart et al., 2019, Cell) | Stuart T et al. (2019). _Comprehensive Integration of Single-Cell Data._ | Cell 177:1888–1902.e21 | [DOI](https://doi.org/10.1016/j.cell.2019.05.031) | 数据整合方法原始研究 | 帮助跨数据集映射/整合；校正过度可删除真实生物差异。 |
| (Hafemeister & Satija, 2019, Genome Biol) | Hafemeister C & Satija R (2019). _Normalization and variance stabilization of single-cell RNA-seq data using regularized negative binomial regression._ | Genome Biol 20:296 | [DOI](https://doi.org/10.1186/s13059-019-1874-1) | 归一化方法原始研究 | UMI计数的正则化负二项模型；特定统计假设不普适所有数据。 |
| (Hodge et al., 2019, Nature) | Hodge RD et al. (2019). _Conserved cell types with divergent features in human versus mouse cortex._ | Nature 573:61–68 | [DOI](https://doi.org/10.1038/s41586-019-1506-7) | 跨物种脑细胞图谱原始研究 | 人鼠保守分子类型与表达/形态分歧并存；同源不等于完全同功能。 |
| (Mathys et al., 2019, Nature) | Mathys H et al. (2019). _Single-cell transcriptomic analysis of Alzheimer’s disease._ | Nature 570:332–337 | [DOI](https://doi.org/10.1038/s41586-019-1195-2) | 疾病相关单核研究 | 支持病理状态相关分子变化；不能单凭相关性证明疾病因果。 |
| (Rodriques et al., 2019, Science) | Rodriques SG et al. (2019). _Slide-seq: A scalable technology for measuring genome-wide expression at high spatial resolution._ | Science 363:1463–1467 | [DOI](https://doi.org/10.1126/science.aaw1219) | 空间RNA方法原始研究 | 提供组织空间维度并映射分子类型；空间分辨率与转录敏感性权衡。 |
| (Ding et al., 2020, Nat Biotechnol) | Ding J et al. (2020). _Systematic comparison of single-cell and single-nucleus RNA-sequencing methods._ | Nat Biotechnol 38:737–746 | [DOI](https://doi.org/10.1038/s41587-020-0465-8) | 跨平台基准比较 | 在多个类型样本中比较技术性能；非所有平台/组织的普适排名。 |
| (Young & Behjati, 2020, GigaScience) | Young MD & Behjati S (2020). _SoupX removes ambient RNA contamination from droplet-based single-cell RNA sequencing data._ | GigaScience 9:giaa151 | [DOI](https://doi.org/10.1093/gigascience/giaa151) | 环境RNA偏差分析与校正 | 背景RNA可造成错误的低量表达；估计修正本身有模型假设。 |
| (Crowell et al., 2020, Nat Commun) | Crowell HL et al. (2020). _muscat detects subpopulation-specific state transitions from multi-sample multi-condition single-cell transcriptomics data._ | Nat Commun 11:6077 | [DOI](https://doi.org/10.1038/s41467-020-19894-4) | 多样本统计方法原始研究 | 区分细胞亚群内状态变化与样本间变异；须符合设计与模型要求。 |
| (Gouwens et al., 2020, Cell) | Gouwens NW et al. (2020). _Integrated Morphoelectric and Transcriptomic Classification of Cortical GABAergic Cells._ | Cell 183:935–953.e19 | [DOI](https://doi.org/10.1016/j.cell.2020.09.057) | 多模态脑细胞类型学原始研究 | 转录组-电生理-形态联合分类更可靠，亦存在离散和连续性。 |
| (Zimmerman et al., 2021, Nat Commun) | Zimmerman KD, Espeland MA & Langefeld CD (2021). _A practical solution to pseudoreplication bias in single-cell studies._ | Nat Commun 12:738 | [DOI](https://doi.org/10.1038/s41467-021-21038-1) | 统计层级偏差方法研究 | 同一供体细胞并非独立重复；必须处理组内相关性。 |
| (Squair et al., 2021, Nat Commun) | Squair JW et al. (2021). _Confronting false discoveries in single-cell differential expression._ | Nat Commun 12:5692 | [DOI](https://doi.org/10.1038/s41467-021-25960-2) | 差异表达方法比较/基准 | 无视生物重复变异可严重夸大差异基因；方法性能随设计而变。 |
| (Luecken et al., 2022, Nat Methods) | Luecken MD et al. (2022). _Benchmarking atlas-level data integration in single-cell genomics._ | Nat Methods 19:41–50 | [DOI](https://doi.org/10.1038/s41592-021-01336-8) | 大规模方法比较 | 需要在消除批次与保留生物差异之间权衡；性能依赖基准任务。 |
| (Heumos et al., 2023, Nat Rev Genet) | Heumos L et al. (2023). _Best practices for single-cell analysis across modalities._ | Nat Rev Genet 24:550–572 | [DOI](https://doi.org/10.1038/s41576-023-00586-w) | 跨模态最佳实践综述 | 总结方法选择、质量控制、整合与差异表达；为规范建议非新实验共识。 |
| (Yao et al., 2023, Nature) | Yao Z et al. (2023). _A high-resolution transcriptomic and spatial atlas of cell types in the whole mouse brain._ | Nature 624:317–332 | [DOI](https://doi.org/10.1038/s41586-023-06812-z) | 小鼠全脑多模态图谱 | 转录组与空间定位联合刻画脑细胞类型；具体标签仍依赖计算分类和分辨率。 |
| (Siletti et al., 2023, Science) | Siletti K et al. (2023). _Transcriptomic diversity of cell types across the adult human brain._ | Science 382:eadd7046 | [DOI](https://doi.org/10.1126/science.add7046) | 人脑大规模单核图谱 | 广覆盖成人脑分子多样性；取样供体与区域代表性影响外推。 |
| (Chen et al., 2024, Nat Med) | Chen X et al. (2024). _A brain cell atlas integrating single-cell transcriptomes across human brain regions._ | Nat Med 30:2679–2691 | [DOI](https://doi.org/10.1038/s41591-024-03150-z) | 跨研究整合图谱/数据资源 | 联合多脑区多数据集；参考标签与跨平台混杂不等于独立实验证实每个细胞亚型。 |
| (Thompson et al., 2025, Nat Neurosci) | Thompson JR et al. (2025). _An integrated single-nucleus and spatial transcriptomics atlas reveals the molecular landscape of the human hippocampus._ | Nat Neurosci 28:1990–2004 | [DOI](https://doi.org/10.1038/s41593-025-02022-0) | 人脑海马核+空间联合图谱 | 联合组织定位和细胞分子类型；空间解卷积与标签转移具模型不确定性。 |
| (DenAdel et al., 2025, Am J Hum Genet) | DenAdel A et al. (2025). _Artificial variables help to avoid over-clustering in single-cell RNA sequencing._ | Am J Hum Genet 112:940–951 | [DOI](https://doi.org/10.1016/j.ajhg.2025.02.014) | 过度聚类/循环推断方法研究 | 同一数据聚类后再作标记检验可能双重利用证据；方法缓解不保证无分类误差。 |
| (Yang et al., 2026, Nature) | Yang H et al. (2026). _Lifespan single-cell transcriptomic atlas of the human prefrontal cortex._ | Nature 657:1003–1015 | [DOI](https://doi.org/10.1038/s41586-026-10271-7) | 最新人脑全生命周期单核图谱 | 前额叶跨年龄供体的分子变化；横断面群体数据不是单细胞时间追踪。 |
| (Ning et al., 2026, BMC Neurosci) | Ning J et al. (2026). _A systematic multi-factorial benchmarking reveals critical technical biases in single-nucleus RNA sequencing of the brain._ | BMC Neurosci (2026，早期在线，待最终卷页) | [DOI](https://doi.org/10.1186/s12868-026-01058-7) | 最新小鼠脑单核技术偏差基准 | 不同取材/固定/平台影响所测细胞群；新发早期版本及特定条件，不能泛化。 |

- **较稳定：** 单细胞/单核RNA测序可系统观察细胞RNA表达异质性，适用于构建细胞分子图谱；技术与跨模态研究表明，脑细胞大类中的许多转录组特征具有可复核性。(Zeisel et al., 2015, Science; Tasic et al., 2018, Nature; Siletti et al., 2023, Science)
- **明确方法依赖：** 解离、核/细胞差异、环境RNA、双细胞、批次校正、聚类及独立生物学重复可显著改变测量与统计解释；QC阈值须按数据类型确认，不能机械套用。(Bakken et al., 2018, PLOS One; Young & Behjati, 2020, GigaScience; Squair et al., 2021, Nat Commun; Ning et al., 2026, BMC Neurosci)
- **争议或推断：** “一个聚类是否是一种独立生物学类型”、不同细胞型的连续/离散边界、伪时间方向、转录本-蛋白对应和细胞通讯候选均需上下文与独立证据。(La Manno et al., 2018, Nature; Gouwens et al., 2020, Cell; DenAdel et al., 2025, Am J Hum Genet)
- **不能单凭本法得出：** 特定细胞与哪个神经元形成突触、某个蛋白必然活跃、某条通路对行为具有因果必要性。对应结论需要形态、蛋白、电生理、结构连接与适当扰动研究。(Cadwell et al., 2016, Nat Biotechnol; Moffitt et al., 2018, Science)
