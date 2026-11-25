---
publish: true
aliases:
  - Neuropixels
  - Neuropixels probe
  - Neuropixels探针
  - 神经像素电极
title: Neuropixels电极
description: Neuropixels是一类集成式高密度硅基细胞外电极探针，可沿针柄同时采集多位置神经电位，用于推断单元放电、局部场电位和跨脑区群体活动，但结果受采样选择、漂移和脉冲分类质量限制。
created: 2026-10-17T10:31:36.894+08:00
modified: 2026-11-14T12:41:03.326+08:00
tags:
  - 类型/方法
  - 层/观测
---

# Neuropixels电极

> **一句话介绍：** Neuropixels 电极是一类具有密集记录位点、片上信号处理与多通道读出的侵入式硅基细胞外电极，能同时采集相邻或跨脑区的毫秒级电位变化，并通过脉冲分类（spike sorting）推断神经元放电及群体活动；它并不直接测量细胞内膜电位、突触连接或细胞的分子身份。(Jun et al., 2017, Nature; Steinmetz et al., 2021, Science; Siegle & Steinmetz, 2026, Nat Rev Neurosci)

## 快速理解

可以把 Neuropixels 想成一支布满微型“听筒”的细长探针：插入脑组织后，多个位点同时记录附近细胞产生的微弱**细胞外电位**。同一个神经元的动作电位可能出现在多个相邻位点上，形成独特但会随距离、方向、组织状态而改变的时空波形。分析软件将大量电压波形分组成**推定单元（putative unit）**，再生成放电时间点序列（spike trains）。这为研究神经群体如何随感觉、动作、学习和睡眠等状态共同变化提供了高时间精度数据。(Gold et al., 2006, J Neurophysiol; Rossant et al., 2016, Nat Neurosci; Jun et al., 2017, Nature)

**它回答的是“在什么时间、什么位置附近，哪些可分离的胞外电活动模式出现”，不是把神经元一个一个自动贴上真实身份标签。**

三个必须区分的计数单位：

1. **记录位点（site）**：针柄上实际存在的电极接触点。
2. **同时读出通道（channel）**：芯片与采集设备在某一时刻可以同时读取的独立电信号路径。
3. **神经元单元（unit）**：根据波形和放电序列，经排序与质量控制后推定的放电来源。

\*\*位点数量不等于通道数量，通道数量也不等于最终通过质量控制的单元数。\*\*经典 NP 1.0 拥有 960 个可选择位点和 384 个同步通道；NP 2.0 四针柄版本含 5,120 个位点，但同一支探针也只有 384 个并行读出通道。软件切换位点的先后采集，不等于所有位点同时记录。(Jun et al., 2017, Nature; Steinmetz et al., 2021, Science)

与 fMRI 的血流动力学代理信号不同，Neuropixels 测量的是脑组织内的电位，因此更适合研究放电时序、试次间神经动态及近邻或跨脑区单元之间的统计耦合；不过**胞外电位仍须通过算法推断为某一细胞的发放**，并非未经处理的“神经元身份真值”。(Buzsáki et al., 2012, Nat Rev Neurosci; Harris et al., 2016, Nat Neurosci)

## 原理与操作流程

### 1. 信号从哪里来：AP 与 LFP 不是同一个读数

神经元跨膜电流在导电组织中形成胞外电场，电极记录多个电流源与汇叠加后的电位。快速动作电位往往呈现局部化的高频胞外波形；局部场电位（local field potential，LFP）则包含较慢的群体电流变化，其来源受突触活动、细胞几何构型、共同输入及体积传导影响。**LFP 不是许多动作电位的简单加总，也不能凭一个频段唯一确定神经机制。**(Gold et al., 2006, J Neurophysiol; Buzsáki et al., 2012, Nat Rev Neurosci; Einevoll et al., 2013, Nat Rev Neurosci)

芯片可对原始电压进行放大、滤波、多路复用和数字化。经典 NP 1.0 的 AP 和 LFP 读出采用不同带宽配置；NP 2.0 与其他衍生型号的具体读出结构并不都相同，不能给所有 Neuropixels 一概套用 NP 1.0 的频带与采样规格。(Jun et al., 2017, Nature; Steinmetz et al., 2021, Science)

**胞外尖峰的形状为何不能等于细胞类型？** 波形受细胞形态、轴突／胞体电流、组织电导率、电极距离与相对位置共同影响。同一细胞轻微位移可改变各通道幅度；不同类别神经元也可能呈现相似波形。2025 年 NP Ultra 研究甚至更清楚地揭示可记录到来自轴突等亚细胞区室的小空间足迹信号，因此“每个 unit 都来自邻近胞体”并不可靠。(Gold et al., 2006, J Neurophysiol; Ye et al., 2025, Neuron)

### 2. 不同型号：版本规格不可混用

| 型号及文献 | 结构与特点 | 重要边界 |
| --- | --- | --- |
| **Neuropixels 1.0** | 经典单针柄 10 mm；960 个可选择电极位点、384 个同步读出通道，支持大规模跨深度记录。(Jun et al., 2017, Nature) | 仅被选中的位点可同时读出；神经元数不等于通道数。 |
| **Neuropixels 2.0** | 小型化、提高纵向位点密度；存在单针柄与四针柄版本。四针柄共 5,120 位点，每支探针 384 个同步通道；与漂移校正相结合支持长期记录。(Steinmetz et al., 2021, Science) | 四针柄总位点数不能误写为单针柄规格；跨天同一神经元需算法和证据验证。 |
| **Neuropixels Ultra** | 高局部采样密度，论文报告位点间距约 6 μm，强化小尺度波形与部分细胞类型区分。(Ye et al., 2025, Neuron) | 局部精细采样有优势，但未必优于 NP 2.0 的长距离深度覆盖。 |
| **Neuropixels 1.0 NHP** | 面向非人灵长类的大脑体积，论文使用约 45 mm 针柄，4,416 个可选择位点、384 个同步通道。(Trautmann et al., 2025, Nat Neurosci) | 特殊针柄的尺寸和适用条件不能等同于标准啮齿动物 NP 1.0。 |
| **Neuropixels Opto 原型** | 在电学位点附近集成可寻址光输出，论文展示结合光遗传学的记录、操纵与 optotagging。(Lakunina et al., 2026, Nat Methods) | 属原型技术；光遗传响应的身份与直接效应仍需要控制。 |

