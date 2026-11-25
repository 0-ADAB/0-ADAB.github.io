---
publish: true
aliases:
  - 时序依赖性突触可塑性
  - Spike-timing-dependent plasticity
  - 脉冲时间依赖性可塑性
title: STDP如何实现时序依赖可塑性
description: STDP 将突触前活动与突触后放电的相对时间转化为长期突触效能变化，但其方向取决于受体、局部树突信号、放电模式、发育状态和神经调质，并非唯一固定时间窗。
created: 2026-10-17T22:22:41.076+08:00
modified: 2026-11-14T12:41:03.119+08:00
tags:
  - 类型/科学问题
  - 层/世界
---

# STDP如何实现时序依赖可塑性

> **核心问题：** 突触前输入与突触后放电的先后顺序和时间间隔，如何经过局部电压、受体/钙信号及突触前后表达机制，转化为可持续的突触增强或减弱？这套规则何时表现为经典“前先后后→增强，后先前后→减弱”，何时失效、反转或改由第三种信号决定？

## 为什么重要？

神经元需要根据经验改变连接强度，但它无法仅靠“两个细胞都活跃”区分哪些输入可能参与促发了当前输出。**脉冲时间依赖性可塑性**（spike-timing-dependent plasticity, STDP）提供了一个可实验检验的解释：不仅看是否共同活跃，还&#x770B;_&#x54EA;个活动先到、相差多久，以及活动发生时突触所处的状态_。早期对海马和皮层成对活动的记录表明，稍稍改变配对顺序，就能使相同连接发生长期增强（LTP）或长期减弱（LTD），但规律具有输入和细胞类型依赖性 (Debanne et al., 1994, PNAS; Markram et al., 1997, Science; Bi & Poo, 1998, J Neurosci; Feldman, 2000, Neuron)。

从机制上，它把**时间关系**映射为**局部生化事件**：突触前谷氨酸释放与突触后树突去极化可能在 NMDA 受体等部位相遇，产生钙信号并驱动受体转运、释放概率或其他持久性改变。不过，在一些连接中 t-LTP 和 t-LTD 需要不同的巧合检测器；在另一些连接中，必须有多巴胺、乙酰胆碱或胶质细胞参与。因此，STDP 应被理解为**多种局部学习规则的家族**，而不是全脑共用的一条“因果关系计算器” (Dan & Poo, 2004, Neuron; Bender et al., 2006, J Neurosci; Seol et al., 2007, Neuron; Brzosko et al., 2019, Neuron; Andrade-Talavera et al., 2023, Mol Psychiatry)。

它的重要性在于提供了连接三类问题的桥梁：细胞怎样改写连接、脑回路怎样调整感觉表征、经验/奖励怎样在较长时间尺度上影响学习。计算模型说明 STDP _可&#x80FD;_&#x751F;成输入竞争与时间序列敏感性；在体实验也观察到时序配对引起的感受野变化，但“存在该机制”和“它是自然学习的普遍必要条件”应当严格区分 (Song et al., 2000, Nat Neurosci; Meliza & Dan, 2006, Neuron; Mu & Poo, 2006, Neuron; Vignoud et al., 2024, Commun Biol)。

## 问题范围与操作性定义

### 1. 核心变量与符号约定

- **突触前事件**：通常指突触前动作电位/轴突激活所导致的递质释放或被记录到的 EPSP 起始；二者有传导与突触延迟，记录时必须说明使用哪一个时标。
- **突触后事件**：通常指突触后胞体动作电位的峰或起始时刻；真正作用于突触的可能是反向传播动作电位（bAP）、局部树突尖峰、膜电位及钙瞬变。
- **时间差**：本节点固定使用 `Δt = t_post − t_pre`；`Δt > 0` 表示**前先、后后**，`Δt < 0` 表示**后先、前后**。不同论文可能采用相反符号，不能只抄曲线不核对定义。
- **被解释量**：诱导后相对基线的单位突触 EPSP/EPSC/IPSC（幅度、斜率或成功率等）变化，以及其维持时间；“当下放电更强”不等于测到了长期突触可塑性。
- **诱导协议**：配对次数、次数间频率、刺激强度、后神经元发放模式、温度、发育年龄、离体/在体、细胞类型、药理条件必须同时报告。

在一些经典培养海马突触中，前先后后、相隔几十毫秒以内往往偏向 LTP，反向顺序偏向 LTD；**这个时间尺度来自特定实验协议，不能无条件作为所有突触的固定阈值** (Bi & Poo, 1998, J Neurosci; Feldman, 2000, Neuron; Caporale & Dan, 2008, Annu Rev Neurosci)。

**示意性的经典成对学习窗，而非普适公式：**

\[
\Delta w =
\begin{cases}
A\_+ e^{-\Delta t/\tau\_+}, & \Delta t>0\\
-A\_- e^{\Delta t/\tau\_-}, & \Delta t<0
\end{cases}
]

这里 `Δw` 是突触权重变化，`A` 与 `τ` 是由具体实验或模型拟合的参数；`Δt = 0` 的归属以及饱和、频率、权重依赖性并不由该式规定。这个形式常用于网络计算，不表示神经元在分子水平逐字实现指数核；时序规则的复杂性已促使三脉冲、电压依赖和钙动力学等模型出现 (Song et al., 2000, Nat Neurosci; Pfister & Gerstner, 2006, J Neurosci; Clopath et al., 2010, Nat Neurosci; Graupner & Brunel, 2012, PNAS)。

### 2. 必须划清的五个概念边界

| 术语 | 与本问题的关系 | 不应混淆之处 |
| --- | --- | --- |
| Hebb 学习 | 活动相关的突触变化上位理论 | STDP 是其若干时间具体化形式之一，不必都遵循同一符号 |
| LTP / LTD | 观察到的持久增强与减弱现象 | 可以不通过 STDP 配对诱导；并不自动表明时序依赖 |
| t-LTP / t-LTD | 用时序配对协议诱导的增强/减弱 | 可能分别依赖不同受体、细胞位置及表达位点 |
| bAP 与局部树突尖峰 | 为突触后输入提供局部去极化/钙信号 | 胞体放电不是所有突触可塑性所必需或充分的事件 |
| 三因子/奖励调制学习 | 在局部活动外加入多巴胺等第三信号 | 不是每一篇 STDP 研究都证明了行为奖赏学习 |

