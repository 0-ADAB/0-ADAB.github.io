---
publish: true
aliases:
  - Marr 三层次
  - 马尔三层次
  - Marr's three levels
  - 三层次分析
  - 层次分析框架
  - 计算层次与算法层次
  - 计算理论层
title: Marr三层次
description: 把信息处理系统区分为计算层次、表征与算法层次、实现层次的方法论框架，说明各层次回答什么问题、层次间约束如何传递，以及常见的层次混用与外推边界。
created: 2026-10-14T13:10:43.134Z
tags:
  - 类型/概念
  - 层/世界
---

# Marr三层次

> **一句话定义：** Marr 三层次（Marr's three levels of analysis）是把一个信息处理系统拆成三个**分析层次**来分别提问的方法论约定——计算层次（computational level）问系统在解决什么问题、为什么需要解决；表征与算法层次（representation and algorithm level）问用什么表征、按什么步骤完成该计算；实现层次（implementation level）问由何种物理过程把它做出来。它的价值在于把「做什么与为什么」「怎么做」「用什么做」分开，使不同研究路径各自可检验；它不是关于大脑结构的经验发现，也不能靠单次实验直接证实或否证。

## 快速理解

核心判断可以先用一句话概括：**三层次是三个提问位置，而不是三块组织层级，也不是三类证据强度的排序。**

对不熟悉该框架的读者，需要注意三点。

1. **它来自视觉研究，而不是来自一次实验。** 该表述最早由 Marr 与 Poggio（1976，MIT AI Memo 357）提出，并在 Marr 的专著《Vision》（1982，Vision）中定型。原始技术报告列出的其实是**四个**层次（计算的性质、算法、特定机制、硬件实现），成书后合并为三个，这一先后差异是文献中常见的引用混淆来源。
2. **它给出的是一条提问顺序，而不是对答案的保证。** Marr 主张先明确计算问题再讨论机制，理由是「不知道系统在做什么，就无法说明它怎么做」（Marr, 1982, Vision）。这条主张本身可被质疑：后续有论证认为计算层次的约束往往不足以支撑对算法层次的推导（Love, 2015, Top Cogn Sci）。
3. **它不产生单独的、可被否证的预测。** 框架的经验内容分散在各层次各自的具体模型上。因此评价「三层次是否正确」这一提问方式本身是有问题的；可检验的是某一层次的具体主张，例如某个神经元的响应是否可被某算法预测（Carandini et al., 2005, J Neurosci）。

## 概念界定与边界

### 三个层次各自规定什么

| 层次 | 中文与英文名称 | 回答的问题 | 典型研究对象 | 层次内产出 | 常见失误 |
| --- | --- | --- | --- | --- | --- |
| 计算层次 | 计算理论层（computational level） | 系统在解决什么问题，为什么需要解决这一问题 | 任务结构、环境约束、输入与输出之间的映射 | 问题的形式化、约束条件、最优性判据 | 约束不足，使模型成为事后叙事；把问题描述当作解释 |
| 表征与算法层次 | 算法层（representation and algorithm level） | 用什么表征、按什么步骤完成该计算 | 表征格式、算法、时间与存储代价 | 可执行的算法与可检验的预测 | 与实现层次界线模糊；把模拟结果的拟合当作机制证据 |
| 实现层次 | 硬件实现层（implementation level） | 由何种物理过程实现该算法 | 细胞、突触、电导、环路与网络动力学 | 生理机制与因果干预结果 | 由局部生理细节直接推断功能 |

### 必须区分的一组概念

**分析层次（levels of analysis）与组织层次（levels of organization）不是同一件事。** 前者指同一对象可以在不同抽象程度上被描述；后者指整体与部分之间的构成关系。有分析明确指出 Marr 讨论的是前者，因此他不涉及「高层属性如何由低层部件突现」这类问题（Bechtel & Shagrir, 2015, Top Cogn Sci）。这一区分对应的边界是：本页不讨论尺度层级（分子—细胞—环路—系统），也不讨论还原与突现的形而上学争议。