**规格使用规则：** 研究和引用硬件数据时明确写出“具体型号／针柄数／电极位点数／并行读出通道数／采样方案／版本”，避免把不同代际的设计合并成一种通用“Neuropixels 规格”。

### 3. 典型实验工作流

1. **从可检验问题出发选择目标脑区及范围。** 明确需要高密度局部记录、多个深部结构、自由活动、长期纵向还是联合光遗传干预；再据此选择针柄几何、数量、实验设计及相关动物福利审查。(Buzsáki, 2004, Nat Neurosci; Siegle & Steinmetz, 2026, Nat Rev Neurosci)
2. **规划位置和位点布局。** 使用适当脑图谱确定进针目标和路径；记录探针型号、角度、深度、位点—通道映射及任何分时切换。术后脑组织学和图谱配准可为“记录来自哪个脑区”提供验证，但受切片变形及定位误差限制。(Jun et al., 2017, Nature; International Brain Laboratory et al., 2025, eLife)
3. **匹配可行的行为与记录方式。** 急性与慢性植入、头固定与自由活动对运动伪迹、稳定性、实验成本和风险有不同要求。对于人类术中记录，研究必须在独立的临床伦理及手术约束下开展，不能将动物实验流程照搬给临床患者。(Steinmetz et al., 2021, Science; Paulk et al., 2022, Nat Neurosci; Coughlin et al., 2023, Nat Protoc)
4. **同步采集电信号与实验事件。** 保存原始连续电压、采样率、通道映射、参考电极、行为事件、刺激时标以及同步信号。同步错误可能把刺激相关延迟误判为神经生理延迟；开放式采集软件和时间同步机制有助于保存完整流程。(Siegle et al., 2017, J Neural Eng; Teeters et al., 2015, Neuron)
5. **信号预处理。** 按采集类型选择坏道检查、参考处理、频带处理、伪迹排除和漂移估计，保留原始数据以便重处理。参考方法、滤波和噪声消除可改变波形，不能将某一种默认管线当成所有脑区的真值。(Harris et al., 2016, Nat Neurosci; Pachitariu et al., 2024, Nat Methods)
6. **Spike sorting。** 在密集电极时空波形中进行尖峰检测、模板／特征提取、聚类及可能的重叠尖峰分离，随后根据运动漂移重新校准单元身份。可选方案包括不同的自动化排序器；SpikeInterface 可以用于统一接口与结果比较，SpikeForest 提供地面真值基准。(Rossant et al., 2016, Nat Neurosci; Chung et al., 2017, Neuron; Magland et al., 2020, eLife; Buccino et al., 2020, eLife)
7. **对每个单元做独立质量审查。** 查看波形一致性、空间分布、放电自相关、不应期违例、隔离度、振幅分布、漂移及会话稳定性。标明单单元（single unit）还是多单元活动（multi-unit activity），并保留不确定的排除理由。(Hill et al., 2011, J Neurosci; Pachitariu et al., 2024, Nat Methods)
8. **分析并复现神经—行为关系。** 使用事件对齐放电率、单试次人口动态、噪声相关、解码等模型，控制动作与唤醒等混杂；记录单位筛选规则、训练测试分割、跨会话细胞匹配和脑区定位置信度。(Steinmetz et al., 2019, Nature; International Brain Laboratory et al., 2025, Nature)
9. **保存可复核数据包。** 至少保存原始电压、通道及几何映射、时间同步、探针插入与组织学证据、排序结果、单元质控、软件版本、分析代码和剔除规则；必要时使用 Neurodata Without Borders（NWB）标准。(Teeters et al., 2015, Neuron; Rübel et al., 2022, eLife)

### 4. 因果解释中的四层对象

| 层次 | 常见输出 | 不可直接越过的边界 |
| --- | --- | --- |
| **电学观测** | 位点电压随时间变化，包括尖峰相关波形和 LFP | 并非细胞内电压；受邻近多个电流源影响。 |
| **算法推断** | 单元标签、spike times、波形模板与位置估计 | unit 是计算归类结果，不是经独立确认的一颗细胞。 |
| **功能关联** | 刺激响应、选择与运动相关性、群体解码、相关结构 | 编码／预测不证明这组细胞对行为必要。 |
| **细胞／回路因果** | 光遗传标记、干预效应、解剖对应、跨方法校验 | 需要额外控制，单凭探针记录不能完成。 |

这些层次的区分是解释高密度电极数据的核心前提。(Harris et al., 2016, Nat Neurosci; Lima et al., 2009, PLoS One; Lakunina et al., 2026, Nat Methods)

## 能回答什么，不能回答什么？