对抑制性 GABA 突触，还需要另外界定“强度”：IPSC 幅度、氯离子平衡电位及抑制效能并不总能相互替换 (Woodin et al., 2003, Neuron; Haas et al., 2006, J Neurophysiol)。

## 主要假说与竞争性解释

### 假说一：NMDAR—bAP 时间巧合检测

**解释：** 突触前释放的谷氨酸与突触后去极化在同一个突触附近重叠，减轻 NMDAR 通道的电压依赖性镁阻塞，形成 Ca²⁺ 内流；不同的局部信号与后续激酶/磷酸酶过程可能导致 LTP 或 LTD。神经元动作电位的反向传播为这种时间重合提供了途径 (Markram et al., 1997, Science; Nishiyama et al., 2000, Nature; Shouval et al., 2002, PNAS)。

**预测：** 阻断 NMDAR、削弱相关树突去极化或改变配对时间会损害特定 t-LTP，改变钙来源或内部钙库则可能改变增强/减弱的方向。

**支持与反例：** 感觉皮层部分突触的 t-LTP 确实有 NMDAR 依赖；但同一连接的 t-LTD 可能改由 mGluR、钙内储、内源性大麻素及突触前 NMDAR 参与。胞体 bAP 不一定在远端足够强，也不构成所有细胞可塑性的必要/充分条件 (Sjöström et al., 2003, Neuron; Bender et al., 2006, J Neurosci; Sjöström & Häusser, 2006, Neuron; Lisman & Spruston, 2005, Nat Neurosci)。

### 假说二：钙信号的幅度、来源和时空结构决定可塑性极性

**解释：** 较强或较短的局部 Ca²⁺ 信号、较弱或较持久的信号可以偏向不同下游生化途径；但细胞内储钙、微区分布、受体耦合及信号动力学会影响最终规则。简单钙阈值是有用的模型，不是普适充分条件 (Nishiyama et al., 2000, Nature; Shouval et al., 2002, PNAS; Graupner & Brunel, 2012, PNAS)。

**支持与反例：** 阻断特定钙源可改变可塑性方向，然而树突棘测得的**体积平均钙瞬变**在不同配对条件下可能很接近，最终却分别发生 LTP/LTD；因此“钙峰越高就一定增强”过度简化了实验结论 (Nevian & Sakmann, 2006, J Neurosci; Bender et al., 2006, J Neurosci)。

### 假说三：局部树突非线性与输入协同性

**解释：** 同一胞体 spike 对近端和远端突触施加的局部电压可能不同；当多个输入协同、引发局部树突尖峰或改善 bAP 传播时，远端可由倾向 LTD 转为 LTP。因而“两个细胞的 spike 时间”未必等于“突触局部经历的有效时间差” (Sjöström et al., 2001, Neuron; Sjöström & Häusser, 2006, Neuron; Letzkus et al., 2006, J Neurosci)。

**预测：** 在相同胞体配对下，改变树突输入位置/协同性/局部去极化会移动学习窗；直接树突电压成像可以将该假说与纯胞体时间窗模型区分。

**限制：** 结果多来自具有特定树突形态的皮层锥体细胞；没有保证所有 interneuron 或轴突末梢可按同一方式计算。

### 假说四：固定两脉冲窗口不足，历史 spike 与速率同样重要

**解释：** 真实神经元有 burst、triplet 及复杂脉冲列；前面一次 spike 可改变后一次的 NMDAR 电流、局部去极化或抑制状态。成对窗口的**线性相加**未必可预测训练后的权重变化。三脉冲模型、电压规则和钙动力学模型试图解释这种非线性 (Sjöström et al., 2001, Neuron; Froemke & Dan, 2002, Nature; Pfister & Gerstner, 2006, J Neurosci; Clopath et al., 2010, Nat Neurosci; Graupner & Brunel, 2012, PNAS)。

**支持与反例：** 自然脉冲列实验以及 CA3–CA1 记录确实表明序列先史、配对频率和重复模式决定方向和幅度；但不同模型可以拟合同一个数据集，不说明其中任一就是唯一分子算法 (Froemke & Dan, 2002, Nature; Wittenberg & Wang, 2006, J Neurosci; Morrison et al., 2008, Biol Cybern)。

### 假说五：t-LTD、逆 Hebb 与抑制性突触需另有“专用”规则

**解释：** 某些新皮层 t-LTD 通过突触后内源性大麻素释放与突触前机制表达；某些纹状体规则可与经典时间符号相反；一些 GABA 突触的可塑性通过氯转运改变抑制效率而非谷氨酸受体插入/移除 (Sjöström et al., 2003, Neuron; Fino et al., 2005, J Neurosci; Woodin et al., 2003, Neuron; Haas et al., 2006, J Neurophysiol)。

**支持：** 在不同皮层连接和纹状体测到的可塑性符号/需要的通路不同；基于逆 Hebb 时序规则的模拟也能学到特定 spike 序列 (Pawlak & Kerr, 2008, J Neurosci; Vignoud et al., 2024, Commun Biol)。

**边界：** 逆 Hebb 的形式并非纹状体所有实验共同结论；更不能将模型里可学习序列直接写成自然行为学习已获因果证明。

### 假说六：发育、调质、胶质提供门控或第三因子

**解释：** 放电顺序本身只是诱发塑性的一个条件。发育状态可能决定连接使用 all-LTP 还是双向时间窗；神经调质受体激活改变 LTP/LTD 的可诱导性和极性；某些晚到的多巴胺信号可追溯性地改变此前配对所留下的“资格痕迹”；胶质细胞 d-丝氨酸等信号在特定 t-LTD 中也可必需 (Seol et al., 2007, Neuron; Itami & Kimura, 2012, J Neurosci; Brzosko et al., 2015, eLife; Andrade-Talavera et al., 2024, J Neurosci)。

**强有力的具体反例：** 2024 年运动皮层 VIP 中间神经元研究显示，VIP→Martinotti 与 VIP→篮状细胞之间的规则不一致，输入到 VIP 的兴奋性连接甚至可在两种 spike 顺序下都增强；2025 年发育早期邻近皮层柱水平连接也报道两种时序均可诱导 LTP，且两种 LTP 的 NMDAR 依赖不同。这些结果否定**固定的单一符号表**，但因样本、细胞类型和发育年龄有限，不能反过来宣称经典 STDP 不存在 (McFarlan et al., 2024, Front Cell Neurosci; Itami & Kimura, 2025, Cells)。

## 关键实验和研究设计

### 1. 从经典发现到后续检验的证据路径