| 相邻术语 | 含义 | 与本页的关系 |
| --- | --- | --- |
| 机制性解释（mechanistic explanation） | 通过部件与部件操作说明现象如何产生 | 实现层次与算法层次常被纳入此类解释，但计算层次是否属于机制性解释存在分歧（Bechtel & Shagrir, 2015, Top Cogn Sci） |
| 多重可实现性（multiple realizability） | 同一功能可由不同物理结构实现 | 与「同一计算可由不同算法与硬件实现」直接相连，是框架的设定前提（Marr, 1982, Vision） |
| 层次错置（level confusion） | 把适用于某一层次的问题在其相邻层次上回答 | 该框架最主要的使用价值之一就是识别此类混淆（Marr & Poggio, 1976, MIT AI Memo 357） |
| 标准模型（standard model） | 某一加工阶段被广泛接受的定量模型 | 属算法层次的具体产物，与框架本身不同；早期视觉至今缺少公认标准模型（Carandini et al., 2005, J Neurosci） |

**不属于本页范围：** 某个具体脑区或环路的机制归属；某一建模方法的数学细节与实现代码；机器学习模型的工程性能评测。

### 框架内部的约束关系

Marr 并未主张三层次彼此完全独立。原文同时给出两条说明：计算的性质由待解决的问题决定，但**算法的选择取决于可用的机制**（Marr, 1982, Vision）。因此「三层次相互独立」是后世文献的一种简化归属，而非原始表述（Eliasmith & Kolbeck, 2015, Top Cogn Sci）。当前较一致的读法是：三者在提问上可分离，在约束上彼此传递。

## 结构与机制（适用时）

本页为概念节点，「结构」指该框架的内部组成与推演方式，而非神经结构。

**推演方向。** 从计算问题出发确定需要被求解的量，再寻找可在给定硬件上执行的算法，最后落实到具体机制；反向路径（由活动数据反推计算与算法）在同一框架下并不自动成立，需要额外论证。

**框架自身的构成要素。**

1. **提问位置**：三个层次分别对应「为什么与做什么」「怎么做」「用什么做」三类问题，跨层次混答会掩盖分歧。
2. **环境约束的引入位置**：计算层次的说明必须引用系统所处环境与任务，指出为什么需要该计算，因而不能在系统内部闭合（Bechtel & Shagrir, 2015, Top Cogn Sci）。
3. **可替换性设定**：同一计算允许存在多种算法与多种实现，同一实现也可承担不同计算；不满足该设定时，层次划分的实际作用会下降。
4. **层次数量的可塑性**：层次数并非固定值。除四层次（Marr & Poggio, 1976, MIT AI Memo 357）与三层次（Marr, 1982, Vision）外，还有在计算与算法之间增设中间层次（Griffiths et al., 2015, Top Cogn Sci）以及以算法层次为整合位置（Love, 2015, Top Cogn Sci）等处理方案。

**研究设计上的一条约束。** 若把框架落实为具体研究，各层次的主张需分别给出判据与检验方式：计算层次的主张涉及环境与任务的设定是否成立，算法层次的主张涉及对未参与拟合的数据或条件的预测能力，实现层次的主张涉及干预后效应的方向与特异性。三层混用会使「证据究竟支持哪一层」不可判定（Carandini, 2012, Nat Neurosci）。

## 关键研究与可重复性

本节按资料性质分层。需要先说明一点：**该框架本身是方法论主张，不存在「重复率」这类指标；可与可重复性概念对接的，是各层次的具体模型与实证结论。** 下文因此把原始研究、方法学评估与负向结果分开列出，不把哲学分析与实验证据并列。

### 框架来源与视觉中的原始应用

- Marr 与 Poggio（1976，MIT AI Memo 357）以傅里叶分析为例说明同一计算可由串行快速算法或光学并行算法完成，选择取决于可用硬件；这是「层次可分离但受约束」这一设定的原始论证来源。
- Marr（1976，Philos Trans R Soc B）给出早期视觉的可执行方案，提出「原始基元图（primal sketch）」并由强度变化词汇描述图像，是三层次在视觉中的首次系统化应用。
- Marr 与 Hildreth（1980，Proc R Soc B）以高斯—拉普拉斯算子（∇²G）的零交叉构造边界检测算法，并把结果与心理物理和生理数据对照，示范算法层次如何落到具体神经假设。
- Marr 与 Ullman（1981，Proc R Soc B）用零交叉处的时间导数约束局部运动方向，并提出 X／Y 细胞与皮层简单细胞的实现模型，是算法层次向实现层次推演的范例。
- Marr（1982，Vision）把上述工作整合为计算、表征与算法、实现三层，并明确「算法选择可能依赖硬件」这一限定。

