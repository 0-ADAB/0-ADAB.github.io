---
publish: true
aliases:
  - ABCD 研究
  - Adolescent Brain Cognitive Development
  - ABCD 脑网络
  - ABCD RSFC
title: ABCD多站点脑网络重复验证
description: ABCD 研究 21 个站点 2,188 名儿童的发现—重复二分设计显示，静息态功能连接与功能网络架构在两个独立子样本间高度可重复；站点效应不强但扫描仪厂商效应大且可重复，并呈「距离越远差异越大」模式。配套的多站点可靠性、批次协调方法与脑—表型关联的样本量门槛，共同限定了多站点数据可合并与可推广的边界。
created: 2026-10-15T21:58:29.229+08:00
modified: 2026-11-14T12:41:03.427+08:00
tags:
  - 类型/证据
  - 层/证据
---

# ABCD多站点脑网络重复验证

> **观察到什么：** ABCD 研究（Adolescent Brain Cognitive Development）在 21 个站点采集了 2,188 名 9–10 岁儿童的静息态 fMRI。Marek 等把样本按人口学变量匹配地切成发现集（N = 1,166）与重复集（N = 1,022）后，在完全独立的重复集上检验发现集识别出的效应：儿童功能脑网络的个体差异在两组间**高度可重复**（Marek et al., 2019, Dev Cogn Neurosci）。更具方法学意味的是，项目量化出三类变异来源——采集**站点**效应不强，但扫描仪**厂商**效应大且可重复，并呈「短距离连接差异小、长距离连接差异大」的距离依赖模式（Marek et al., 2019, Dev Cogn Neurosci）。控制潜在混淆后，若干高阶网络间功能连接与一般认知的关联在重复集中成立，但效应量很小，属于「需数千量级样本才稳定」的那类关联（Marek et al., 2019, Dev Cogn Neurosci; Marek et al., 2022, Nature）。这一发现既支持多站点数据可合并，也提示合并前须对厂商效应建模或做敏感性分析（Pomponio et al., 2020, NeuroImage）。

## 原始研究信息

本节点汇集 ABCD 多站点重复验证研究及其方法学背景，按四类组织：

- **核心重复发现**：Marek 等（2019，Dev Cogn Neurosci）以 ABCD 静息态数据做可重复性框架分析，是本节的主证据。
- **ABCD 基础设施**：Volkow 等（2018，Dev Cogn Neurosci）总体构思；Casey 等（2018，Dev Cogn Neurosci）21 站点统一采集协议；Barch 等（2018，Dev Cogn Neurosci）表型与评估框架；Garavan 等（2018，Dev Cogn Neurosci）招募设计；Luciana 等（2018，Dev Cogn Neurosci）神经认知电池；Hagler 等（2019，NeuroImage）影像处理与质控流程。
- **网络架构测量基础**：Power 等（2011，Neuron）与 Gordon 等（2014，Cereb Cortex）定义了功能网络分区与节点方案，是「网络架构可重复性」结论赖以为据的度量框架。
- **多站点可靠性与协调方法**：Noble 等（2017，NeuroImage）旅行受试者研究、Badhwar 等（2020，NeuroImage）单个体跨 13 站点研究、Parsons 等（2024，Imaging Neurosci）ABCD 纵向多站点稳定性，从经验上刻画跨站点一致性；Johnson 等（2007，Biostatistics）的 ComBat、Fortin 等（2017，NeuroImage）与 Pomponio 等（2020，NeuroImage）的协调扩展，给出校正站点/厂商效应的工具；Nichols 等（2017，Nat Neurosci）为多站点 MRI 最佳实践共识。
- **样本量逻辑与负结果**：Marek 等（2022，Nature）证明脑—表型关联需数千量级个体才可重复；Noble 等（2019，NeuroImage）的 meta 分析给出单条功能连接重测信度平均 ICC ≈ 0.29；Power 等（2012，NeuroImage）揭示头动产生系统性假连接；Elliott 等（2020，Psychol Sci）显示任务态 fMRI 指标重测信度偏低；Yarkoni（2020，Behav Brain Sci）从概念上批判「泛化危机」；Spisak 等（2023，Nature）与 Kang 等（2024，Nature）则对「需数千人」给出竞争性/补充性解释。