| 问题 | Neuropixels 能支持的证据 | 不能仅凭记录推出 |
| --- | --- | --- |
| **哪些单元在某事件附近放电？** | 用排序后 spike trains 估计事件对齐放电及试次变异。(Steinmetz et al., 2019, Nature) | 这些单元就是某确定分子类型细胞、且该活动使行为发生。 |
| **不同区域是否同时表达任务变量？** | 多个结构的放电率、群体活动和解码结果可同期比较。(International Brain Laboratory et al., 2025, Nature) | 同时相关说明信息从 A 单向传到 B，或证明各区之间的突触连接。 |
| **单元之间是否存在同步或统计耦合？** | 尖峰交叉相关、延迟相关和群体协变。 | 直接单突触连接，除非有更严格的模型、控制或独立验证。 |
| **能否记录长时间学习过程？** | 配合慢性植入、稳定记录和后验匹配，可探索跨天神经活动。(Dhawale et al., 2017, eLife; Steinmetz et al., 2021, Science) | 同一 ID 自动保证同一神经元跨天毫无歧义。 |
| **LFP 能反映什么？** | 探查局部／跨位点节律与电场时空变化。(Einevoll et al., 2013, Nat Rev Neurosci) | 某频率仅代表某个确定神经递质、脑区或细胞类别。 |
| **可否凭波形推断细胞类型？** | 在有标记真值和限定训练数据的条件下，部分细胞类型可概率区分。(Beau et al., 2025, Cell; Ye et al., 2025, Neuron) | 窄波形一概为抑制性中间神经元，或某模型对所有脑区跨物种通用。 |
| **Neuropixels 能“读取整个脑”吗？** | 多探针或多实验累积可形成广域跨脑区图谱。(International Brain Laboratory et al., 2025, Nature) | 一根针柄在单次实验中无遗漏地覆盖全脑所有神经元。 |
| **可用于人类吗？** | 有特定手术条件下的人类皮层研究和协议。(Paulk et al., 2022, Nat Neurosci; Coughlin et al., 2023, Nat Protoc) | 已普遍适用于常规临床检测、自由植入或诊断。 |

**容易混淆的三组推断：**

- **测到电压 ≠ 精确获知神经元完整膜电位。** 测得的是细胞外多个源叠加形成的场。(Buzsáki et al., 2012, Nat Rev Neurosci)
- **获得几百个 unit ≠ 无偏抽样了几百颗神经元。** 记录半径、胞体与轴突几何、活动水平、信噪比、检测阈值和筛选规则都影响哪些来源被采集及保留。(Harris et al., 2016, Nat Neurosci; Ye et al., 2025, Neuron)
- **神经活动解码成功 ≠ 大脑必然使用相同算法。** 解码性能依赖特征、训练方案、行为混杂及任务；若无干预证据，解释应停留在关联和预测层。(Steinmetz et al., 2019, Nature; International Brain Laboratory et al., 2025, Nature)

## 空间、时间尺度与适用对象

### 1. 时间与空间尺度

- **时间：** 探针记录细胞外电位，适合分析毫秒量级的放电时序；经典高频 AP 记录常以约 30 kHz 数字采样，但**采样间隔**、波形检出精度和 spike sorting 的真实时间误差不是同一个量，参数取决于具体硬件和处理流程。(Jun et al., 2017, Nature; Siegle & Steinmetz, 2026, Nat Rev Neurosci)
- **空间：** 位点通常沿细长针柄排列，使近邻电位和跨层／跨深度变化得以测量。电极位点间距是硬件几何参数，不等于细胞定位精度、脑区分区精度或探测到的单元范围。(Jun et al., 2017, Nature; Gold et al., 2006, J Neurophysiol)
- **覆盖：** 针柄可连续经过不同结构，多个探针能够扩大并行覆盖；但脑区位置归属还需插入路径、组织学重建和脑图谱配准，且对弯曲脑区与复杂边界存在误差。(Steinmetz et al., 2019, Nature; International Brain Laboratory et al., 2025, eLife)
- **长期性：** 慢性记录的时间跨度可从多次短会话延伸到周或月，但不同单元可追踪性的证据强度并不一致；稳定性受移动、组织反应、设备寿命与后验匹配标准影响。(Dhawale et al., 2017, eLife; Steinmetz et al., 2021, Science)

### 2. 实验体系

**啮齿动物：** 应用最充分，包括头固定、自由行为、一次性插入和长期慢性实验；多实验室数据支持某些标准化指标的跨实验室可重复性。(Jun et al., 2017, Nature; International Brain Laboratory et al., 2025, eLife)

**非人灵长类：** 需要适合更深靶区、更硬组织和更大脑体积的探针几何、机械适配及严格伦理设计。2025 年经过同行评审的 Neuropixels 1.0 NHP 研究提供技术可行性证据；另有并非 Neuropixels 品牌的高通道硅探针，不能将这些不同硬件归为同一型号。(Trautmann et al., 2025, Nat Neurosci; Liu et al., 2024, Nat Neurosci)

**人类：** 2022 年报道特定条件下的皮层记录，2023 年公开手术室操作协议；这类研究通常发生在严格受控的术中情境，并不能表明 Neuropixels 是常规无创临床检查。(Paulk et al., 2022, Nat Neurosci; Coughlin et al., 2023, Nat Protoc)

**适用优势：** 在较广覆盖下保留神经放电的高时间分辨率，便于同时研究多单元／多脑区神经动力学；开放分析工具和数据标准有利于多人复核。(Siegle et al., 2021, Nature; Buccino et al., 2020, eLife)

**关键局限：** 侵入性与组织损伤风险、探针机械漂移与脑组织相对运动、高维数据量和计算成本、未被采样神经元的选择偏差，以及胞外波形对细胞身份和连接方向的识别能力有限。(Harris et al., 2016, Nat Neurosci; Siegle & Steinmetz, 2026, Nat Rev Neurosci)

## 质量控制与典型伪迹

### 1. 典型质量问题