### 层次关系的方法学与哲学检验

这些文献的证据性质是论证、文本分析与立场陈述，不是实验数据；引用时应按此定位。

- Bechtel 与 Shagrir（2015，Top Cogn Sci）论证三层次各有不可替代的说明作用，并澄清分析层次与组织层次之别。
- Peebles 与 Cooper（2015，Top Cogn Sci）指出框架发表三十年后仍被广泛采用，同时报告中间层次（表征与算法）持续被自下（还原论神经科学）与自上（贝叶斯计算层次）两条路径削弱或取消。
- Eliasmith 与 Kolbeck（2015，Top Cogn Sci）通过原文考察主张 Marr 意在反对还原论与含糊表述，而非主张层次独立。
- Love（2015，Top Cogn Sci）指出计算层次的约束不足，难以支撑自上而下的层次整合，主张以算法层次作为整合位置。
- Griffiths、Lieder 与 Goodman（2015，Top Cogn Sci）提出「资源理性分析（resource-rational analysis）」，在计算与算法之间定义中间层次，用计算成本约束连接两端。

### 算法层次预测能力的评估

- Carandini 等（2005，J Neurosci）系统评估早期视觉模型对任意刺激（含自然场景）的预测能力，结论是仅基于线性感受野的模型不足，必须纳入控制响应性的非线性机制；该文同时指出当时尚未形成各阶段公认的标准模型。这属于算法层次未完成的直接证据。

### 负向结果与方法学边界

- Jonas 与 Kording（2017，PLoS Comput Biol）在一个各层次结构完全已知的微处理器上套用常见神经科学分析流程，未能重建其信息处理层次。该结果提示：仅依靠数据驱动方法，即使数据充足，也可能不足以获得对层次结构的理解。其局限在于把处理器与脑做类比本身需要论证，且并未穷尽全部可用方法。
- Carandini（2012，Nat Neurosci）主张环路与行为之间的跨度过大，需要以「神经计算」作为中间层次，是对「实现层次可直接解释行为」的直接质疑。
- Krakauer 等（2017，Neuron）与 Niv（2021，Behav Neurosci）提出行为与任务分解应先于神经实现研究，理由是同一行为可由不同环路实现、同一活动模式也可参与不同行为；Gomez-Marin 等（2014，Nat Neurosci）从实验约束程度、数据维度与描述层次三个维度论证行为描述本身是独立的基础工作。上述三篇均为立场性文章。
- Brette（2019，Behav Brain Sci）论证「神经编码」表述依赖实验条件并预设了外部意义来源，认为以编码变量承载表征的做法受限；该文针对的是算法层次的表征假设，不是框架的层次划分本身。

### 建模实践中的重新表述

- Kriegeskorte 与 Douglas（2018，Nat Neurosci）主张以能执行任务的模型连接计算假设与神经数据，使计算层次的假设获得可检验形式。
- Saxe、Nelli 与 Summerfield（2021，Nat Rev Neurosci）讨论深度网络作为脑计算理论时需明确「所问问题对应哪一层次」，并指出行为、学习动态与神经表征三类比较各自的方法学要求。
- Doerig 等（2023，Nat Rev Neurosci）主张把「神经连接主义（neuroconnectionism）」作为表达可检验脑计算理论的语言，并按研究纲领的标准评估其进展，而非逐项判定个别网络成败。

## 当前较稳定的认识