| 研究问题 | 代表实验与设计 | 直接观察及可支持的推断 | 主要偏倚/必要对照 |
| --- | --- | --- | --- |
| 时序先后是否影响 LTP/LTD？ | 海马培养或成对皮层全细胞记录，系统改变 Δt (Debanne et al., 1994, PNAS; Markram et al., 1997, Science; Bi & Poo, 1998, J Neurosci; Feldman, 2000, Neuron) | 发现时序依赖的长时程权重变化 | 培养/切片状态、连接稳定性、初始权重、配对次数 |
| 其他动物/连接是否也有时间次序规则？ | 电鱼小脑样系统，以及皮层不同输入 (Bell et al., 1997, Nature; Feldman, 2000, Neuron) | 时间顺序效应不只存在于一种制备 | 类脑区与真皮层的同源性、协议定义差异 |
| 钙是否是统一信号？ | NMDAR 阻断、内部钙库干预、双光子树突棘 Ca²⁺ 成像 (Nishiyama et al., 2000, Nature; Nevian & Sakmann, 2006, J Neurosci) | 钙参与诱导，但平均峰值不能唯一预测方向 | 指示剂缓冲效应、微区钙与体平均差异 |
| LTD 和 LTP 的巧合检测器是否相同？ | mGluR/eCB/CB1、突触前 NMDAR 操纵及配对 (Sjöström et al., 2003, Neuron; Bender et al., 2006, J Neurosci) | 一些皮层 t-LTD 有独立于 t-LTP 的机制 | 药理选择性、pre/post 表达位点判定 |
| 复杂序列能否用两脉冲窗预测？ | 自然脉冲列、不同配对频率/数目 (Sjöström et al., 2001, Neuron; Froemke & Dan, 2002, Nature; Wittenberg & Wang, 2006, J Neurosci) | 频率、历史与协同性不可忽略 | 全细胞记录洗脱、阈值/饱和、输入招募 |
| 树突位置是否改变规则？ | 远/近端激活、树突局部去极化、bAP 传播测量 (Sjöström & Häusser, 2006, Neuron; Letzkus et al., 2006, J Neurosci) | 位置及树突协同性改变权重变化的符号 | 必须配对测局部而非仅胞体电位 |
| 抑制性与纹状体突触怎样不同？ | GABA IPSC/氯转运；纹状体配对与多巴胺阻断 (Woodin et al., 2003, Neuron; Haas et al., 2006, J Neurophysiol; Fino et al., 2005, J Neurosci; Pawlak & Kerr, 2008, J Neurosci) | 规则、极性、表达部位/门控条件多样 | 动力学与释放概率混杂、疾病/药物影响 |
| STDP 与在体感觉表征有多近？ | 在体视觉刺激配对单细胞脉冲；视顶盖移动刺激 (Meliza & Dan, 2006, Neuron; Mu & Poo, 2006, Neuron) | 特定感受野随时间配对出现预测性改变 | 感受野≠单个已定位突触；发育期特异 |
| 调质能否改变配对结果？ | 受体药理、嗅觉强化、树突棘成像和追溯性 DA (Seol et al., 2007, Neuron; Cassenaer & Laurent, 2012, Nature; Yagishita et al., 2014, Science; Brzosko et al., 2015, eLife) | 第三因素改变诱导方向、窗口及资格痕迹 | 调质有广泛兴奋性效应；昆虫到哺乳类不能一概外推 |
| 规则是否随发育与细胞类型而变？ | 关键期前后桶状皮层、VIP 连接与胶质信号干预 (Itami & Kimura, 2012, J Neurosci; McFarlan et al., 2024, Front Cell Neurosci; Andrade-Talavera et al., 2024, J Neurosci; Itami & Kimura, 2025, Cells) | all-LTP、双顺序 LTP、特定 t-LTD 机制各异 | 不能混淆发育阶段、突触几何、受体组合 |
| 为什么已有时间规则仍难保证记忆？ | 权重竞争、三脉冲/钙/电压/稳态模型 (Song et al., 2000, Nat Neurosci; Pfister & Gerstner, 2006, J Neurosci; Clopath et al., 2010, Nat Neurosci; Vogels et al., 2011, Science; Vignoud et al., 2024, Commun Biol) | 计算上可形成时间选择性、序列辨别或 E/I 平衡 | 预测是模型内部结果，不是体内已证实的学习算法 |

### 2. 实验操作应如何避免常见误判

1. **明确事件时间零点。** 预先规定 `Δt` 的正负方向；对突触前电刺激，校准传导延迟并报告 EPSP 实测起点，避免将电极刺激的时间当作递质到达时间。
2. **全面扫描窗口。** 不只测试一个“经典 +10 ms”和一个“经典 −10 ms”，还要覆盖间隔更远及零配对，报告是否出现无变化或 all-LTP；如此可比较单峰、双向与逆 Hebb 学习窗 (Bender et al., 2006, J Neurosci; Itami & Kimura, 2012, J Neurosci; Itami & Kimura, 2025, Cells)。
3. **在相同初始突触强度下比较。** 对照基线 EPSP/EPSC、短时程可塑性、串联电阻和未配对输入；原始强度本身可以影响诱导幅度 (Bi & Poo, 1998, J Neurosci)。
4. **同时拆开三类信号。** 测胞体/树突电压、局部棘 Ca²⁺、长期权重；同步操纵 NMDAR、钙内库、eCB 和 neuromodulator，记录是在诱导、表达还是维持阶段产生影响 (Nevian & Sakmann, 2006, J Neurosci; Bender et al., 2006, J Neurosci)。
5. **同一连接体系内更换放电形式。** 在重复两脉冲、三脉冲、burst 和自然脉冲列间交叉，用一部分数据拟合模型、用独立实验条件检验模型；避免简单以拟合曲线漂亮为“生物机制已确认” (Froemke & Dan, 2002, Nature; Pfister & Gerstner, 2006, J Neurosci; Graupner & Brunel, 2012, PNAS)。
6. **从切片走向在体需要附加证据。** 先验证配对能改变单细胞/单突触，再测试正常感觉或奖赏任务中同类型事件是否足够发生、必要的环路是否可被定向阻断，而不是将感受野变化直接等同全网络某个学习规则 (Meliza & Dan, 2006, Neuron; Mu & Poo, 2006, Neuron; Brzosko et al., 2019, Neuron)。

### 3. 可执行的“强假说对照”设计