| 问题 | 可能造成的错误 | 核查与处理原则 |
| --- | --- | --- |
| **探针与脑组织相对漂移** | 同一单元波形／通道位置随时间改变；一次记录被分裂成多个 unit，或两个 unit 被错误合并。 | 检查位点深度随时间的峰值事件分布、模板漂移、校正后单元稳定性；保留漂移模型和未校正结果。(Steinmetz et al., 2021, Science; Pachitariu et al., 2024, Nat Methods) |
| **尖峰碰撞、遮蔽和漏检** | 同时发放的波形重叠；低幅度尖峰更易遗漏，偏移发放率及相关估计。 | 比较模板残差、振幅分布及不同排序器输出，不能把自动软件的“已检测”视为无漏检。(Yger et al., 2018, eLife; Magland et al., 2020, eLife) |
| **假单元／误合并／误拆分** | 记录到噪声或重复记账，或把不同细胞混为一组。 | 查看波形跨通道空间足迹、自／互相关、不应期违例、隔离指标和人工复核记录。(Hill et al., 2011, J Neurosci; Chung et al., 2017, Neuron) |
| **参考、接地与电子噪声** | 工频干扰、共同模式或异常通道可能模拟群体同步。 | 核对参考配置、坏道、噪声谱和实时监视；避免过度共模处理而抹除真实共变。(Harris et al., 2016, Nat Neurosci) |
| **运动／刺激伪迹** | 行为动作或外加刺激同步产生非神经电压瞬变。 | 以无刺激对照、参考通道、动作视频和波形时空结构区分噪声与尖峰。(Buzsáki et al., 2015, Neuron; Lakunina et al., 2026, Nat Methods) |
| **电极轨迹／脑区归属误差** | 错把单元分配到邻近脑区，制造虚假的跨脑区功能差异。 | 保留组织切片、轨迹重建、脑图谱版本及定位不确定性；特别复核边界单元。(International Brain Laboratory et al., 2025, eLife) |
| **跨天身份漂移** | 错把不同神经元作为同一单元追踪，导致错误学习／可塑性结论。 | 联合波形、深度、邻域关系和稳定度证据，报告匹配概率／阈值及敏感性分析。(Dhawale et al., 2017, eLife; Steinmetz et al., 2021, Science) |
| **细胞类型分类偏差** | 将放电率／波形分类错误解释为特定细胞类别。 | 若做身份研究，应提供光遗传标签、组织学、药理或其他真值，并报告混淆矩阵和测试数据分布。(Lima et al., 2009, PLoS One; Beau et al., 2025, Cell; Ye et al., 2025, Neuron) |
| **单元筛选与伪重复** | 按条件筛选“有响应”的单元后只报告显著结果；把来自同一只动物的许多 unit 当作独立动物。 | 预设单元选取和统计层级，按动物／会话建模或分组重抽样，不把 unit 数当成独立生物学样本数。(Harris et al., 2016, Nat Neurosci; International Brain Laboratory et al., 2025, eLife) |
| **数据与代码无法复现** | 原始电压丢失、坐标系／时钟不明、参数版本缺失会使排序结果无法复核。 | 归档原始连续信号、探针及通道映射、同步、质控、元数据和软件版本；适当使用 NWB。(Teeters et al., 2015, Neuron; Rübel et al., 2022, eLife) |

### 2. 一份不能只看单一阈值的单元质控清单

对每个最终纳入分析的 unit，至少检查：

- **波形：** 主要通道及邻近通道模板、幅度随时间的稳定性、波形是否符合合理的时空传播特征。
- **放电时序：** 自相关、不应期（refractory period）违例、是否出现高频异常或记录中断。
- **簇分离：** isolation distance、L-ratio、d-prime 或近邻污染评估等，选用适用于具体算法的质量指标。
- **漏检：** amplitude cutoff 等指标及峰幅度分布，并结合噪声估计；过低发放率时估计不稳定。
- **漂移：** 最大／累计位移、分段模板稳定性、脑组织相对移动后的波形一致性。
- **稳定出现：** presence ratio、会话内出现率、跨天候选匹配一致性。
- **人工审查记录：** 合并、分裂、排除的理由及排序器版本；记录处理流程是否被有意改变。

这些术语和质量思想有方法学文献基础，但**没有一套可脱离任务、脑区、排序器和下游统计目的而固定不变的通用阈值**。即便 Kilosort4 在模拟漂移和分类任务中有较好表现，也不能免除真实数据的生理合理性审查。(Hill et al., 2011, J Neurosci; Harris et al., 2016, Nat Neurosci; Pachitariu et al., 2024, Nat Methods)

### 3. 可重复性与独立验证

**算法级验证：** 配对 juxtacellular／细胞外记录可以提供部分尖峰地面真值；SpikeForest 等基准把排序器放在多种标注数据上比较。但所用真值的神经元类型、植入条件与信噪范围，未必覆盖新数据的难点。(Neto et al., 2016, J Neurophysiol; Yger et al., 2018, eLife; Magland et al., 2020, eLife)

**实验级验证：** 2025 年国际脑实验室跨实验室研究采用共享任务与重复靶点的协议，对多个基础电生理指标和分析结果进行比较。这表明标准化可以改进实验可比性；它不能证明所有脑区、物种或任务的 Neuropixels 结果天然一致。(International Brain Laboratory et al., 2025, eLife)

**神经生物学验证：** 明确区分重复观测到某一 spike 模式、同一细胞的稳定记录、同一种细胞类型，以及具有因果功能的细胞群。后几种结论分别需要更严格的时空匹配、分子／光遗传标签与功能干预。(Steinmetz et al., 2021, Science; Beau et al., 2025, Cell; Lakunina et al., 2026, Nat Methods)

### 4. 最小记录报告清单

- 研究对象、行为任务、动物／患者数量、纳入排除规则及伦理条件已说明
- 探针代际、针柄数、总位点、同时通道、位点映射和有效记录时长已记录
- 目标脑区、插入位置、组织学轨迹及定位不确定性已提供
- 连续原始信号、参考方式、频带、采样率和同步机制可复核
- 排除通道与排除 unit 的理由、漂移校正及软件版本已报告
- 各种质量指标和单元筛选阈值均有定义；single-unit 与 multi-unit 分开标记
- 生物学统计按动物／会话等独立层级处理，避免单位数造成伪重复
- 神经—行为关联没有越界写成因果、细胞身份或直接解剖连接
- 数据与算法来源清楚，公开或限制性共享的理由已说明

## 代表性实验或应用

### A. 硬件突破和长期记录