1. **三层次是分析层次，不是组织层次，也不等同于尺度层级。** 这是文献中用法相对一致的要点，也是使用该框架时最常需要先澄清的一点（Bechtel & Shagrir, 2015, Top Cogn Sci）。
2. **计算层次的独立作用在于引入环境与任务约束，说明「为什么需要这个计算」。** 若只给出输入与输出的对应关系而不说明环境中的约束，该层次未发挥其独特功能（Bechtel & Shagrir, 2015, Top Cogn Sci）。
3. **层次之间存在约束传递，而非严格独立。** 原始文本明确说明算法选择可能取决于可用硬件，后续分析亦认为「层次独立」是对 Marr 立场的简化归属（Marr, 1982, Vision; Eliasmith & Kolbeck, 2015, Top Cogn Sci）。
4. **「同一计算可由不同算法与不同硬件实现」是框架的设定前提。** 该前提与多重可实现性直接相关，也是分层提问得以成立的条件（Marr & Poggio, 1976, MIT AI Memo 357; Marr, 1982, Vision）。
5. **中间层次长期处于争议中心。** 框架发表三十年后，表征与算法层次仍被两条相反路径削弱或取消，这与该框架以视觉为原型的背景有关（Peebles & Cooper, 2015, Top Cogn Sci）。
6. **层次数量没有唯一方案。** 已有四层次、三层次、在计算与算法之间增设中间层次、以算法层次为整合位置等多种处理，选择取决于研究对象与所接受的约束来源（Marr & Poggio, 1976, MIT AI Memo 357; Marr, 1982, Vision; Griffiths et al., 2015, Top Cogn Sci; Love, 2015, Top Cogn Sci）。
7. **框架不能替代各层次自身的经验研究。** 以早期视觉为例，算法层次至今没有公认的标准模型，说明框架的采用与算法层次问题的解决是两件事（Carandini et al., 2005, J Neurosci）。

## 争议与推断边界

**争议一：三层次是否彼此独立。** 通行归属认为 Marr 主张独立，但原文考察显示该主张与文本不符，且原文保留了层次间的依赖说明（Eliasmith & Kolbeck, 2015, Top Cogn Sci; Marr, 1982, Vision）。因此引用「Marr 认为三层次独立」时，应注明这是后世的简化表述。

**争议二：计算层次是否具备解释力与可检验性。** 一种立场认为计算层次引入环境约束，是不可替代的说明（Bechtel & Shagrir, 2015, Top Cogn Sci）；另一种立场认为该层约束不足，无法为层次整合提供可靠基础（Love, 2015, Top Cogn Sci）。两者针对的是同一问题的不同侧面：前者关注该层次能否提出恰当的问题，后者关注该层次能否导出算法。目前该分歧未被实验判定。

**争议三：层次是否需要增补或合并。** 有方案在其间增设中间层次（Griffiths et al., 2015, Top Cogn Sci），有方案以单一层次作为整合位置（Love, 2015, Top Cogn Sci），也有方案主张层次整合本身可行并通过大规模模型演示（Eliasmith & Kolbeck, 2015, Top Cogn Sci）。这些方案各自依据不同的研究对象，尚无统一结论。

**争议四：反向工程路径的有效性。** 在已知真值系统上的结果显示，通行的数据驱动分析未能重建信息处理层次（Jonas & Kording, 2017, PLoS Comput Biol）。该结论的外推边界需要标明：微处理器与脑在可干预性、退化性与可观测性上差异明显，作者本人也未穷尽现有方法，故该结果支持的是「方法需谨慎评估」而非「反向工程不可行」。

**争议五：行为研究与神经研究何者优先。** 行为优先论主张任务与行为的分解先于神经实现研究（Krakauer et al., 2017, Neuron; Niv, 2021, Behav Neurosci; Gomez-Marin et al., 2014, Nat Neurosci）。这些文献为立场性论证与案例归纳，不是对照实验；它们与「干预实验检验因果」并不互斥，其可检验部分在于行为分解能否对计算与机制模型施加额外约束。

**争议六：表征假设本身是否成立。** 对「神经编码」表述的批评指向算法层次的前提（Brette, 2019, Behav Brain Sci）。若表征假设不成立，该层次的表述方式需要重构；但该批评本身也存在反对意见，尚未取得共识。

**外推边界与资料性质限制。**

- **物种与系统边界**：框架起源于人类与动物的视觉研究，其计算层次的约束依赖具体任务与环境设定；迁移到认知、社会或临床应用时，可用的环境约束更弱，易退化为含糊表述——这正是 Marr 本人明确反对的情形（Eliasmith & Kolbeck, 2015, Top Cogn Sci）。
- **跨方法边界**：同一层次可对应多种测量方法，方法不同会改变该层次主张的可检验程度；以成像、电生理或行为方法各自得到的结果不构成同一层次内的独立重复（Carandini et al., 2005, J Neurosci; Carandini, 2012, Nat Neurosci）。
- **资料性质边界**：本页引用的主张中，仅有少数来自原始研究，多数为观点文章、专刊导言与哲学分析。二者不应并列作为同等强度的证据，其支持范围见「关键文献与资料」表末列。
- **未完成事项**：本页未判定三层次与后续「神经连接主义」方案之间的优劣，也未处理该框架在语言学、精神病学等领域的变体用法。