在同一物种/连接类型中，对\*\*配对顺序（前后）× 频率（低/高）× 突触位置（近端/远端）× 调质状态（有/无）\*\*做可控交叉实验，同时记录神经元局部电压、Ca²⁺ 与长期权重变化，预注册三种模型的判别性预测：

- **纯 pair-STDP：** 固定相对时序最重要，其他变量仅改变增益；
- **钙/电压非线性模型：** 频率和树突条件可移动窗口甚至反转符号；
- **第三因子门控模型：** 相同局部电信号下，神经调质/胶质状态可阻止或重定向变化。

该实验方案是**根据既有文献提出的可检验设计建议**，不是已完成的统一多中心研究。

## 当前较稳妥的回答

**目前证据较强：**

- **相对发放时序可以影响许多突触的长期强度，但方向和时间窗并非普适。** 海马培养、皮层切片、视顶盖和其他回路都有支持观察；同时，不同连接确有不同/反转/仅增强规则 (Markram et al., 1997, Science; Bi & Poo, 1998, J Neurosci; Feldman, 2000, Neuron; Mu & Poo, 2006, Neuron; Itami & Kimura, 2012, J Neurosci; McFarlan et al., 2024, Front Cell Neurosci)。
- **局部电压、NMDA 与 Ca²⁺ 信号构成若干兴奋性 STDP 的重要诱导条件。** 但某些 t-LTD 还有其他巧合检测器，且钙平均幅度不足以唯一区分增强和减弱 (Nishiyama et al., 2000, Nature; Bender et al., 2006, J Neurosci; Nevian & Sakmann, 2006, J Neurosci)。
- **脉冲列结构、频率和树突距离是解释方向与幅度的关键变量。** 固定指数 pair 窗口是基准模型而不是普适的生理定律 (Sjöström et al., 2001, Neuron; Froemke & Dan, 2002, Nature; Wittenberg & Wang, 2006, J Neurosci; Sjöström & Häusser, 2006, Neuron; Feldman, 2012, Neuron)。
- **STDP 可受到神经调质、发育阶段与细胞类型的门控。** 这些条件会使同一配对顺序产生不同结果，甚至无法诱导可塑性 (Seol et al., 2007, Neuron; Pawlak & Kerr, 2008, J Neurosci; Itami & Kimura, 2012, J Neurosci; Brzosko et al., 2015, eLife; Andrade-Talavera et al., 2024, J Neurosci; Itami & Kimura, 2025, Cells)。

**较可靠但必须局限表述：** 时序配对可在体改变某些视觉或嗅觉回路活动，并在计算模型中产生权重竞争或序列学习；这支持 STDP 的功能意义，却不足以证明成人大脑所有自然学习均由固定 pair-STDP 实现 (Meliza & Dan, 2006, Neuron; Mu & Poo, 2006, Neuron; Cassenaer & Laurent, 2012, Nature; Song et al., 2000, Nat Neurosci; Vignoud et al., 2024, Commun Biol)。

**不应给出的强结论：** “前先后后必定 LTP”“反向必定 LTD”“钙峰值等于学习结果”“bAP 对所有突触塑性必要”“STDP 单独等于因果学习”“神经元存在统一毫秒学习窗”。

## 证据质量与可重复性

| 证据层次 | 跨研究汇合情况 | 反例、限制和审核要点 |
| --- | --- | --- |
| **经典配对窗口（细胞层）** | 多研究组、不同区域重复找到某种时序依赖 (Markram et al., 1997, Science; Bi & Poo, 1998, J Neurosci; Feldman, 2000, Neuron) | 不同连接、年龄、诱导次数得不同曲线；非严格同一协议的重复 |
| **钙和 NMDAR 机制** | 药理/遗传干预与钙成像相互支持局部信号作用 (Nishiyama et al., 2000, Nature; Bender et al., 2006, J Neurosci; Nevian & Sakmann, 2006, J Neurosci) | 阻断诱导不等于唯一巧合检测器；钙峰值不够解释极性 |
| **树突和自然 spike 列** | 成像/记录与模型总体一致 (Froemke & Dan, 2002, Nature; Sjöström & Häusser, 2006, Neuron; Letzkus et al., 2006, J Neurosci) | 不同模型可拟合不同子集；需要外部条件的前瞻预测 |
| **原始可塑性和网络行为关联** | 视皮层、视顶盖、听觉及昆虫嗅觉回路存在在体证据 (Meliza & Dan, 2006, Neuron; Mu & Poo, 2006, Neuron; Froemke et al., 2007, Nature; Cassenaer & Laurent, 2012, Nature) | 体内感受野或奖励反应与单一特定突触机制之间有推断距离 |
| **neuromodulator 第三因子** | 胆碱/肾上腺素、多巴胺在数种模型中可改变规则 (Seol et al., 2007, Neuron; Pawlak & Kerr, 2008, J Neurosci; Brzosko et al., 2015, eLife) | 不同多巴胺受体与细胞群作用不同；不保证所有动物相同 |
| **发育及细胞类型边界** | 2012、2024 和 2025 年不同实验背景均观察到非经典规则 (Itami & Kimura, 2012, J Neurosci; McFarlan et al., 2024, Front Cell Neurosci; Andrade-Talavera et al., 2024, J Neurosci; Itami & Kimura, 2025, Cells) | 这些是相互补充而非严格的同协议多中心重复；需特别核查细胞身份、龄期 |
| **计算模型** | pair、triplet、膜电压、钙和逆 Hebb 模型可解释多类现象 (Song et al., 2000, Nat Neurosci; Pfister & Gerstner, 2006, J Neurosci; Clopath et al., 2010, Nat Neurosci; Graupner & Brunel, 2012, PNAS; Vignoud et al., 2024, Commun Biol) | 可计算性/拟合优度≠神经生物学的必要条件，稳态机制仍需补充 |

**重要的负结果：** 近似相同的钙瞬变未必给出相同可塑性符号（反对简单钙阈值充分性）；发育早期或 VIP 某些连接可能在反向顺序下也增强；另一些 VIP 连接在相应协议下未观察到显著变化。这些不是“STDP 全面失效”，而是约束了“时间差如何被读出”的解释范围 (Nevian & Sakmann, 2006, J Neurosci; McFarlan et al., 2024, Front Cell Neurosci; Itami & Kimura, 2025, Cells)。