- **2017 年：Neuropixels 1.0。** 将密集电极位点和片上电子学整合至细长硅探针，示范在清醒啮齿动物中跨脑区大规模记录；是硬件工程与功能演示，而不是证明“全脑所有神经元都可记录”。(Jun et al., 2017, Nature)
- **2021 年：Neuropixels 2.0。** 通过缩小系统、优化电极几何和漂移校正，提高长期记录、自由行为与跨天比较的可行性；仍需研究层面的同一单元核验。(Steinmetz et al., 2021, Science)
- **2025 年：Neuropixels Ultra。** 更密集的空间采样提高特定皮层记录的检测表现并保留细小局部波形，推动亚细胞信号识别；局部精细波形和多脑区覆盖之间仍有设计权衡。(Ye et al., 2025, Neuron)
- **2026 年：Neuropixels Opto 原型。** 集成电学记录和双波段光输出，允许在特定实验中做空间可寻址刺激和光遗传标签；对非目标光响应与记录伪迹仍要独立控制。(Lakunina et al., 2026, Nat Methods)

### B. 多区域神经编码与公开数据

- **跨脑区任务变量：** 使用 Neuropixels 在小鼠视觉决策任务中追踪多个脑区的活动，显示动作相关信号和刺激／选择表征的分布并不相同；实验设计不能单独确定信息流因果方向。(Steinmetz et al., 2019, Nature)
- **小鼠视觉系统层级：** 大规模标准化电生理数据揭示视觉系统多区域单元反应特征，可支持对视觉层级的检验；结论依赖刺激范式与所覆盖脑区。(Siegle et al., 2021, Nature)
- **跨实验室复杂行为图谱：** 国际脑实验室的广域数据集联合多实验室、多个探针和标准化行为，描绘不同脑区在决策任务中的变量表征；数据整合是广域取样而非单探针全脑覆盖。(International Brain Laboratory et al., 2025, Nature)

### C. 跨物种扩展、细胞身份及解释边界

- **人类术中皮层记录：** 在严格控制条件下用 Neuropixels 测得人类皮层多单元活动，后续有专门协议；不等于具备常规诊疗或广泛长期植入适应证。(Paulk et al., 2022, Nat Neurosci; Coughlin et al., 2023, Nat Protoc)
- **非人灵长类深脑：** 2025 年 NHP 专用探针研究扩展大脑深处记录和多区域覆盖；同属高密度电极技术的其他设备应作为独立技术路线比较，而非混名。(Trautmann et al., 2025, Nat Neurosci; Liu et al., 2024, Nat Neurosci)
- **细胞类型分类：** 特定小脑细胞群体结合光遗传和药理验证可构造训练真值、提升分类；预测表现只适用于被检验的脑区、类别和模型分布。(Beau et al., 2025, Cell)
- **持续性记录研究：** 2017 年早期长期自动化电生理工作已建立跨周追踪方法的价值，说明长时程追踪并不是 NP 2.0 单一设备首创的科学问题。(Dhawale et al., 2017, eLife)

### D. 算法、QC 与复现基础设施

- **基准检验：** 从早期密集阵列算法和配对真值，到 SpikeForest／SpikeInterface，排序器的标准化比较逐渐成为必要研究环节。(Rossant et al., 2016, Nat Neurosci; Yger et al., 2018, eLife; Magland et al., 2020, eLife; Buccino et al., 2020, eLife)
- **Kilosort4：** 2024 年改进基于密集探针的自动排序和运动相关误差处理；值得作为软件方法证据，但不能宣称它对所有数据最好或已无需人工 QC。(Pachitariu et al., 2024, Nat Methods)
- **跨实验室再现性：** 标准化行为、记录与分析，有助于从“跨实验室可比较”走向更可靠的神经编码结论；仍要报告采样、脑区和分群差异。(International Brain Laboratory et al., 2025, eLife)

## 与其他方法的关系

| 方法 | 与 Neuropixels 的互补性 | 不能据此推出 |
| --- | --- | --- |
| **全细胞膜片钳／细胞内记录** | 能更直接测量细胞内膜电位、亚阈值电流或突触电流，可为胞外信号提供生物物理校验。(Gold et al., 2006, J Neurophysiol) | 膜片钳的小规模、受空间约束记录，不能简单替代跨脑区大规模胞外群体采样。 |
| **传统多电极阵列／四电极（tetrode）** | 同属胞外电生理，历史数据和自动排序研究可互相参照。(Rossant et al., 2016, Nat Neurosci) | 通道数、位点间距和漂移行为相同；不能跨几何结构套用相同单元质量阈值。 |
| **高密度光学 Ca²⁺ 成像** | 有机会观察细胞形态、亚细胞位置及同一视野细胞的长期变化，与 Neuropixels 的尖峰级时序互补。(Siegle & Steinmetz, 2026, Nat Rev Neurosci) | 光学 Ca²⁺ 信号可无模型地重建每一个动作电位，或直接等价于胞外 spike times。 |
| **EEG／MEG／皮层脑电** | 可获得较广空间范围的电活动或脑电磁场信息；其信号来源与 LFP 的物理机制部分相关。(Buzsáki et al., 2012, Nat Rev Neurosci) | EEG／MEG 和 Neuropixels 的信号都是单神经元放电或具有相同尺度的定位精度。 |
| **功能磁共振成像（fMRI）** | 能无创观察人类广域脑活动相关的血流动力学变化，与 Neuropixels 的高时间精度细胞外电学证据在尺度上互补。 | 同一位置的 BOLD 与尖峰可一一对应，或从两种方法的相关性直接获得突触方向。 |
| **光遗传学／optotagging** | 可在适当遗传和对照条件下操纵特定细胞群，给胞外 unit 添加更可信的身份线索；2026 年 Neuropixels Opto 将部分功能集成。(Lima et al., 2009, PLoS One; Lakunina et al., 2026, Nat Methods) | 只要有短潜伏期响应就能排除一切网络间接效应、光伪迹或细胞类型误标。 |
| **组织学、空间转录组与脑区图谱** | 为探针轨迹、脑区位置与细胞类型提供空间／分子参照。 | 对同一未标记胞外 unit 的分子类型实现无歧义自动匹配。 |
| **其他新型高通道硅探针** | 可从通道数、机械构型、不同物种和脑区接入能力对照 Neuropixels。(Liu et al., 2024, Nat Neurosci; Siegle & Steinmetz, 2026, Nat Rev Neurosci) | 不同品牌和设备型号应被视为 Neuropixels 的同一版本。 |