## 实验设计与对象

**队列与采集。** ABCD 是一项覆盖 21 个站点、2,188 名 9–10 岁儿童的纵向脑发育队列，采用统一的 MRI 采集协议与跨站点质控（Volkow et al., 2018, Dev Cogn Neurosci; Casey et al., 2018, Dev Cogn Neurosci; Hagler et al., 2019, NeuroImage）。统一协议与质控是多站点结论成立的工程前提。

**发现集—重复集二分。** 这是本节点最关键的设计特征：样本按人口学变量匹配地切成发现集（N = 1,166）与重复集（N = 1,022）两半，先在发现集上识别效应，再在完全独立的重复集上检验——重复集不参与任何效应识别，从设计上避免了「同一数据上识别即验证」的循环（Marek et al., 2019, Dev Cogn Neurosci）。

**网络架构的度量。** 「功能网络架构」由静息态功能连接矩阵经分区方案（如 Power 等 2011，Neuron；Gordon 等 2014，Cereb Cortex）聚合为网络节点与边后刻画；可重复性检验比较的是节点—网络层面的群体结构，而非单条连接的个体值（Marek et al., 2019, Dev Cogn Neurosci）。

**效应分解。** 项目量化了站点（site）、扫描仪厂商（manufacturer）与个体水平噪声（含头动）三类变异来源。厂商效应的模式是「短距离连接差异小、长距离连接差异大」，提示厂商差异进入的是全局信号与连接结构而非随机噪声（Marek et al., 2019, Dev Cogn Neurosci）。

## 核心结果

**1. 可重复的网络架构。** 静息态功能连接与功能网络架构在发现集与重复集间高度可重复——即「儿童之间的网络差异」这一群体结构本身是稳定可测的（Marek et al., 2019, Dev Cogn Neurosci）。Gratton 等（2018，Neuron）在同一人多次扫描中进一步证明，群与个体因子主导网络组织、认知状态与日间变异贡献很小，从方法学上支持「个体网络差异可稳定测量」。

**2. 站点效应弱、厂商效应大且可重复。** 站点（site）效应不强；扫描仪厂商（manufacturer）效应大、可重复，并随连接距离增大而增大（Marek et al., 2019, Dev Cogn Neurosci）。这一区分对多站点研究的方法学选择有直接意义：简单地按站点回归未必必要，但按厂商建模或做厂商敏感性分析通常是必要的（Pomponio et al., 2020, NeuroImage）。

**3. 对照：厂商效应并非普适。** 需要强调，厂商效应不是跨研究一致的结论。Noble 等（2017，NeuroImage）的旅行受试者研究（8 名受试者 × 8 站点，NAPLS）在单变量连接上未发现主要站点或厂商效应，个体方差约为站点方差的 3 倍；Badhwar 等（2020，NeuroImage）让同一人在 13 站点、3 厂商 2.5 年间扫描，多元连接图高度一致，但厂商间仍存在可识别的系统性偏移。可见「厂商效应必须控制」是有条件的——它取决于协议、扫描时长与被试内/间设计，不能泛化为所有多站点研究的铁律（Marek et al., 2019, Dev Cogn Neurosci; Noble et al., 2017, NeuroImage; Badhwar et al., 2020, NeuroImage）。

**4. 脑—行为关联效应量小。** 控制混淆变量后，若干高阶网络间功能连接与一般认知的关联在重复集中成立，但效应量处于常规样本量无法稳定检测的区间——这正是 Marek 等（2022，Nature）在三个数据集、合计约 5 万个体上证明的「脑—表型关联需数千量级才稳定」的 ABCD 实例（Marek et al., 2019, Dev Cogn Neurosci; Marek et al., 2022, Nature）。

**5. 信度背景与纵向稳定性。** 单条功能连接的重测信度平均 ICC ≈ 0.29（Noble et al., 2019, NeuroImage），这意味着网络层面的稳定结论可建立在大量连接的平均之上，而单条连接的个体差异测量噪声很大。Parsons 等（2024，Imaging Neurosci）在 ABCD 内部进一步显示，皮层灰质指标的纵向稳定性随脑区、指标与测试站点变化，为多站点测量的可靠性提供了纵向证据。