**不能据此声称完成了系统评价。** 目前是按机制和证据层级组织的研究型叙述节点，未进行完整的数据库检索登记、论文层面的偏倚量表评分或合并效应量分析；跨模型一致性不能转化为可重复百分比。2012 年蝗虫嗅觉 STDP 研究有一项正式图版勘误（[Nature corrigendum](https://doi.org/10.1038/nature11261)），本稿在表内提示，不把更正内容当作一项新的独立证据 (Cassenaer & Laurent, 2012, Nature)。

## 未解决问题

1. **真正的局部巧合检测器有哪些、怎样决定 t-LTP 或 t-LTD？** 在同一连接使用电压与钙联合成像、局部药理及下游蛋白活性报告器，分离“来源/时空动态/效应器”而不只比较胞体放电顺序 (Bender et al., 2006, J Neurosci; Nevian & Sakmann, 2006, J Neurosci; Andrade-Talavera et al., 2024, J Neurosci)。
2. **经典 STDP 与“全 LTP/逆 Hebb”规则的发育切换机制是什么？** 在关键期前后追踪相同投射类型、树突位置和受体表达，测试更换单一条件是否足以转换规则 (Itami & Kimura, 2012, J Neurosci; Itami & Kimura, 2025, Cells; McFarlan et al., 2024, Front Cell Neurosci)。
3. **在自然脉冲列中，应该用 pair、triplet、局部电压还是多时尺度资格痕迹预测改变？** 用独立在体脉冲数据预测未来突触权重，再进行针对性操纵 (Froemke & Dan, 2002, Nature; Pfister & Gerstner, 2006, J Neurosci; Clopath et al., 2010, Nat Neurosci; Graupner & Brunel, 2012, PNAS)。
4. **STDP 如何在持续活动中避免权重跑向饱和？** 比较稳态抑制性可塑性、突触缩放与局部竞争是否在生理时间尺度上共同工作，而不是仅靠模拟参数边界 (Song et al., 2000, Nat Neurosci; Clopath et al., 2010, Nat Neurosci; Vogels et al., 2011, Science)。
5. **局部毫秒配对如何连接数百毫秒至秒级的奖励反馈？** 同步测突触结构、生理和延时多巴胺，在自由行为中区分瞬间配对与追溯调质效应 (Yagishita et al., 2014, Science; Brzosko et al., 2015, eLife; Brzosko et al., 2019, Neuron)。
6. **现有在体结果能否证明特定 STDP 规则对真实学习具有因果必要性？** 需要保持基础放电和传递不变、仅选择性破坏突触时间规则，并检测行为学习和感受野可塑性 (Meliza & Dan, 2006, Neuron; Mu & Poo, 2006, Neuron; Cassenaer & Laurent, 2012, Nature)。
7. **抑制性和胶质细胞参与的可塑性该如何统一测量？** 需要并行记录 GABA 反转电位、释放概率、胶质 D-丝氨酸、胞体/树突电压，而非统一用 EPSP 幅度量化 (Woodin et al., 2003, Neuron; Haas et al., 2006, J Neurophysiol; Andrade-Talavera et al., 2024, J Neurosci)。
8. **何时应该放弃单一脑区学习规则，改用功能性回路模型？** 在相同动作序列或感觉输入上对比经典时序模型与纹状体逆 Hebb 模型的独立预测，避免因模型“能学会”就反推“真实脑正这样学” (Vignoud et al., 2024, Commun Biol; Morrison et al., 2008, Biol Cybern)。

## 相关节点

**已有文件名可见但尚未核实 Vault 落盘/发布状态：** AMPA受体、大脑如何选择动作、基底核如何参与动作选择与抑制。

**候选科学问题节点：** 为什么突触活动会形成长时程增强或减弱、学习中的奖励延迟如何影响突触更新、发育关键期如何重塑皮层连接、时序可塑性如何改变神经元群体编码。

**候选概念节点：** NMDA受体、树突棘、反向传播动作电位、CaMKII、内源性大麻素、长时程增强、长时程抑制、多巴胺、星形胶质细胞。

**候选方法与模型节点：** 配对全细胞膜片钳、双光子钙成像、STDP学习窗口、三脉冲STDP模型、电压依赖可塑性模型、钙阈值模型、闭环光遗传。

> 未提供完整 Vault 目录与实际发布清单，故一律使用普通文本候选；本稿没有创建未经证实存在性的 Obsidian Wikilink。

## 参考资料

正文采用 **(作者 et al., 年份, 期刊简称)** 或双作者姓氏格式；同一括号多条文献以分号分隔。文献表列出完整题名、卷页、DOI、资料性质及推断边界。资料核验以正式出版记录为准；**综述、模型、机制原始实验与在体研究不可在证据强度上直接混同**。

| 正文引用 | 作者、年份与完整论文题名 | 期刊卷页 | DOI／永久链接 | 资料性质 | 主要支持与限制 |
| --- | --- | --- | --- | --- | --- |
| (Debanne et al., 1994, PNAS) | Debanne D.; Gähwiler B. H.; Thompson S. M. (1994). _Asynchronous pre- and postsynaptic activity induces associative long-term depression in area CA1 of the rat hippocampus in vitro_ | PNAS 91(3):1148–1152 | [DOI](https://doi.org/10.1073/pnas.91.3.1148) | 原始实验／历史先驱 | 时序偏移可诱导 CA1 LTD；使用突触后去极化，不等同后来的标准双 spike STDP |
| (Bell et al., 1997, Nature) | Bell C. C.; Han V. Z.; Sugawara Y.; Grant K. (1997). _Synaptic plasticity in a cerebellum-like structure depends on temporal order_ | Nature 387:278–281 | [DOI](https://doi.org/10.1038/387278a0) | 原始实验／比较神经生物学 | 电鱼类小脑样结构体现顺序依赖；不是典型哺乳动物皮层双 spike 方案 |
| (Markram et al., 1997, Science) | Markram H.; Lübke J.; Frotscher M.; Sakmann B. (1997). _Regulation of synaptic efficacy by coincidence of postsynaptic APs and EPSPs_ | Science 275(5297):213–215 | [DOI](https://doi.org/10.1126/science.275.5297.213) | 原始实验／经典发现 | 成对皮层神经元的时序效应；不能直接外推所有突触 |
| (Bi & Poo, 1998, J Neurosci) | Bi G.-Q.; Poo M.-M. (1998). _Synaptic modifications in cultured hippocampal neurons: dependence on spike timing, synaptic strength, and postsynaptic cell type_ | J Neurosci 18(24):10464–10472 | [DOI](https://doi.org/10.1523/JNEUROSCI.18-24-10464.1998) | 原始实验／经典定量时间窗 | 培养海马神经元的经典非对称窗口及初始权重依赖；数十毫秒非通用常数 |
| (Feldman, 2000, Neuron) | Feldman D. E. (2000). _Timing-based LTP and LTD at vertical inputs to layer II/III pyramidal cells in rat barrel cortex_ | Neuron 27(1):45–56 | [DOI](https://doi.org/10.1016/S0896-6273\(00\)00008-8) | 原始实验／跨连接检验 | 桶状皮层不同输入的非对称时间窗；不等于天然体验的完全因果机制 |
| (Nishiyama et al., 2000, Nature) | Nishiyama M.; Hong K.; Mikoshiba K.; Poo M.-M.; Kato K. (2000). _Calcium stores regulate the polarity and input specificity of synaptic modification_ | Nature 408:584–588 | [DOI](https://doi.org/10.1038/35046067) | 原始实验／机制补充 | 细胞内钙库影响 LTP/LTD 方向与输入特异性；不只属于标准双 spike 诱导 |
| (Song et al., 2000, Nat Neurosci) | Song S.; Miller K. D.; Abbott L. F. (2000). _Competitive Hebbian learning through spike-timing-dependent synaptic plasticity_ | Nat Neurosci 3:919–926 | [DOI](https://doi.org/10.1038/78829) | 计算模型 | 显示简单 STDP 可在模型中形成权重竞争；不是生物网络已被证实按该算法学习 |
| (Sjöström et al., 2001, Neuron) | Sjöström P. J.; Turrigiano G. G.; Nelson S. B. (2001). _Rate, timing, and cooperativity jointly determine cortical synaptic plasticity_ | Neuron 32(6):1149–1164 | [DOI](https://doi.org/10.1016/S0896-6273\(01\)00542-6) | 原始实验＋定量建模 | 频率、时序和协同性共同决定可塑性；固定成对窗口不可通吃 |
| (Froemke & Dan, 2002, Nature) | Froemke R. C.; Dan Y. (2002). _Spike-timing-dependent synaptic modification induced by natural spike trains_ | Nature 416:433–438 | [DOI](https://doi.org/10.1038/416433a) | 原始实验／脉冲列 | 前序 spike 改变后续配对贡献；简单配对项相加可能失败 |
| (Shouval et al., 2002, PNAS) | Shouval H. Z.; Bear M. F.; Cooper L. N. (2002). _A unified model of NMDA receptor-dependent bidirectional synaptic plasticity_ | PNAS 99(16):10831–10836 | [DOI](https://doi.org/10.1073/pnas.152343099) | 理论模型／钙阈值 | 钙动力学能解释部分 LTP/LTD；未证明仅由平均钙幅度决定全部规则 |
| (Sjöström et al., 2003, Neuron) | Sjöström P. J.; Turrigiano G. G.; Nelson S. B. (2003). _Neocortical LTD via coincident activation of presynaptic NMDA and cannabinoid receptors_ | Neuron 39(4):641–654 | [DOI](https://doi.org/10.1016/S0896-6273\(03\)00476-8) | 原始实验／突触前 t-LTD | 内源性大麻素、突触前 NMDAR 参与特定皮层 t-LTD；未证明其他脑区相同 |
| (Woodin et al., 2003, Neuron) | Woodin M. A.; Ganguly K.; Poo M.-M. (2003). _Coincident pre- and postsynaptic activity modifies GABAergic synapses by postsynaptic changes in Cl− transporter activity_ | Neuron 39(5):807–820 | [DOI](https://doi.org/10.1016/S0896-6273\(03\)00507-5) | 原始实验／抑制性突触 | 抑制性突触可通过氯转运改变有效强度；不属于 AMPA EPSP 的简单 LTP/LTD |
| (Dan & Poo, 2004, Neuron) | Dan Y.; Poo M.-M. (2004). _Spike timing-dependent plasticity of neural circuits_ | Neuron 44(1):23–30 | [DOI](https://doi.org/10.1016/j.neuron.2004.09.007) | 综述／理论背景 | 梳理学习规则及网络推断；不能作为单项机制的独立重复 |
| (Fino et al., 2005, J Neurosci) | Fino E.; Glowinski J.; Venance L. (2005). _Bidirectional activity-dependent plasticity at corticostriatal synapses_ | J Neurosci 25(49):11279–11287 | [DOI](https://doi.org/10.1523/JNEUROSCI.4476-05.2005) | 原始实验／纹状体对照 | 皮层—纹状体配对可出现双向可塑性；规则依输入和记录条件 |
| (Lisman & Spruston, 2005, Nat Neurosci) | Lisman J.; Spruston N. (2005). _Postsynaptic depolarization requirements for LTP and LTD: a critique of spike timing-dependent plasticity_ | Nat Neurosci 8:839–841 | [DOI](https://doi.org/10.1038/nn0705-839) | 评论／争论 | 指出树突去极化及 bAP 非必需/非充分的可能性；属于批评性论证 |
| (Bender et al., 2006, J Neurosci) | Bender V. A.; Bender K. J.; Brasier D. J.; Feldman D. E. (2006). _Two coincidence detectors for spike timing-dependent plasticity in somatosensory cortex_ | J Neurosci 26(16):4166–4177 | [DOI](https://doi.org/10.1523/JNEUROSCI.0176-06.2006) | 原始实验／竞争机制 | 桶状皮层 LTP 和 LTD 依赖不同钙来源及巧合探测器；反对通用单检测器 |
| (Haas et al., 2006, J Neurophysiol) | Haas J. S.; Nowotny T.; Abarbanel H. D. I. (2006). _Spike-timing-dependent plasticity of inhibitory synapses in the entorhinal cortex_ | J Neurophysiol 96(6):3305–3313 | [DOI](https://doi.org/10.1152/jn.00551.2006) | 原始实验／抑制性回路 | 内嗅皮层抑制性连接呈自身的非对称时序规则；不适用兴奋性突触模板 |
| (Letzkus et al., 2006, J Neurosci) | Letzkus J. J.; Kampa B. M.; Stuart G. J. (2006). _Learning rules for spike timing-dependent plasticity depend on dendritic synapse location_ | J Neurosci 26(41):10420–10429 | [DOI](https://doi.org/10.1523/JNEUROSCI.2650-06.2006) | 原始实验／树突位置 | 局部位置及树突尖峰影响时间窗；不能用胞体时序替代局部电压 |
| (Meliza & Dan, 2006, Neuron) | Meliza C. D.; Dan Y. (2006). _Receptive-field modification in rat visual cortex induced by paired visual stimulation and single-cell spiking_ | Neuron 49(2):183–189 | [DOI](https://doi.org/10.1016/j.neuron.2005.12.009) | 在体单细胞配对实验 | 在体感受野变化与时序预期一致；感受野变化≠逐突触机制被完全定位 |
| (Mu & Poo, 2006, Neuron) | Mu Y.; Poo M.-M. (2006). _Spike timing-dependent LTP/LTD mediates visual experience-dependent plasticity in a developing retinotectal system_ | Neuron 50(1):115–125 | [DOI](https://doi.org/10.1016/j.neuron.2006.03.009) | 在体发育回路／机制干预 | 蝌蚪视觉体验配对及 BDNF/NO 操纵联系 STDP 与回路调整；物种和发育期特异 |
| (Nevian & Sakmann, 2006, J Neurosci) | Nevian T.; Sakmann B. (2006). _Spine Ca2+ signaling in spike-timing-dependent plasticity_ | J Neurosci 26(43):11001–11013 | [DOI](https://doi.org/10.1523/JNEUROSCI.1749-06.2006) | 原始实验／钙模型反例 | 总体树突棘钙瞬变幅度不足以唯一预测增益符号；需考虑空间/分子下游 |
| (Pfister & Gerstner, 2006, J Neurosci) | Pfister J.-P.; Gerstner W. (2006). _Triplets of spikes in a model of spike timing-dependent plasticity_ | J Neurosci 26(38):9673–9682 | [DOI](https://doi.org/10.1523/JNEUROSCI.1425-06.2006) | 计算模型／高阶 spike | 三脉冲模型可拟合复杂脉冲列和频率效应；不等于已识别唯一生物分子机制 |
| (Sjöström & Häusser, 2006, Neuron) | Sjöström P. J.; Häusser M. (2006). _A cooperative switch determines the sign of synaptic plasticity in distal dendrites of neocortical pyramidal neurons_ | Neuron 51(2):227–238 | [DOI](https://doi.org/10.1016/j.neuron.2006.06.017) | 原始实验／树突机制 | 远端树突 bAP 衰减及协同性可反转可塑性符号；依细胞形态与局部激活 |
| (Wittenberg & Wang, 2006, J Neurosci) | Wittenberg G. M.; Wang S. S.-H. (2006). _Malleability of spike-timing-dependent plasticity at the CA3–CA1 synapse_ | J Neurosci 26(24):6610–6617 | [DOI](https://doi.org/10.1523/JNEUROSCI.5388-05.2006) | 原始实验／规则反例 | CA3–CA1 诱导对频率、刺激结构显著敏感；不能仅用几毫秒顺序推断 |
| (Froemke et al., 2007, Nature) | Froemke R. C.; Merzenich M. M.; Schreiner C. E. (2007). _A synaptic memory trace for cortical receptive field plasticity_ | Nature 450:425–429 | [DOI](https://doi.org/10.1038/nature06289) | 在体突触记录／感觉可塑性 | 听觉皮层体验与调质配对形成输入特异变化；非经典单突触 STDP 充分性测试 |
| (Seol et al., 2007, Neuron) | Seol G. H.; Ziburkus J.; Huang S.; et al. (2007). _Neuromodulators control the polarity of spike-timing-dependent synaptic plasticity_ | Neuron 55(6):919–929 | [DOI](https://doi.org/10.1016/j.neuron.2007.08.013) | 原始实验／神经调质 | 胆碱能及肾上腺素能相关信号门控和反转可塑性；依皮层连接与受体状态 |
| (Caporale & Dan, 2008, Annu Rev Neurosci) | Caporale N.; Dan Y. (2008). _Spike timing–dependent plasticity: a Hebbian learning rule_ | Annu Rev Neurosci 31:25–46 | [DOI](https://doi.org/10.1146/annurev.neuro.31.060407.125639) | 学术综述 | 归纳兴奋/抑制、位置和动物证据；综述非独立实验 |
| (Morrison et al., 2008, Biol Cybern) | Morrison A.; Diesmann M.; Gerstner W. (2008). _Phenomenological models of synaptic plasticity based on spike timing_ | Biol Cybern 98:459–478 | [DOI](https://doi.org/10.1007/s00422-008-0233-1) | 方法综述／模型比较 | 比较表象模型与适用场景；不能凭模型拟合推断全部分子细节 |
| (Pawlak & Kerr, 2008, J Neurosci) | Pawlak V.; Kerr J. N. D. (2008). _Dopamine receptor activation is required for corticostriatal spike-timing-dependent plasticity_ | J Neurosci 28(10):2435–2446 | [DOI](https://doi.org/10.1523/JNEUROSCI.4402-07.2008) | 原始实验／多巴胺门控 | 纹状体某协议的 STDP 需要多巴胺受体活性；不能推广所有纹状体条件 |
| (Clopath et al., 2010, Nat Neurosci) | Clopath C.; Büsing L.; Vasilaki E.; Gerstner W. (2010). _Connectivity reflects coding: a model of voltage-based STDP with homeostasis_ | Nat Neurosci 13:344–352 | [DOI](https://doi.org/10.1038/nn.2479) | 计算模型／电压＋稳态 | 用膜电压及稳态项拟合非线性学习规则；回路结果为模型预测 |
| (Vogels et al., 2011, Science) | Vogels T. P.; Sprekeler H.; Zenke F.; Clopath C.; Gerstner W. (2011). _Inhibitory plasticity balances excitation and inhibition in sensory pathways and memory networks_ | Science 334(6062):1569–1573 | [DOI](https://doi.org/10.1126/science.1211095) | 计算模型／抑制性可塑性 | 模型显示抑制性局部可塑性调节 E/I 平衡；不是直接的动物实验重复 |
| (Cassenaer & Laurent, 2012, Nature) | Cassenaer S.; Laurent G. (2012). _Conditional modulation of spike-timing-dependent plasticity for olfactory learning_ | Nature 482:47–52 | [DOI](https://doi.org/10.1038/nature10776) | 在体原始研究／昆虫强化学习 | 蝗虫蘑菇体调质信号调整 STDP；2012 年图版更正 DOI:10.1038/nature11261，不能外推哺乳类行为 |
| (Feldman, 2012, Neuron) | Feldman D. E. (2012). _The spike-timing dependence of plasticity_ | Neuron 75(4):556–571 | [DOI](https://doi.org/10.1016/j.neuron.2012.08.001) | 领域综述／证据边界 | 强调时序只是可塑性决定因素之一、在体外推仍有限 |
| (Graupner & Brunel, 2012, PNAS) | Graupner M.; Brunel N. (2012). _Calcium-based plasticity model explains sensitivity of synaptic changes to spike pattern, rate, and dendritic location_ | PNAS 109(10):3991–3996 | [DOI](https://doi.org/10.1073/pnas.1109359109) | 计算模型／钙动力学 | 拟合不同频率、时序与树突位置；模型解释不等于钙平均值充分 |
| (Itami & Kimura, 2012, J Neurosci) | Itami C.; Kimura F. (2012). _Developmental switch in spike timing-dependent plasticity at layers 4–2/3 in the rodent barrel cortex_ | J Neurosci 32(43):15000–15011 | [DOI](https://doi.org/10.1523/JNEUROSCI.2506-12.2012) | 原始实验／发育反例 | 关键期前更偏向无论顺序皆 LTP、随后改变；受龄期和连接影响 |
| (Yagishita et al., 2014, Science) | Yagishita S.; Hayashi-Takagi A.; Ellis-Davies G. C. R.; et al. (2014). _A critical time window for dopamine actions on the structural plasticity of dendritic spines_ | Science 345(6204):1616–1620 | [DOI](https://doi.org/10.1126/science.1255514) | 原始实验／突触棘结构可塑性 | 多巴胺时窗调控结构变化；与标准电生理 STDP 有联系但不是同一指标 |
| (Brzosko et al., 2015, eLife) | Brzosko Z.; Schultz W.; Paulsen O. (2015). _Retroactive modulation of spike timing-dependent plasticity by dopamine_ | eLife 4:e09685 | [DOI](https://doi.org/10.7554/eLife.09685) | 原始实验／追溯性调制 | 多巴胺可改变先前配对留下的可塑性趋势；离体模型不等同完整学习行为 |
| (Brzosko et al., 2019, Neuron) | Brzosko Z.; Mierau S. B.; Paulsen O. (2019). _Neuromodulation of spike-timing-dependent plasticity: past, present, and future_ | Neuron 103(4):563–581 | [DOI](https://doi.org/10.1016/j.neuron.2019.05.041) | 领域综述／跨时间尺度 | 归纳调质把毫秒配对与奖励延时连接的证据；非独立实证 |
| (Andrade-Talavera et al., 2023, Mol Psychiatry) | Andrade-Talavera Y.; Fisahn A.; Rodríguez-Moreno A. (2023). _Timing to be precise? An overview of spike timing-dependent plasticity, brain rhythmicity, and glial cells interplay within neuronal circuits_ | Mol Psychiatry 28:2177–2188 | [DOI](https://doi.org/10.1038/s41380-023-02027-w) | 综述／胶质细胞与生理边界 | 提出多细胞网络和胶质调节框架；各子机制共识程度不同 |
| (Andrade-Talavera et al., 2024, J Neurosci) | Andrade-Talavera Y.; Sánchez-Gómez J.; Coatl-Cuaya H.; Rodríguez-Moreno A. (2024). _Developmental spike timing-dependent long-term depression requires astrocyte d-serine at L2/3–L2/3 synapses of the mouse somatosensory cortex_ | J Neurosci 44(48):e0805242024 | [DOI](https://doi.org/10.1523/JNEUROSCI.0805-24.2024) | 原始实验／胶质参与 LTD | 未成年小鼠 S1 特定连接 t-LTD 依赖胶质 d-丝氨酸等信号；不可统一扩展到 STDP 全部规则 |
| (McFarlan et al., 2024, Front Cell Neurosci) | McFarlan A. R.; Guo C.; Gomez I.; et al. (2024). _The spike-timing-dependent plasticity of VIP interneurons in motor cortex_ | Front Cell Neurosci 18:1389094 | [DOI](https://doi.org/10.3389/fncel.2024.1389094) | 原始实验／细胞类型特异性 | VIP→MC 可 LTD、VIP→BC 未检出效应、E→VIP 可双顺序 LTP；不是统一抑制性 STDP |
| (Vignoud et al., 2024, Commun Biol) | Vignoud G.; Venance L.; Touboul J. D. (2024). _Anti-Hebbian plasticity drives sequence learning in striatum_ | Commun Biol 7:555 | [DOI](https://doi.org/10.1038/s42003-024-06203-8) | 计算模型／逆 Hebb 规则 | 在模拟纹状体中逆 Hebb 规则可支持序列识别；没有直接证明体内行为通过该规则学得 |
| (Itami & Kimura, 2025, Cells) | Itami C.; Kimura F. (2025). _Spike timing-dependent plasticity at layer 2/3 horizontal connections between neighboring columns during synapse formation before the critical period in the developing barrel cortex_ | Cells 14(18):1459 | [DOI](https://doi.org/10.3390/cells14181459) | 原始实验／2025 发育阶段例外 | 早期邻柱水平连接两种顺序可 all-LTP；分别有不同 NMDAR 依赖，单研究需独立复验 |

### 科研编辑与人工审核说明

- **来源性质：** 以经典原始论文、机制检验、不同脑区/物种验证、数学模型、领域综述和新近原始研究构成分层证据链。本稿不是全面数据库系统检索，也未量化总体重复成功率。
- **特别核验：** 读者应优先复查每篇研究的 `Δt` 正负定义、配对频率/次数、突触类型、发育年龄，以及 LTP/LTD 究竟发生在突触前还是突触后。
- **需跟踪的正式勘误：** Cassenaer & Laurent (2012, Nature) 后续更正了图 2f 的部分重复面板，DOI：[10.1038/nature11261](https://doi.org/10.1038/nature11261)；本文仍引用原研究并明确这一事项。
- **分类差异：** 用户消息注明“01\_科学问题轴/运动与行动”，但当前上传模板的 `category: 突触传递与可塑性`。为遵守输入模板及主题语义，本稿保留后者；如需在“运动与行动”设交叉入口，应另由人工确认，不在这里擅自移动主文件。
- **待人工验收：** 查重 STDP 的中文同义节点，校对新近 2024–2025 年论文的外推与后续独立验证、确认确实存在且拟公开的关联节点后再补双链。
- **发布安全：** 初稿 `publish: false`、`review_status: needs_review`；未更改 Obsidian Vault、五轴主页、首页索引或发布配置。