## 相关节点

- [[04_证据与推理轴/04_证据与推理轴|证据与推理轴]]：推断类型、推断边界与证据质量在总体框架中的位置。
- [[04_证据与推理轴/证据质量/可重复性|可重复性]]：框架本身不适用重复率判据，层次内各具体主张才需要分别检验。
- [[03_方法与模型轴/03_方法与模型轴|方法与模型轴]]：算法层次与实现层次各自依赖的测量与建模方法。
- [[02_研究对象与尺度轴/02_研究对象与尺度轴|研究对象与尺度轴]]：实现层次涉及的实体与尺度，需与分析层次区分。
- [[01_科学问题轴/01_科学问题轴|科学问题轴]]：计算层次最终要回答的科学问题。
- [[05_应用与转化轴/05_应用与转化轴|应用与转化轴]]：层次混用在临床与转化研究中的具体后果。

**同分类与相邻节点（已在库内但尚未发布，故此处以纯文本列出，不建立双链）**：机制与功能、机制性解释、描述与解释、还原与突现、多重可实现性、必要性与充分性、相关与因果、预测与解释、定位不等于功能解释、从相关到因果的边界、激活不等于编码、解码成功不等于机制得到证明、逆向推理的局限、相关脑区不等于必要脑区。

## 关键文献与资料

**编排说明：** 正文引注统一为「作者—年份—期刊简称」：括号引注写作 `(Author et al., Year, Journal)`，中文叙述引注写作「作者 等（Year，Journal）」。三位及以上作者用 `et al.`，两位作者用 `&`，单作者用单姓氏。下表按出版年升序排列（同年按第一作者姓氏字母序），「正文引用」列为对应的括号形式。本节点共 22 条资料，其中原始研究与技术报告 6 条、方法学评估与实证 2 条、综述与立场文章 9 条、哲学与框架分析 5 条；专著的「期刊／卷页」列按非期刊来源写法填写。书目信息经出版方页面、DOI 解析与 PubMed／Europe PMC 记录核对；本表不表示已逐篇复算原始数据。篇数不等于独立重复次数。