## 与哪些科学主张有关？

本节点为跨主题证据档案，与「多站点数据能否合并」「组间关联 vs. 个体预测」两类推断规则相关。相关 Claim 节点尚未创建，此处以文字列出：

- **「大规模多站点静息态数据的网络指标可重复」**：本项目直接证据，属**较确定**（限于儿童样本、所纳入站点与统一协议）。
- **「厂商效应需要被识别与建模」**：本项目量化证据，但 Noble 等（2017，NeuroImage）与 Badhwar 等（2020，NeuroImage）提示其强度与设计相关，属**较确定但条件性**。
- **「功能连接可直接预测个体认知水平」**：关联效应量小、信度受限，属**未确立**（Elliott et al., 2020, Psychol Sci; Noble et al., 2019, NeuroImage; Marek et al., 2022, Nature）。

## 证据质量

- **发现—重复二分是设计优势。** 重复集完全不参与效应识别，比跨研究比较更严格地检验了可重复性（Marek et al., 2019, Dev Cogn Neurosci）。
- **横断面设计。** 单一时点的 9–10 岁样本不能支持发育轨迹推断；重复性指的是「跨子样本」，不是「跨时间」（Marek et al., 2019, Dev Cogn Neurosci; Parsons et al., 2024, Imaging Neurosci）。
- **站点与厂商范围有限。** 21 个站点的设备与协议在该项目内协调；结论外推到其他采集体系需要新的验证，且与 NAPLS 旅行受试者研究（Noble et al., 2017, NeuroImage）的结论并不完全一致，提示厂商效应具有研究依赖性。
- **行为关联的效应量小。** 脑—行为关联的效应量处于常规样本量无法稳定检测的区间，本项目的价值在于它同时报告了关联与重复性，而非宣称关联已确立（Marek et al., 2019, Dev Cogn Neurosci; Marek et al., 2022, Nature）。
- **头动混淆未完全消除。** 即使做了标准头动回归，残存头动仍可能污染长距连接，而长距连接恰是厂商效应最显著之处，二者需联合考量（Power et al., 2012, NeuroImage; Marek et al., 2019, Dev Cogn Neurosci）。

## 不能推出什么？

1. **不能把「网络架构可重复」外推为「所有 fMRI 指标可重复」。** 本项目针对静息态功能连接与网络指标；任务态指标的重测信度明显更低（Elliott et al., 2020, Psychol Sci），局部指标与其他扫描模式需各自验证。
2. **不能忽略、也不能夸大厂商效应。** 「站点效应不强」不等于「采集差异不重要」，但 Noble 等（2017，NeuroImage）显示单变量连接上厂商效应也可不显著；正确的推论是「须针对具体设计与协议检验并建模厂商效应」，而非一律当作主导混淆（Marek et al., 2019, Dev Cogn Neurosci; Noble et al., 2017, NeuroImage; Pomponio et al., 2020, NeuroImage）。
3. **不能从横断面数据推断发育变化。** 9–10 岁单时点的可重复性与发育轨迹是不同问题（Marek et al., 2019, Dev Cogn Neurosci）。
4. **不能把「可重复」当作「可预测个体」。** 组间关联成立与个体层面预测达标是两件事，后者受重测信度（Noble et al., 2019, NeuroImage；ICC ≈ 0.29）与效应量（Marek et al., 2022, Nature）双重约束；Yarkoni（2020，Behav Brain Sci）从概念上指出这类关联普遍缺乏跨样本泛化验证。
5. **不能把「需数千人」当作脑—表型研究的唯一结论。** Spisak 等（2023，Nature）指出多元 BWAS 在中等样本即可复现；Kang 等（2024，Nature）强调研究设计特征（而不仅是样本量）提升可重复性——二者与 Marek 等（2022，Nature）互补，提示门槛是方法依赖的。

## 相关节点