**方法选择：** 如果目标是“单试次、放电时序、群体协同”，优先考虑胞外电生理与严格 spike sorting；如果目标是“确定单一细胞的膜电位机制”，应补充细胞内方法；如果目标是“细胞类型的因果作用”，应在电极记录之外加上细胞类型验证与可解释的干预设计。(Harris et al., 2016, Nat Neurosci; Buzsáki et al., 2015, Neuron; Siegle & Steinmetz, 2026, Nat Rev Neurosci)

## 相关节点

**候选关联（普通文本；未验证 Obsidian Vault 中同名文件是否真实存在且拟公开，因此不创建 Wikilink）：**

- **神经活动测量：** 功能磁共振成像（fMRI）、脑电图（EEG）、脑磁图（MEG）、双光子钙成像、细胞外电生理、全细胞膜片钳、局部场电位（LFP）。
- **硬件与范式：** Neuropixels 1.0、Neuropixels 2.0、Neuropixels Ultra、Neuropixels Opto、光遗传学、光遗传标签（optotagging）、慢性植入。
- **信号与分析：** 动作电位、spike sorting、Kilosort、SpikeInterface、神经元群体编码、交叉相关、运动漂移校正、时间同步、脑区配准。
- **推断与证据质量：** 测量信度、可重复性、因果推断、伪重复、细胞类型识别、采样偏差。
- **此前讨论的跨轴主题：** 边界细胞、中央执行网络；若要添加双链，须先核实 Vault 中对应节点、路径和公开计划。

## 参考资料

以下引文统一采用 `(作者 et al., 年份, 期刊简称)` 格式；两位作者保留双方姓氏，单作者保留姓氏。表中所列为可核查的正式论文 DOI，包含**原始硬件研究、算法与地面真值验证、跨实验室重复、综述／方法标准和应用研究**。引用“方法综述／标准”表示它们提出或总结方法，不应冒充证明某项生物学因果关系的独立实验。