| 正文引用 | 作者、年份与论文题名 | 期刊／卷页 | DOI／永久入口 | 证据性质 | 主要支持及限制 |
| --- | --- | --- | --- | --- | --- |
| (Marr, 1976, Philos Trans R Soc B) | Marr D. (1976). Early processing of visual information. | Philos Trans R Soc B 275(942):483–519 | [原文入口](https://doi.org/10.1098/rstb.1976.0090) | 原始研究，早期视觉计算方案 | 提出原始基元图并给出可实现的早期视觉处理方案，是三层次在视觉中的早期应用实例；其算法细节在后续模型中被多次修订，不能作为框架本身的经验证据。 |
| (Marr & Poggio, 1976, MIT AI Memo) | Marr D; Poggio T. (1976). From understanding computation to understanding neural circuitry. | MIT Artificial Intelligence Laboratory（A.I. Memo 357） | [原文入口](https://dspace.mit.edu/handle/1721.1/5782) | 技术报告，框架原始表述 | 以傅里叶分析为例说明同一计算可由不同算法与硬件完成，主张各层次仅松散相关、还原论不等于构造论；该文列出的是四个层次，与 1982 年成书的三层次不同。 |
| (Marr, 1977, Artif Intell) | Marr D. (1977). Artificial intelligence—a personal view. | Artif Intell 9(1):37–48 | [原文入口](https://doi.org/10.1016/0004-3702\(77\)90013-3) | 观点文章，方法论 | 区分关注计算问题本身与关注实现机制的两类理论，为后续层次划分提供方法论前提；未给出层次的具体划分。 |
| (Marr & Hildreth, 1980, Proc R Soc B) | Marr D; Hildreth E. (1980). Theory of edge detection. | Proc R Soc B 207(1167):187–217 | [原文入口](https://doi.org/10.1098/rspb.1980.0020) | 原始研究，算法层次模型 | 以高斯—拉普拉斯算子的零交叉构造边界检测算法，并与心理物理及生理数据对照；属当时的算法层次主张，其生理对应为模型预测。 |
| (Marr & Ullman, 1981, Proc R Soc B) | Marr D; Ullman S. (1981). Directional selectivity and its use in early visual processing. | Proc R Soc B 211(1183):151–180 | [原文入口](https://doi.org/10.1098/rspb.1981.0001) | 原始研究，算法与机制桥接 | 用零交叉处时间导数约束局部运动方向，并提出 X／Y 细胞与简单细胞的实现模型；示范算法层次向实现层次的推演方式，具体生理对应仍属预测。 |
| (Marr, 1982, Vision) | Marr D. (1982). Vision: A Computational Investigation into the Human Representation and Processing of Visual Information. | W. H. Freeman（2010 年由 MIT Press 重印） | [原文入口](https://doi.org/10.7551/mitpress/9780262514620.001.0001) | 专著，框架定型 | 三层次的标准表述来源；同时说明算法选择可能依赖硬件，故「层次独立」的归属需回到原文语境判断。 |
| (Churchland & Sejnowski, 1992, The Computational Brain) | Churchland P S; Sejnowski T J. (1992). The Computational Brain. | MIT Press（Bradford Books） | [原文入口](https://doi.org/10.7551/mitpress/2010.001.0001) | 专著，计算神经科学纲领 | 主张以神经元群体模型连接计算概念与行为数据，把实现层次视为对计算假设的约束来源之一；反映框架在神经科学中的早期扩展用法。 |
| (Carandini et al., 2005, J Neurosci) | Carandini M; Demb J B; Mante V; Tolhurst D J; Dan Y; Olshausen B A; Gallant J L; Rust N C. (2005). Do we know what the early visual system does? | J Neurosci 25(46):10577–10597 | [原文入口](https://doi.org/10.1523/JNEUROSCI.3726-05.2005) | 综述，算法层次预测能力评估 | 指出仅基于线性感受野的模型无法预测自然刺激下的神经反应，需纳入非线性机制，且当时尚无公认标准模型；为算法层次未完成的直接证据。 |
| (Carandini, 2012, Nat Neurosci) | Carandini M. (2012). From circuits to behavior: a bridge too far? | Nat Neurosci 15(4):507–509 | [原文入口](https://doi.org/10.1038/nn.3043) | 观点文章，层次间鸿沟 | 主张环路与行为之间跨度过大，需以神经计算作为中间层次；是对「实现层次可直接解释行为」的明确质疑。 |
| (Gomez-Marin et al., 2014, Nat Neurosci) | Gomez-Marin A; Paton J J; Kampff A R; Costa R M; Mainen Z F. (2014). Big behavioral data: psychology, ethology and the foundations of neuroscience. | Nat Neurosci 17(11):1455–1462 | [原文入口](https://doi.org/10.1038/nn.3812) | 观点文章，行为层次 | 从实验约束程度、数据维度与描述层次三个维度讨论行为数据，主张行为描述本身是独立的基础工作；与「行为只是实现层次的读出」相对。 |
| (Bechtel & Shagrir, 2015, Top Cogn Sci) | Bechtel W; Shagrir O. (2015). The non-redundant contributions of Marr's three levels of analysis for explaining information-processing mechanisms. | Top Cogn Sci 7(2):312–322 | [原文入口](https://doi.org/10.1111/tops.12141) | 哲学分析，框架辩护 | 论证三层次各有不可替代的说明作用，并区分分析层次与组织层次；为「层次不可合并」的主要论据。 |
| (Eliasmith & Kolbeck, 2015, Top Cogn Sci) | Eliasmith C; Kolbeck C. (2015). Marr's attacks: On reductionism and vagueness. | Top Cogn Sci 7(2):323–335 | [原文入口](https://doi.org/10.1111/tops.12133) | 哲学分析，文本考察与建模案例 | 认为 Marr 意在同时反对还原论与含糊表述，而非主张层次独立，并以其大规模功能脑模型说明层次整合可行；对「层次独立」的通行归属提出异议。 |
| (Griffiths et al., 2015, Top Cogn Sci) | Griffiths T L; Lieder F; Goodman N D. (2015). Rational use of cognitive resources: Levels of analysis between the computational and the algorithmic. | Top Cogn Sci 7(2):217–229 | [原文入口](https://doi.org/10.1111/tops.12142) | 理论建议，层次桥接 | 提出资源理性分析，在计算与算法之间定义中间层次，以计算成本约束连接两端；说明三层次并非必然尺度分离，可进一步细分。 |
| (Love, 2015, Top Cogn Sci) | Love B C. (2015). The algorithmic level is the bridge between computation and brain. | Top Cogn Sci 7(2):230–242 | [原文入口](https://doi.org/10.1111/tops.12131) | 理论建议，层次整合 | 论证计算层次约束不足、难以支撑自上而下的层次整合，主张以算法层次为整合位置；是对「计算层次优先」的明确反对意见。 |
| (Peebles & Cooper, 2015, Top Cogn Sci) | Peebles D; Cooper R P. (2015). Thirty years after Marr's Vision: Levels of analysis in cognitive science. | Top Cogn Sci 7(2):187–190 | [原文入口](https://doi.org/10.1111/tops.12137) | 专刊导言，框架现状 | 记录框架三十年后仍被广泛采用，并指出中间层次持续被自下与自上两条路径削弱或取消；为「持久但有争议」的直接表述。 |
| (Jonas & Kording, 2017, PLoS Comput Biol) | Jonas E; Kording K P. (2017). Could a neuroscientist understand a microprocessor? | PLoS Comput Biol 13(1):e1005268 | [原文入口](https://doi.org/10.1371/journal.pcbi.1005268) | 方法学实证，已知真值系统 | 在结构完全已知的微处理器上套用常见神经科学分析流程，未能重建其信息处理层次；外推边界为处理器与脑在可干预性、退化性与可观测性上的差异，且未穷尽现有方法。 |
| (Krakauer et al., 2017, Neuron) | Krakauer J W; Ghazanfar A A; Gomez-Marin A; MacIver M A; Poeppel D. (2017). Neuroscience needs behavior: Correcting a reductionist bias. | Neuron 93(3):480–490 | [原文入口](https://doi.org/10.1016/j.neuron.2016.12.041) | 观点文章，方法论 | 主张先以行为与任务分解获得理解，再研究神经实现，理由是同一行为可由不同环路实现；属立场性论证，非对照实验。 |
| (Kriegeskorte & Douglas, 2018, Nat Neurosci) | Kriegeskorte N; Douglas P K. (2018). Cognitive computational neuroscience. | Nat Neurosci 21(9):1148–1160 | [原文入口](https://doi.org/10.1038/s41593-018-0210-5) | 综述，纲领性 | 主张以可执行任务的模型连接认知计算假设与神经数据，使计算层次假设获得可检验形式；代表框架在现代建模实践中的一种操作化方式。 |
| (Brette, 2019, Behav Brain Sci) | Brette R. (2019). Is coding a relevant metaphor for the brain? | Behav Brain Sci 42:e215 | [原文入口](https://doi.org/10.1017/S0140525X19000049) | 理论批评，含公开同行评议 | 论证神经编码表述隐含实验条件依赖与意义来源问题，认为以编码变量承载表征的做法受限；针对算法层次的表征假设，该批评本身亦有反对意见。 |
| (Niv, 2021, Behav Neurosci) | Niv Y. (2021). The primacy of behavioral research for understanding the brain. | Behav Neurosci 135(5):601–609 | [原文入口](https://doi.org/10.1037/bne0000471) | 观点文章，方法论 | 以多个实例论证行为实验在回答「脑在做什么」及对计算与机制模型施加约束方面常优于神经测量；属立场性论证。 |
| (Saxe et al., 2021, Nat Rev Neurosci) | Saxe A; Nelli S; Summerfield C. (2021). If deep learning is the answer, what is the question? | Nat Rev Neurosci 22(1):55–67 | [原文入口](https://doi.org/10.1038/s41583-020-00395-8) | 综述，方法论路线图 | 讨论深度网络作为脑计算理论时的比较对象与检验方式，强调需明确所问问题对应哪一层次；说明框架在深度学习方法下需重新界定对应关系。 |
| (Doerig et al., 2023, Nat Rev Neurosci) | Doerig A; Sommers R P; Seeliger K; Richards B; Ismael J; Lindsay G W; Kording K P; Konkle T; van Gerven M A J; Kriegeskorte N; Kietzmann T C. (2023). The neuroconnectionist research programme. | Nat Rev Neurosci 24(7):431–450 | [原文入口](https://doi.org/10.1038/s41583-023-00705-w) | 观点文章，研究纲领 | 主张把神经连接主义作为表达可检验脑计算理论的语言，并按研究纲领标准评估其进展；是近年对「计算层次应如何表述」的一种替代方案。 |