- [[04_证据与推理轴/04_证据与推理轴|证据与推理轴]]：证据质量、推断边界与跨主题证据档案在总体框架中的位置。
- [[04_证据与推理轴/证据质量/可重复性|可重复性]]：样本量门槛、测量信度与外部验证在总体框架中的位置。
- [[01_科学问题轴/01_科学问题轴|科学问题轴]]：发育与认知类科学问题节点将来应如何引用本档案。
- [[02_研究对象与尺度轴/02_研究对象与尺度轴|研究对象与尺度轴]]：静息态等功能状态对象节点的证据边界。

**待建候选节点（尚未创建，故暂不添加无效双链）**：静息态功能连接、多站点研究、扫描仪厂商效应、发现集与重复集、脑—行为关联。

## 关键文献与资料

**编排说明：** 正文引注统一为「作者—年份—期刊简称」：括号引注写作 `(Author et al., Year, Journal)`，中文叙述引注写作「作者 等（Year，Journal）」。三位及以上作者用 `et al.`，两位作者用 `&`，单作者用单姓氏。下表按出版年升序排列（同年按第一作者姓氏字母序），「正文引用」列为对应的括号形式。书目元数据经 Crossref 逐条核对；资料更新至 2026 年 10 月。

| 正文引用 | 作者、年份与论文题名 | 期刊／卷页 | DOI／永久入口 | 证据性质 | 主要支持及限制 |
| --- | --- | --- | --- | --- | --- |
| (Johnson et al., 2007, Biostatistics) | Johnson WE; Li C; Rabinovic A (2007). Adjusting batch effects in microarray expression data using empirical Bayes methods | Biostatistics 8(1):118-127 | [原文入口](https://doi.org/10.1093/biostatistics/kxj037) | 方法（批次效应校正，ComBat） | 经验贝叶斯批次校正，是后续神经影像跨站点协调的基础方法；非 ABCD 特异性，最初为基因芯片提出。 |
| (Power et al., 2011, Neuron) | Power JD; Cohen AL; Nelson SM; … Petersen SE (2011). Functional network organization of the human brain | Neuron 72(4):665-678 | [原文入口](https://doi.org/10.1016/j.neuron.2011.09.006) | 方法（功能网络架构定义，264 节点分区） | 定义了网络节点分区与功能网络组织框架；为 ABCD 网络可重复性提供度量基础。 |
| (Power et al., 2012, NeuroImage) | Power JD; Barnes KA; Snyder AZ; Schlaggar BL; Petersen SE (2012). Spurious but systematic correlations in functional connectivity MRI networks arise from subject motion | NeuroImage 59:2142-2154 | [原文入口](https://doi.org/10.1016/j.neuroimage.2011.10.018) | 方法／伪迹 | 头动产生系统性假连接，是多站点 rsFC 必须控制的混淆；部分站点/厂商差异可由头动分布差异解释。 |
| (Gordon et al., 2014, Cereb Cortex) | Gordon EM; Laumann TO; Adeyemo B; … Petersen SE (2014). Generation and evaluation of a cortical area parcellation from resting-state correlations | Cereb Cortex 26(1):288-303 | [原文入口](https://doi.org/10.1093/cercor/bhu239) | 方法（皮层分区） | 基于静息态相关的皮层分区，常作网络节点定义；影响网络架构度量的可比性。 |
| (Nichols et al., 2017, Nat Neurosci) | Nichols TE; Das S; Eickhoff SB; … Yeo BTT (2017). Best practices in data analysis and sharing in neuroimaging using MRI | Nat Neurosci 20:299-303 | [原文入口](https://doi.org/10.1038/nn.4500) | 方法／共识 | 多站点 MRI 分析、共享与质控最佳实践共识；直接指导跨站点研究的设计与协调。 |
| (Noble et al., 2017, NeuroImage) | Noble S; Scheinost D; Finn ES; … Constable RT (2017). Multisite reliability of MR-based functional connectivity | NeuroImage 146:959-970 | [原文入口](https://doi.org/10.1016/j.neuroimage.2016.10.020) | 多站点观察（旅行受试者） | 8 名受试者 × 8 站点（NAPLS），单变量连接无主要站点/厂商效应、个体效应主导（个体方差≈站点 3 倍）；5 分钟扫描 ICC 0.07–0.17，25 分钟升至 0.21–0.36；与 ABCD 的厂商效应发现形成对照。 |
| (Barch et al., 2018, Dev Cogn Neurosci) | Barch DM; Albaugh MD; Avenevoli S; … Sher KJ (2018). Demographic, physical and mental health assessments in the adolescent brain and cognitive development study: Rationale and description | Dev Cogn Neurosci 32:55-66 | [原文入口](https://doi.org/10.1016/j.dcn.2017.10.010) | ABCD 基础设施 | ABCD 人口学、体格与心理健康评估框架；为发现集/重复集匹配提供依据。 |
| (Casey et al., 2018, Dev Cogn Neurosci) | Casey BJ; Cannonier T; … Dale AM (2018). The Adolescent Brain Cognitive Development (ABCD) study: Imaging acquisition across 21 sites | Dev Cogn Neurosci 32:43-54 | [原文入口](https://doi.org/10.1016/j.dcn.2018.03.001) | ABCD 基础设施 | 21 站点统一 MRI 采集协议；多站点可重复性的工程前提。 |
| (Garavan et al., 2018, Dev Cogn Neurosci) | Garavan H; Bartsch H; Conway K; … Zahs D (2018). Recruiting the ABCD sample: Design considerations and procedures | Dev Cogn Neurosci 32:16-22 | [原文入口](https://doi.org/10.1016/j.dcn.2018.04.004) | ABCD 基础设施 | ABCD 招募设计与流程，保证样本人口学代表性；支撑发现集/重复集可比性。 |
| (Gratton et al., 2018, Neuron) | Gratton C; Laumann TO; Nielsen AN; … Petersen SE (2018). Functional Brain Networks Are Dominated by Stable Group and Individual Factors, Not Cognitive or Daily Variation | Neuron 98:439-452.e5 | [原文入口](https://doi.org/10.1016/j.neuron.2018.03.035) | 方法／稳定性 | 同一人多次扫描显示群与个体因子稳定、认知状态与日间变异贡献小；支持「个体网络差异可重复」。 |
| (Luciana et al., 2018, Dev Cogn Neurosci) | Luciana M; Bjork JM; Nagel BJ; … Banich MT (2018). Adolescent neurocognitive development and impacts of substance use: Overview of the ABCD baseline neurocognition battery | Dev Cogn Neurosci 32:67-79 | [原文入口](https://doi.org/10.1016/j.dcn.2018.02.006) | ABCD 基础设施 | ABCD 基线神经认知电池；为脑—行为关联分析提供表型。 |
| (Volkow et al., 2018, Dev Cogn Neurosci) | Volkow ND; Koob GF; … Weiss SRB (2018). The conception of the ABCD study: From substance use to a broad NIH collaboration | Dev Cogn Neurosci 32:4-7 | [原文入口](https://doi.org/10.1016/j.dcn.2017.10.002) | ABCD 基础设施 | ABCD 总体构思与 NIH 协作框架；21 站点、9–10 岁儿童队列来源。 |
| (Hagler et al., 2019, NeuroImage) | Hagler DJ; Hatton S; … Dale AM (2019). Image processing and analysis methods for the Adolescent Brain Cognitive Development Study | NeuroImage 202:116091 | [原文入口](https://doi.org/10.1016/j.neuroimage.2019.116091) | ABCD 基础设施（处理/QC） | ABCD 影像处理与质控流程；站点/厂商差异须在预处理阶段被识别与建模。 |
| (Marek et al., 2019, Dev Cogn Neurosci) | Marek S; Tervo-Clemmens B; Nielsen AN; … Dosenbach NUF (2019). Identifying reproducible individual differences in childhood functional brain networks: An ABCD study | Dev Cogn Neurosci 40:100706 | [原文入口](https://doi.org/10.1016/j.dcn.2019.100706) | 核心、多站点观察（内置重复集） | 21 站点 2,188 人；发现集 N = 1,166、重复集 N = 1,022；网络架构高度可重复；站点效应弱、厂商效应大且可重复（距离越远差异越大）；横断面 9–10 岁。 |
| (Noble et al., 2019, NeuroImage) | Noble S; Scheinost D; Constable RT (2019). A decade of test-retest reliability of functional connectivity: A systematic review and meta-analysis | NeuroImage 203:116157 | [原文入口](https://doi.org/10.1016/j.neuroimage.2019.116157) | 方法／meta | 单条功能连接重测信度平均 ICC ≈ 0.29；信度上限约束个体层面预测；非 ABCD 特异性。 |
| (Badhwar et al., 2020, NeuroImage) | Badhwar A; Collin-Verreault E; … Bellec P (2020). Multivariate consistency of resting-state fMRI connectivity maps acquired on a single individual over 2.5 years, 13 sites and 3 vendors | NeuroImage 205:116210 | [原文入口](https://doi.org/10.1016/j.neuroimage.2019.116210) | 多站点观察（单个体） | 同一人在 13 站点、3 厂商 2.5 年扫描，多元连接图高度一致；个体网络指纹可跨站点复现，但厂商间存在可识别系统性偏移。 |
| (Elliott et al., 2020, Psychol Sci) | Elliott ML; Knodt AR; … Hariri AR (2020). What Is the Test-Retest Reliability of Common Task-Functional MRI Measures? New Empirical Evidence and a Meta-Analysis | Psychol Sci 31:792-806 | [原文入口](https://doi.org/10.1177/0956797620916786) | 方法／meta（负结果） | 常用任务态 fMRI 指标重测信度低（多数 ICC < 0.5），提示「个体预测」受限；与静息态网络稳定性形成对照。 |
| (Pomponio et al., 2020, NeuroImage) | Pomponio R; Erus G; … Davatzikos C (2020). Harmonization of large MRI datasets for the analysis of brain imaging patterns throughout the lifespan | NeuroImage 208:116450 | [原文入口](https://doi.org/10.1016/j.neuroimage.2019.116450) | 方法（协调，neuroHarmonize/ComBat-GAM） | 在 ComBat 基础上引入非线性（GAM）协调，处理站点/厂商非线性效应；直接应对 ABCD 式厂商效应。 |
| (Yarkoni, 2020, Behav Brain Sci) | Yarkoni T (2020). The generalizability crisis | Behav Brain Sci 45 | [原文入口](https://doi.org/10.1017/s0140525x20001685) | 理论／负结果 | 指出心理学/神经科学普遍缺乏跨样本泛化验证；为「重复 ≠ 可预测个体」提供概念框架。 |
| (Marek et al., 2022, Nature) | Marek S; Tervo-Clemmens B; … Dosenbach NUF (2022). Reproducible brain-wide association studies require thousands of individuals | Nature 603(7902):654-660 | [原文入口](https://doi.org/10.1038/s41586-022-04492-9) | 原始分析（样本量门槛） | 三个数据集、合计约 5 万个体；脑—表型关联需数千量级才稳定；解释 ABCD 脑—行为关联效应量的背景。 |
| (Spisak et al., 2023, Nature) | Spisak T; Bingel U; Wager TD (2023). Multivariate BWAS can be replicable with moderate sample sizes | Nature 615(7951):E4-E7 | [原文入口](https://doi.org/10.1038/s41586-023-05745-x) | 竞争性解释（负/补充） | 对 Marek 等（2022）的回应：多元 BWAS 在中等样本即可复现；提示「需数千人」是单变量结论，非全貌。 |
| (Kang et al., 2024, Nature) | Kang K; Seidlitz S; … Vandekar SN (2024). Study design features increase replicability in brain-wide association studies | Nature 636:719-727 | [原文入口](https://doi.org/10.1038/s41586-024-08260-9) | 竞争性解释（补充） | 强调研究设计特征（而不仅是样本量）提升 BWAS 可重复性；与 Marek 等（2022）互补而非对立。 |
| (Parsons et al., 2024, Imaging Neurosci) | Parsons S; Brandmaier AM; Lindenberger U; Kievit RA (2024). Longitudinal stability of cortical grey matter measures varies across brain regions, imaging metrics, and testing sites in the ABCD study | Imaging Neurosci 2 | [原文入口](https://doi.org/10.1162/imag_a_00086) | ABCD 纵向/多站点 | ABCD 皮层灰质指标的纵向稳定性随脑区、指标与站点变化；为多站点测量提供纵向信度证据。 |