| 正文引用 | 作者、年份与论文题名 | 期刊信息 | DOI／永久链接 | 资料性质 | 主要支持与限制 |
| --- | --- | --- | --- | --- | --- |
| (Buzsáki, 2004, Nat Neurosci) | Buzsáki G. Large-scale recording of neuronal ensembles. | Nat Neurosci 7:446–451 (2004) | [DOI](https://doi.org/10.1038/nn1233) | 观点／技术背景 | 说明群体神经活动测量的科学动机；不构成 Neuropixels 性能测试。 |
| (Gold et al., 2006, J Neurophysiol) | Gold C, Henze DA, Koch C, Buzsáki G. On the origin of the extracellular action potential waveform: a modeling study. | J Neurophysiol 95:3113–3128 (2006) | [DOI](https://doi.org/10.1152/jn.00979.2005) | 生物物理建模 | 说明胞外波形受形态、膜电流和电极位置影响；模型不能单独确定真实细胞身份。 |
| (Lima et al., 2009, PLoS One) | Lima SQ, Hromádka T, Znamenskiy P, Zador AM. PINP: A New Method of Tagging Neuronal Populations for Identification during In Vivo Electrophysiological Recording. | PLoS One 4:e6099 (2009) | [DOI](https://doi.org/10.1371/journal.pone.0006099) | 原始实验／光遗传标签 | 证明有条件地将遗传定义与胞外单元关联；须排除光刺激间接效应。 |
| (Hill et al., 2011, J Neurosci) | Hill DN, Mehta SB, Kleinfeld D. Quality Metrics to Accompany Spike Sorting of Extracellular Signals. | J Neurosci 31:8699–8705 (2011) | [DOI](https://doi.org/10.1523/JNEUROSCI.0971-11.2011) | 方法论文／单元质控 | 提出用不应期、遗漏率等指标审视分类质量；单一指标不足以保证真实性。 |
| (Buzsáki et al., 2012, Nat Rev Neurosci) | Buzsáki G, Anastassiou CA, Koch C. The origin of extracellular fields and currents—EEG, ECoG, LFP and spikes. | Nat Rev Neurosci 13:407–420 (2012) | [DOI](https://doi.org/10.1038/nrn3241) | 机制综述 | 解释胞外电场及各类电信号源；LFP 不能简单归因于某一神经元。 |
| (Einevoll et al., 2013, Nat Rev Neurosci) | Einevoll GT, Kayser C, Logothetis NK, Panzeri S. Modelling and analysis of local field potentials for studying the function of cortical circuits. | Nat Rev Neurosci 14:770–785 (2013) | [DOI](https://doi.org/10.1038/nrn3599) | 方法综述／LFP | 解释 LFP 与局部电流源、组织几何及体积传导的关系；频带并非唯一生理过程。 |
| (Buzsáki et al., 2015, Neuron) | Buzsáki G, Stark E, Berényi A, et al. Tools for Probing Local Circuits: High-Density Silicon Probes Combined with Optogenetics. | Neuron 86:92–105 (2015) | [DOI](https://doi.org/10.1016/j.neuron.2015.01.028) | 方法综述／联合干预 | 讨论高密度电极结合光遗传操作的价值和局限；不是 Neuropixels Opto 的原始验证。 |
| (Teeters et al., 2015, Neuron) | Teeters JL, Godfrey K, Young R, et al. Neurodata Without Borders: Creating a Common Data Format for Neurophysiology. | Neuron 88:629–634 (2015) | [DOI](https://doi.org/10.1016/j.neuron.2015.10.025) | 数据标准／NWB | 支持原始神经生理数据与元数据的规范保存；格式统一不等于数据质量自动合格。 |
| (Neto et al., 2016, J Neurophysiol) | Neto JP, Lopes G, Frazão J, et al. Validating silicon polytrodes with paired juxtacellular recordings: method and dataset. | J Neurophysiol 116:892–903 (2016) | [DOI](https://doi.org/10.1152/jn.00103.2016) | 配对记录／地面真值 | 以近细胞记录评估胞外 spike 检出；并非所有探针和脑区的普遍准确率。 |
| (Rossant et al., 2016, Nat Neurosci) | Rossant C, Kadir SN, Goodman DFM, et al. Spike sorting for large, dense electrode arrays. | Nat Neurosci 19:634–641 (2016) | [DOI](https://doi.org/10.1038/nn.4268) | 算法／密集电极排序 | 提出面向密集阵列的 spike sorting 方法；性能依数据、噪声及细胞密度变化。 |
| (Harris et al., 2016, Nat Neurosci) | Harris KD, Quiroga RQ, Freeman J, Smith SL. Improving data quality in neuronal population recordings. | Nat Neurosci 19:1165–1174 (2016) | [DOI](https://doi.org/10.1038/nn.4365) | 质量控制综述 | 讨论大型群体记录中伪迹、采样偏差和单元质量；属于方法建议的综合。 |
| (Chung et al., 2017, Neuron) | Chung JE, Magland JF, Barnett AH, et al. A Fully Automated Approach to Spike Sorting. | Neuron 95:1381–1394.e6 (2017) | [DOI](https://doi.org/10.1016/j.neuron.2017.08.030) | 原始算法／MountainSort | 自动化 spike sorting 和聚类质量量化；不是对所有 Neuropixels 数据的零误差承诺。 |
| (Jun et al., 2017, Nature) | Jun JJ, Steinmetz NA, Siegle JH, et al. Fully integrated silicon probes for high-density recording of neural activity. | Nature 551:232–236 (2017) | [DOI](https://doi.org/10.1038/nature24636) | 原始硬件／跨脑区记录 | Neuropixels 1.0 奠基：960 电极位点、384 同步通道；位点／通道／单元数不可混为一谈。 |
| (Dhawale et al., 2017, eLife) | Dhawale AK, Poddar R, Wolff SBE, et al. Automated long-term recording and analysis of neural activity in behaving animals. | eLife 6:e27702 (2017) | [DOI](https://doi.org/10.7554/eLife.27702) | 原始方法／长期胞外记录 | 展示长期连续记录和跨天单元追踪的可行性；并非 Neuropixels 2.0 特有结果。 |
| (Siegle et al., 2017, J Neural Eng) | Siegle JH, Cuevas López A, Patel YA, et al. Open Ephys: an open-source, plugin-based platform for multichannel electrophysiology. | J Neural Eng 14:045003 (2017) | [DOI](https://doi.org/10.1088/1741-2552/aa5eea) | 采集软件／系统方法 | 支持开放采集与同步生态；设备兼容性需以相应硬件版本和文档另行核实。 |
| (Yger et al., 2018, eLife) | Yger P, Spampinato GLB, Esposito E, et al. A spike sorting toolbox for up to thousands of electrodes validated with ground truth recordings in vitro and in vivo. | eLife 7:e34518 (2018) | [DOI](https://doi.org/10.7554/eLife.34518) | 算法／配对真值验证 | 以不同真值条件评估排序；算法表现不是通用单元真实性证明。 |
| (Steinmetz et al., 2019, Nature) | Steinmetz NA, Zatka-Haas P, Carandini M, Harris KD. Distributed coding of choice, action and engagement across the mouse brain. | Nature 576:266–273 (2019) | [DOI](https://doi.org/10.1038/s41586-019-1787-x) | 原始实验／跨脑区行为编码 | 展示分布式视觉、决策及动作相关信号；编码相关性不等于必需因果作用。 |
| (Magland et al., 2020, eLife) | Magland J, Jun JJ, Lovero E, et al. SpikeForest, reproducible web-facing ground-truth validation of automated neural spike sorters. | eLife 9:e55167 (2020) | [DOI](https://doi.org/10.7554/eLife.55167) | 基准资源／算法比较 | 用 ground-truth 数据比较排序器；基准覆盖并非现实数据所有噪声状态。 |
| (Buccino et al., 2020, eLife) | Buccino AP, Hurwitz CL, Garcia S, et al. SpikeInterface, a unified framework for spike sorting. | eLife 9:e61834 (2020) | [DOI](https://doi.org/10.7554/eLife.61834) | 软件框架／可复现流程 | 统一排序、质控和比较接口；重现软件流程不保证生理解释正确。 |
| (Steinmetz et al., 2021, Science) | Steinmetz NA, Aydin Ç, Lebedeva A, et al. Neuropixels 2.0: A miniaturized high-density probe for stable, long-term brain recordings. | Science 372:eabf4588 (2021) | [DOI](https://doi.org/10.1126/science.abf4588) | 原始硬件＋漂移算法／多实验室 | NP 2.0 探针缩小、四针柄 5,120 位点和长期追踪；需要严格的跨天同一性验证。 |
| (Siegle et al., 2021, Nature) | Siegle JH, Jia X, Durand S, et al. Survey of spiking in the mouse visual system reveals functional hierarchy. | Nature 592:86–92 (2021) | [DOI](https://doi.org/10.1038/s41586-020-03171-x) | 多区域数据集／视觉系统 | 大规模神经放电记录与功能层级分析；受刺激集、脑区及筛选标准约束。 |
| (Paulk et al., 2022, Nat Neurosci) | Paulk AC, Kfir Y, Khanna AR, et al. Large-scale neural recordings with single neuron resolution using Neuropixels probes in human cortex. | Nat Neurosci 25:252–263 (2022) | [DOI](https://doi.org/10.1038/s41593-021-00997-0) | 原始人类皮层术中记录 | 证明严格条件下人类脑表面相关皮层短时记录可行；并非广泛常规植入适应证。 |
| (Rübel et al., 2022, eLife) | Rübel O, Tritt A, Ly R, et al. The Neurodata Without Borders ecosystem for neurophysiological data science. | eLife 11:e78362 (2022) | [DOI](https://doi.org/10.7554/eLife.78362) | 开放数据标准／生态 | 规范时间序列、单元及元数据组织与共享；不保证原始 signal 已通过生理 QC。 |
| (Coughlin et al., 2023, Nat Protoc) | Coughlin B, Muñoz W, Kfir Y, et al. Modified Neuropixels probes for recording human neurophysiology in the operating room. | Nat Protoc 18:2927–2953 (2023) | [DOI](https://doi.org/10.1038/s41596-023-00871-2) | 协议／人类术中使用 | 提供特殊伦理和环境下的实验方案；并不是临床常规使用的通用许可。 |
| (Pachitariu et al., 2024, Nat Methods) | Pachitariu M, Sridhar S, Pennington J, Stringer C. Spike sorting with Kilosort4. | Nat Methods 21:914–921 (2024) | [DOI](https://doi.org/10.1038/s41592-024-02232-7) | 原始算法／漂移与排序 | Kilosort4 在多类模拟基准中改善分类；仍需在真实数据上审查单元质量。 |
| (Liu et al., 2024, Nat Neurosci) | Liu Y, Jia H, Sun H, et al. A high-density 1,024-channel probe for brain-wide recordings in non-human primates. | Nat Neurosci 27:1620–1631 (2024) | [DOI](https://doi.org/10.1038/s41593-024-01692-6) | 独立设备路线／对照 | 展示 Neuropixels 之外的高密度探针设计；不是 Neuropixels 某一代型号。 |
| (International Brain Laboratory et al., 2025, eLife) | International Brain Laboratory. Reproducibility of in vivo electrophysiological measurements in mice. | eLife 13:RP100840（正式发表版本 2025） | [DOI](https://doi.org/10.7554/eLife.100840.3) | 跨实验室复核／受评审版本 | 共用任务、定位及流程能提高跨实验室比较的再现性；不同实验问题不可直接外推。 |
| (International Brain Laboratory et al., 2025, Nature) | International Brain Laboratory, Angelaki D, Benson B, et al. A brain-wide map of neural activity during complex behaviour. | Nature 645:177–191 (2025) | [DOI](https://doi.org/10.1038/s41586-025-09235-0) | 跨实验室脑广域数据集 | 大规模集中记录可定位不同脑区的任务变量表征；不能从共激活断言定向因果。 |
| (Trautmann et al., 2025, Nat Neurosci) | Trautmann EM, Hesse JK, Stine GM, et al. Large-scale high-density brain-wide neural recording in nonhuman primates. | Nat Neurosci 28:1562–1575 (2025) | [DOI](https://doi.org/10.1038/s41593-025-01976-5) | 原始硬件／非人灵长类 | NHP 长针柄版本提供深脑接入及高密度记录；并非标准小鼠探针的直接规格。 |
| (Ye et al., 2025, Neuron) | Ye Z, Shelton AM, Shaker JR, et al. Ultra-high-density Neuropixels probes improve detection and identification in neuronal recordings. | Neuron 113:3966–3982.e12 (2025) | [DOI](https://doi.org/10.1016/j.neuron.2025.08.030) | 原始硬件／NP Ultra | 更密集位点提高部分条件下检测率与波形信息；细胞类型分类是有验证范围的概率预测。 |
| (Beau et al., 2025, Cell) | Beau M, Herzfeld DJ, Naveros F, et al. A deep learning strategy to identify cell types across species from high-density extracellular recordings. | Cell 188:2218–2234.e22 (2025) | [DOI](https://doi.org/10.1016/j.cell.2025.01.041) | 跨物种单元分类／多方法验证 | 特定小脑细胞类别的训练与验证可提高身份推断；不能推广为所有脑区普适识别。 |
| (Lakunina et al., 2026, Nat Methods) | Lakunina AA, Socha KZ, Ladd AE, et al. Neuropixels Opto: combining high-resolution electrophysiology and optogenetics. | Nat Methods 23:1207–1216 (2026) | [DOI](https://doi.org/10.1038/s41592-026-03076-z) | 原始原型／光电联合 | 同支探针联合记录、光激活和 optotagging；原型实验不等同于已普及的商用技术。 |
| (Siegle & Steinmetz, 2026, Nat Rev Neurosci) | Siegle JH, Steinmetz NA. Large-scale electrophysiology at single-spike resolution. | Nat Rev Neurosci 27:395–415 (2026) | [DOI](https://doi.org/10.1038/s41583-026-01042-4) | 领域综述／设备及实践 | 比较大规模胞外记录平台、复现和共享挑战；为综合框架，不代替具体原始实验。 |

### 待人工审核与发布前验收

1. **硬件版本：** 用实际探针记录表核对本节点的 NP 1.0、NP 2.0、Ultra、NHP 与 Opto 分类。尤其注意 2026 年 Opto 的论文为原型研究，不能直接将其描述为所有实验室均可用的成熟商业产品。
2. **实验设计：** 如果之后将本文作为实验 SOP 使用，须补充所在单位的动物／人体伦理要求、设备版本、组织学定位、同步校准和具体质控流程。本文不提供适用于所有实验的通用手术步骤或数值阈值。
3. **科研证据：** 针对要引用的结论，核对是否为单探针记录、跨会话追踪还是跨实验室汇总数据；对每一个细胞类型或因果主张确认是否有独立验证。
4. **跨物种外推：** 检查小鼠／大鼠、非人灵长类及人类短时术中研究的适用边界，不把可行性验证解释成常规临床效用已成立。
5. **重复与双链：** 检查 Vault 中是否已有「Neuropixels／Neuropixels电极」的规范节点及真实关联条目。只有确认目标存在且计划公开后，才添加 Obsidian Wikilink。
6. **发布：** 本文件维持 `publish: false` 与 `review_status: needs_review`；人工完成科学、引用、元数据及双链审核后，才手动批准发布并更新 03 轴索引及相关主页。
