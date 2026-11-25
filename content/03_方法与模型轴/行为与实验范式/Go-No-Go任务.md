---
publish: true
aliases:
  - Go/No-Go task
  - Go-No-Go task
  - Go/NoGo
  - go/no-go 任务
  - Go/Nogo 任务
  - 去/不去任务
title: Go-No-Go任务
description: 让被试对多数刺激快速按键、对少数刺激不按键的行为范式，用虚报率与反应时衡量在优势反应背景下按信号撤回准备动作的表现；其数值只在该任务参数下成立，不等于可直接读出的抑制能力。
created: 2026-10-14T21:10:43.039+08:00
modified: 2026-11-14T12:41:03.345+08:00
tags:
  - 类型/方法
  - 层/观测
---

# Go-No-Go任务

> **一句话介绍：** 在同一个试次序列中，让被试对占多数的一类刺激尽快按键（Go）、对占少数的一类刺激不按键（No-go），再用「对 No-go 刺激的虚报率」与「Go 试次的反应时」推断：当按键倾向已被建立时，他能否按刺激的含义撤回一个已准备的动作。

## 快速理解

**任务要制造的不是「辨别」，而是「倾向」。** 如果两类刺激等概率、试次节奏又慢，被试没有理由形成按键习惯，No-go 试次只考验能否分辨刺激，不考验能否压住反应。在四组参数不同的变体中比较，只有「节奏快、No-go 稀少」的版本可靠地诱发出优势运动活动（以偏侧化准备电位 LRP 为指标）；慢节奏、等概率版本中与抑制相关的活动比前者低约 75%(Wessel, 2018, Psychophysiology)。作者同时调查了文献使用情况：约 40% 的研究采用等概率的 Go/No-Go，约 20% 采用长于 4 s 的刺激—刺激间隔。

**一次试次要报的四个参数。** ① Go 与 No-go 的比例；② 刺激—刺激间隔；③ 反应时限；④ 总试次数与 No-go 试次数。这四项决定了「有没有优势反应」以及「有没有足够的 No-go 试次支持稳定估计」，而不是无关的技术细节：同一批被试在不同工作记忆负荷的版本中，No-go 相关激活的位置就发生变化(Mostofsky et al., 2003, Cogn Brain Res; Simmonds et al., 2008, Neuropsychologia)。

**读出什么。** 常用终点有四类：No-go 试次上的虚报（commission error，即不该按键时按了）、Go 试次上的漏报（omission error）、Go 试次的平均反应时与变异，以及按信号检测论换算的辨别力 d′ 与反应偏向 c。后两者把「分不清两类刺激」与「倾向于按键」分开，是报告虚报率时应当同时给出的量(Stanislaw & Todorov, 1999, Behav Res Methods Instrum Comput)。

**它与 stop-signal 任务的关键差别。** Go/No-Go 的 No-go 信号与 Go 信号同时出现，没有「延迟出现的停止信号」，因此无法用独立竞赛模型把抑制过程潜伏期反推出来；能给出抑制潜伏期估计的是 stop-signal 范式(Logan & Cowan, 1984, Psychol Rev; Verbruggen & Logan, 2008, Trends Cogn Sci)。把 Go/No-Go 的虚报率当作「抑制速度」的代理，是把两个不同设计的观测量混为一谈。

**名称在文献中指向两种东西。** 同名的「Go/No-Go 联想任务」（GNAT）用按键／不按键的结构测量内隐联想强度，其参数、指标与解释都与反应抑制范式无关(Nosek & Banaji, 2001, Soc Cogn)。检索与引用时必须区分，否则会把两个不相干的构念并入同一条证据链。

**历史位置。** 视觉 Go/No-Go 的直接前身是持续作业测验（CPT）：要求被试对高频目标作出反应、对其它刺激不反应，最初用于评估脑损伤(Rosvold et al., 1956, J Consult Psychol)。把它推到极端的是持续注意反应任务（SART）：Go 刺激极多、No-go 极少，作者把失败解释为注意脱离而非抑制失败(Robertson et al., 1997, Neuropsychologia)。这一改动说明同一装置可以测量不同构念，取决于参数与解释框架。

## 原理与操作流程

**1. 刺激—反应映射。** 每个试次呈现一个视觉刺激，被试按预先约定的映射按键或保持不动。映射可以固定（例如绿色按键、红色不按键），也可以随情境更新（例如「红色是否需要按键取决于其前面绿色刺激的个数」，属高工作记忆负荷版本）。前者主要调用刺激—反应的直接联结，后者额外调用工作记忆维持与更新，两者的 No-go 激活并不一致(Mostofsky et al., 2003, Cogn Brain Res)。因此「Go/No-Go 任务」不是一个单一范式，报告时必须写明映射规则是否随情境变化。

**2. 参数设置。** 常规做法是 Go 比例高于 No-go（如 4:1 或 5:1）、刺激—刺激间隔在 1–2 s 量级、对 Go 反应设时限。三项参数共同决定优势反应能否建立：把 No-go 概率从 25% 提高到 50% 会同时改变刺激概率结构与冲突程度(Eimer, 1993, Biol Psychol)，而在慢节奏、等概率的设计中，优势运动活动本身难以被诱发(Wessel, 2018, Psychophysiology)。

**3. 优势反应是否真的建立，需要独立检验。** 行为层面的证据是 Go 反应时低于对照条件、且 No-go 前的准备电位出现偏侧化。以 LRP 为指标可以逐试次判断 No-go 试次是否先出现了准备性运动活动；没有这一步，「No-go 试次测到了抑制」只是设计者的一句话(Wessel, 2018, Psychophysiology)。

**4. 计分。** 基本指标是对 No-go 刺激的按键率。由于该比率受反应偏向强烈影响，需要同时报告 d′ 与 c；当虚报率接近 0 时，比率本身缺乏变异，地板效应会掩盖真实差异(Stanislaw & Todorov, 1999, Behav Res Methods Instrum Comput)。反应时侧应报告 Go 试次的均值与变异，No-go 试次若出现按键，则该试次的反应时反映的是抑制失败的时刻，不能与 Go 反应时合并。

**5. 变体谱系。** ① 简单固定映射，No-go 刺激始终同一(Mostofsky et al., 2003, Cogn Brain Res)；② 情境依赖映射，需在工作记忆中维持并更新「是否按键」的规则(Mostofsky et al., 2003, Cogn Brain Res)；③ SART：高 Go 比例、固定序列、以注意脱离为主要解释(Robertson et al., 1997, Neuropsychologia)；④ 提示—靶（cued）版本，把准备阶段与执行阶段分开；⑤ 学习版本：把「做／不做」当作两个可选动作，与奖赏或惩罚结果正交化，用于分离效价与动作效应(Guitart-Masip et al., 2012, NeuroImage)。第 ⑤ 类严格说测的是动作—结果学习，不是反应抑制。

**6. 同步测量。** 电生理层面，No-go 试次在刺激后约 260 ms 起出现下前额区效应，300–600 ms 出现左偏侧额中央效应，源分析指向前扣带与左前运动区(Kiefer et al., 1998, NeuroReport)；在只用 Go 与 No-go 两类的版本中，N2 仅见于 No-go、源定位指向右侧外侧眶额与扣带，No-go 的 P3 波幅更大、潜伏期更长且更靠前(Bokura et al., 2001, Clin Neurophysiol)。影像层面，早期 PET 与事件相关 fMRI 已报告 No-go 相对 Go 的额叶差异(Kawashima et al., 1996, Brain Res; Garavan et al., 1999, Proc Natl Acad Sci U S A)。因果层面，用经颅磁刺激暂时失活右侧额下回岛盖部，会选择性损害「停止已启动动作」的能力，而不影响反应执行与生理唤醒(Chambers et al., 2006, J Cogn Neurosci)。

## 能回答什么，不能回答什么？

**可以直接回答的。** ① 在明确参数下，被试对 No-go 信号的按键率与 Go 反应时；② 两组被试（如临床组与对照组）在同一参数下的差异方向与效应量；③ 与 EEG／fMRI 同步时，No-go 与 Go 条件之间的信号差异；④ 在同一被试内操纵参数（比例、时限、映射复杂度）后表现如何随之改变(Benikos et al., 2013, Int J Psychophysiol; Mostofsky et al., 2003, Cogn Brain Res)。

**不能回答的，第一条是「抑制速度」。** 由于 No-go 信号与 Go 信号同时呈现，任务中不存在可用来推算「停止过程完成时刻」的延迟，独立竞赛模型的反推方法在此不适用(Logan & Cowan, 1984, Psychol Rev; Verbruggen & Logan, 2009, Neurosci Biobehav Rev)。要量化抑制潜伏期，须改用 stop-signal 设计并遵循其报告规范(Verbruggen et al., 2019, eLife)。

**第二条是「N2 就是抑制」。** 这条推断已被两类证据削弱。其一，在不需要抑制但冲突高的条件下同样出现 N2，且 N2 随 Go 频率升高而增大，说明它更符合冲突监测(Nieuwenhuis et al., 2003, Cogn Affect Behav Neurosci; Donkers & van Boxtel, 2004, Brain Cogn)；冲突监测本身有独立的理论框架(Botvinick et al., 2001, Psychol Rev)。其二，N2 的 No-go 效应在听觉模态下极小，这一反例由提出抑制解释的作者自己报告(Falkenstein et al., 1999, Acta Psychol)。较新的综述把额中线 N200／theta 归入冲突监测或反应程序更新，把前部 P300／delta 归入反应相关的评价阶段，两者都不是「抑制强度」的直接读数(Huster et al., 2013, Int J Psychophysiol)。

**第三条是「No-go 激活的脑区就是抑制中枢」。** 这条定位最初来自影像与病变证据的整合，曾把反应抑制集中到右侧额下皮层(Aron et al., 2004, Trends Cogn Sci)；但把简单刺激与复杂刺激的 Go/No-Go 分开做激活似然估计元分析后，多数 No-go 激活（含前辅助运动区）由注意或工作记忆负荷驱动，而不是抑制过程本身(Criaud & Boulinguez, 2013, Neurosci Biobehav Rev)。在保持刺激条件、只改变抑制要求时，右侧额下回的抑制特异反应明显减弱，提示它更多参与显著或任务相关线索的检测(Hampshire et al., 2010, NeuroImage)；把注意捕获从抑制中剥离后，右侧额下回更多归入腹侧注意系统(Sharp et al., 2010, Proc Natl Acad Sci U S A)；在下级皮层亚区层面，对「抑制需求」也没有功能唯一性，激活最强的情形是处理低频刺激，与是否需要抑制无关(Erika-Florence et al., 2014, Nat Commun)。另一种解释把 No-go 之后普遍出现的反应变慢归为一次全局的运动抑制(Wessel & Aron, 2017, Neuron)，这同样不要求把某个额叶区域指定为抑制中枢。

**第四条是「虚报率可以当诊断指标或冲动性指标」。** 把抑制效率与冲动性挂钩的做法有较早的实证来源(Logan et al., 1997, Psychol Sci)，对 318 项研究、11 类精神障碍的元分析给出：Go/No-Go 类任务的虚报错误效应量从焦虑障碍的 g = −0.10 到双相障碍的 g = 0.52，作者的结论是单独使用时的敏感性与特异性都不足以充当诊断指标或生物标志物(Wright et al., 2014, J Abnorm Psychol)。与自评问卷的汇聚效度也有限：把执行功能任务、延迟满足与自评／他评量表放在一起，总体收敛仅 r ≈ 0.27，其中执行功能任务最弱(Duckworth & Kern, 2011, J Res Pers)。

**第五条是「可以稳定测量个体差异」。** 任务效应稳健与个体差异信度高在统计上互相牵制：组间变异小才会让实验效应稳定，而组间变异小恰好使个体差异的信度降低(Hedge et al., 2018, Behav Res Methods)。实测中，冲动性行动类任务（含 Go/No-Go）的重测相关约 0.65–0.73(Weafer et al., 2013, Exp Clin Psychopharmacol)，而大规模重测显示自评量表信度高、行为任务导出的指标普遍偏低(Enkavi et al., 2019, Proc Natl Acad Sci U S A)。做相关研究前应先在自己的样本里估计信度。

## 空间、时间尺度与适用对象

**时间尺度。** 单试次通常 0.5–4 s，取决于刺激—刺激间隔与反应时限；一个可用的数据集一般在 100–400 试次、10–30 min。电生理成分在毫秒级：No-go 相关效应自刺激后约 260 ms 起出现，P3 类成分在 300–600 ms(Kiefer et al., 1998, NeuroReport)。功能影像的采样在秒级，因此事件相关设计必须靠试次抖动与短刺激间隔来提高时间分辨(Garavan et al., 1999, Proc Natl Acad Sci U S A)。

**空间尺度。** 行为指标本身不含空间信息。头皮电位经源分析可给到厘米级的粗略定位，且逆问题不唯一(Bokura et al., 2001, Clin Neurophysiol)；功能磁共振给到毫米级但依赖对照条件的差减是否成立(Rubia et al., 2003, NeuroImage)；经颅磁刺激的空间精度在厘米量级，且作用范围随线圈与强度变化(Chambers et al., 2006, J Cogn Neurosci)。

**适用对象。** 人类成人是主要对象；儿童与临床人群同样可用，但需注意任务时长与阅读／颜色命名等前置能力(Casey et al., 1997, J Am Acad Child Adolesc Psychiatry)。非人灵长类有单细胞层面的对应证据：猴下前额叶在提示期即出现区分 Go 与 No-go 的神经元，128 个此类神经元中 106 个（83%）对侧、同侧视野的反应不对称(Sakagami & Niki, 1994, Exp Brain Res)。跨物种比较时须注意：两任务在解剖网络与神经化学调制上只有细微差别，不能假定等价(Eagle et al., 2008, Psychopharmacology)。

**必要条件。** ① 优势反应确实被建立（比例、间隔、时限三者配合，并有行为或 LRP 证据）；② No-go 试次数足以稳定估计虚报率；③ 反应装置固定，避免手指位置变化引入运动学差异；④ 报告完整参数，使他人能判断该数据能否与自己的任务相比(Wessel, 2018, Psychophysiology)。

## 质量控制与典型伪迹

**参数不报告，结果不可比。** 比例、间隔、时限、试次数四项缺一，读者无法判断优势反应是否存在。这不是格式问题：约 40% 的已发表研究采用等概率设计、约 20% 采用长间隔，而这两类设计的抑制需求都显著低于快节奏稀有 No-go 版本(Wessel, 2018, Psychophysiology)。

**地板效应与反应偏向。** 虚报率接近 0 时，组间差异被压缩到无法检测，此时应改用 d′ 与 c，或调整任务难度使错误率落在可测区间(Stanislaw & Todorov, 1999, Behav Res Methods Instrum Comput)。

**速度—准确性权衡被当成能力差异。** 改变反应时限会同时改变抑制表现、主观努力与皮肤电唤醒水平，N2 与 P3 也随之变化(Benikos et al., 2013, Int J Psychophysiol)。当两组使用不同时限，或一组被额外强调速度时，虚报率差异不能直接读作抑制差异。

**对照条件不等运动输出。** 若 No-go 条件比 Go 条件少一次按键，任何差异都可能来自运动执行本身。可行的控制是设置按键次数相等、只改变「是否按同一个键」的对照，或使用无运动但含冲突的对照任务(Donkers & van Boxtel, 2004, Brain Cogn; Rubia et al., 2003, NeuroImage)。运动相关电位的分析进一步显示，P3 的 No-go 效应在需要按键的版本中被放大，说明该成分混有运动成分(Smith et al., 2008, Clin Neurophysiol)。

**电生理指标选择不当。** N2 与 P3 都不是抑制的专属指标：N2 更符合冲突监测(Nieuwenhuis et al., 2003, Cogn Affect Behav Neurosci)，P3 含评价与运动成分(Smith et al., 2008, Clin Neurophysiol; Huster et al., 2013, Int J Psychophysiol)。把某一成分的波幅直接命名为「抑制强度」，是把相关当因果。

**影像结论外推过度。** 元分析显示 Go/No-Go 与 stop-signal 的共同激活位于右前岛叶与前辅助运动区，但前者更多调用额顶控制网络、后者更多调用扣带—岛盖网络，两者重叠而不相同(Swick et al., 2011, NeuroImage)。另有元分析指出，Go/No-Go 版本的共同激活以左半球内侧、内下额叶与顶叶为主，而 stop 任务以右半球前扣带、辅助运动区、下前额与顶叶为主(Rubia et al., 2001, NeuroImage)；这一左右差异与「抑制＝右侧额下回」的简化说法并不一致，引用时应说明任务类型。

**名称混淆与文献混入。** 检索「go/no-go」会同时命中 GNAT 等内隐测量方法(Nosek & Banaji, 2001, Soc Cogn)，其指标与反应抑制无关。建立检索式时应限定任务特征（刺激比例、反应窗口），而不是只用任务名。

**信度与效度的最低检查。** 若研究目的是个体差异或相关分析，应在报告效应前给出本样本的重测信度；文献中的经验值是冲动性行动类任务约 0.65–0.73(Weafer et al., 2013, Exp Clin Psychopharmacol)，而跨任务的行为指标整体信度偏低(Enkavi et al., 2019, Proc Natl Acad Sci U S A)。若研究目的是组间差异，则应意识到稳健的任务效应与可用的个体差异指标常常不能兼得(Hedge et al., 2018, Behav Res Methods)。

## 代表性实验或应用

**范式来源。** 持续作业测验要求被试对高频目标反应、对其余刺激不反应，用于评估脑损伤，是视觉 Go/No-Go 的结构前身(Rosvold et al., 1956, J Consult Psychol)。

**影像定位的早期证据。** 9 名健康被试的 PET 研究比较 GO/NO-GO 与单纯反应选择，报告了 NO-GO 决策相关的功能场(Kawashima et al., 1996, Brain Res)。事件相关 fMRI 进一步显示，成功抑制优势反应时出现右半球偏侧的中／下额回、额缘区与前岛叶瞬态激活(Garavan et al., 1999, Proc Natl Acad Sci U S A)。

**联合分析与任务依赖性。** 在 5 种抑制任务版本中做联合分析，Go/No-Go 与 stop 任务共享内侧、内下额叶与顶叶网络，但各自有特异成分(Rubia et al., 2001, NeuroImage)。把两种工作记忆负荷不同的 Go/No-Go 直接比较，简单版本 No-go 激活集中在前辅助运动区，高负荷版本额外调用右背侧前额叶(Mostofsky et al., 2003, Cogn Brain Res)。

**因果检验。** 经颅磁刺激暂时失活右侧额下回岛盖部后，被试停止已启动动作的能力选择性受损，反应执行与生理唤醒不受影响(Chambers et al., 2006, J Cogn Neurosci)。把抑制与错误检测分开的影像研究则显示，右侧额下皮层对应抑制、内侧前额对应错误检测(Rubia et al., 2003, NeuroImage)。

**临床与个体差异。** ADHD 儿童在包括 Go/No-Go 在内的三项反应抑制任务上表现更差，且与右侧额纹状体的解剖测量相关(Casey et al., 1997, J Am Acad Child Adolesc Psychiatry)。跨 11 类精神障碍的元分析给出虚报错误效应量 g = −0.10 至 0.52，结论是不足以单独作为诊断指标(Wright et al., 2014, J Abnorm Psychol)。作为对比，stop-signal 的元分析给出 ADHD g = 0.62、强迫症 g = 0.77、精神分裂症 g = 0.69(Lipszyc & Schachar, 2010, J Int Neuropsychol Soc)；两组数字不能互相替代。

**参数效应的直接检验。** 四组变体的 EEG 研究显示，只有快节奏、稀有 No-go 的版本可靠诱发优势运动活动，抑制相关活动在慢节奏等概率版本中减少约 75%(Wessel, 2018, Psychophysiology)。

**作为学习范式。** 把「做／不做」与奖赏／惩罚正交化后，被试在奖赏条件下更易学会主动选择、在惩罚条件下更易学会被动选择，模型化分析把这一不对称拆为工具性与巴甫洛夫成分(Guitart-Masip et al., 2012, NeuroImage)。这类用法测的是动作—结果学习，与反应抑制不是同一构念。

## 与其他方法的关系

**与 stop-signal 任务。** 两者都要求「不反应」，但只有 stop-signal 能估计抑制潜伏期(Logan & Cowan, 1984, Psychol Rev; Verbruggen & Logan, 2008, Trends Cogn Sci)。神经层面两者重叠而不等同：共同激活在右前岛叶与前辅助运动区，差异分布在额顶控制网络与扣带—岛盖网络(Swick et al., 2011, NeuroImage)。跨物种的药理学证据也提示两任务的神经化学调制存在差别(Eagle et al., 2008, Psychopharmacology)。选择哪一个取决于问题：要速度参数用 stop-signal，要「有／无反应」的离散结果与更短的试次用 Go/No-Go。stop-signal 的设计与报告已有共识清单可循(Verbruggen et al., 2019, eLife)。需要补充的是，纯反应性范式对精神科问题的建模能力被认为有限，反应性、前瞻性与选择性控制因此被区分为不同层次(Aron, 2011, Biol Psychiatry)；Go/No-Go 属于其中的反应性一端。

**与 CPT、SART 等持续作业变体。** CPT 以高频目标与低负荷维持为核心(Rosvold et al., 1956, J Consult Psychol)；SART 把 Go 比例推到极高，把失败解释为注意脱离(Robertson et al., 1997, Neuropsychologia)。它们与标准 Go/No-Go 共享按键／不按键结构，但目标构念不同，跨范式比较需先说明参数差异。

**与自评问卷和延迟满足任务。** 三类测量的收敛有限，总体 r ≈ 0.27，执行功能任务最弱(Duckworth & Kern, 2011, J Res Pers)；行为任务的指标信度普遍低于自评量表(Enkavi et al., 2019, Proc Natl Acad Sci U S A)。因此把 Go/No-Go 成绩与问卷分数做相关时，应先考虑测量误差对相关系数的衰减。

**与电生理和影像。** ERP 提供毫秒级过程信息但空间定位粗糙(Kiefer et al., 1998, NeuroReport; Bokura et al., 2001, Clin Neurophysiol)；fMRI 提供毫米级定位但时间分辨差、且高度依赖对照条件(Criaud & Boulinguez, 2013, Neurosci Biobehav Rev)。两者与行为同步时的价值在于约束解释，而不在于把某个成分或脑区命名为「抑制」。

**与因果干预。** 经颅磁刺激可对候选节点做暂时性失活(Chambers et al., 2006, J Cogn Neurosci)，单细胞记录可在非人灵长类给出提示期的神经元选择性(Sakagami & Niki, 1994, Exp Brain Res)。二者补足行为数据无法回答的机制问题，但空间精度与样本规模都限制了结论强度。

**与计算模型。** 竞赛模型为「停止」提供了可拟合的过程假设(Logan & Cowan, 1984, Psychol Rev; Verbruggen & Logan, 2009, Neurosci Biobehav Rev)；冲突监测模型为「No-go 激活＝冲突」提供了理论框架(Botvinick et al., 2001, Psychol Rev)；强化学习模型则可把「做／不做」拆成工具性与巴甫洛夫成分(Guitart-Masip et al., 2012, NeuroImage)。模型选择的差异会直接改变对同一批数据的解读。

**与构念分类工作。** 「抑制」被拆为执行性、动机性与自动注意性三类共 8 种，术语混用是跨研究不可比的主要来源(Nigg, 2000, Psychol Bull)；潜变量分析显示优势反应抑制与抗干扰共享成分、但与抗前提干扰无关(Friedman & Miyake, 2004, J Exp Psychol Gen)。反应抑制与冲动性的行为与神经基础被系统梳理后，同样指向「抑制是多成分构念」这一判断(Bari & Robbins, 2013, Prog Neurobiol)。这三项工作决定了 Go/No-Go 只能声称测量其中一个子成分。

## 相关节点

- [[03_方法与模型轴/03_方法与模型轴|方法与模型轴]]
- [[04_证据与推理轴/证据质量/可重复性|可重复性]]

以下主题在本库尚无已发布节点，暂以纯文本列出，待建后再改为双链：

- 反应抑制（构念与子成分划分）
- 停止信号任务（stop-signal task）
- 持续注意反应任务（SART）
- 事件相关电位（ERP）与 N2／P3 成分
- 前辅助运动区（pre-SMA）与右侧额下回
- 冲突监测理论
- 冲动性与自我控制的测量
- 信号检测论在行为任务计分中的应用

## 关键文献与资料

表格说明：本表按出版年升序排列，同年按第一作者姓氏字母序；第 1 列与正文引注逐字一致。第 3 列期刊使用《期刊简称映射表》统一简称。篇数不等于独立重复次数：同一实验室的系列研究、同一数据集的不同分析不构成独立验证。

| 正文引用 | 作者、年份与论文题名 | 期刊／卷页 | DOI／永久入口 | 证据性质 | 主要支持及限制 |
| --- | --- | --- | --- | --- | --- |
| (Rosvold et al., 1956, J Consult Psychol) | Rosvold HE; Mirsky AF; Sarason I; Bransome ED Jr; Beck LH (1956). A continuous performance test of brain damage. | J Consult Psychol 20(5):343–350 | [原文入口](https://doi.org/10.1037/h0043220) | 原始实验（临床对照） | 支持：确立高频目标加要求抑制的持续作业测验结构，是视觉 Go/No-Go 的直接前身。限制：研究目标是脑损伤定位，不含反应抑制的理论构念与现代试次级计时。 |
| (Logan & Cowan, 1984, Psychol Rev) | Logan GD; Cowan WB (1984). On the ability to inhibit thought and action: A theory of an act of control. | Psychol Rev 91(3):295–327 | [原文入口](https://doi.org/10.1037/0033-295X.91.3.295) | 理论／计算模型 | 支持：提出 go 与 stop 两过程独立竞赛的框架，是抑制潜伏期只能由模型反推这一判断的来源。限制：面向 stop-signal 设计，直接套用到 Go/No-Go 缺少可估参数。 |
| (Eimer, 1993, Biol Psychol) | Eimer M (1993). Effects of attention and stimulus probability on ERPs in a Go/Nogo task. | Biol Psychol 35(2):123–138 | [原文入口](https://doi.org/10.1016/0301-0511\(93\)90009-W) | 原始实验（ERP） | 支持：No-go 刺激引出更大 N2 与更靠前的 P3 拓扑；把 No-go 概率从 25% 改为 50% 后效应仍在。限制：概率操作同时改变注意负荷，两者未解耦。 |
| (Sakagami & Niki, 1994, Exp Brain Res) | Sakagami M; Niki H (1994). Spatial selectivity of go/no-go neurons in monkey prefrontal cortex. | Exp Brain Res 100(1):165–169 | [原文入口](https://doi.org/10.1007/BF00227290) | 原始实验（猴单细胞记录） | 支持：猴下前额叶存在提示期即区分 go 与 no-go 的神经元，128 个中 106 个对侧同侧视野反应不对称。限制：动物数量少，提示期活动是预备而非抑制的直接证据。 |
| (Kawashima et al., 1996, Brain Res) | Kawashima R; Satoh K; Itoh H; Ono S; Furumoto S; Gotoh R; et al. (1996). Functional anatomy of GO/NO-GO discrimination and response selection—a PET study in man. | Brain Res 728(1):79–89 | [原文入口](https://doi.org/10.1016/0006-8993\(96\)00389-7) | 原始实验（PET，n=9） | 支持：报告 NO-GO 决策相对反应选择的功能场差异。限制：区块设计、样本小，无法分离刺激识别与抑制过程。 |
| (Casey et al., 1997, J Am Acad Child Adolesc Psychiatry) | Casey BJ; Castellanos FX; Giedd JN; Marsh WL; Hamburger SD; Schubert AB; et al. (1997). Implication of right frontostriatal circuitry in response inhibition and attention-deficit hyperactivity disorder. | J Am Acad Child Adolesc Psychiatry 36(3):374–383 | [原文入口](https://doi.org/10.1097/00004583-199703000-00016) | 原始实验（MRI＋行为，ADHD 与对照儿童） | 支持：ADHD 儿童在包括 Go/No-Go 的三项抑制任务上表现更差，并与右侧额纹状体解剖测量相关。限制：相关设计，样本为儿童，未检验任务间构念等价性。 |
| (Logan et al., 1997, Psychol Sci) | Logan GD; Schachar RJ; Tannock R (1997). Impulsivity and inhibitory control. | Psychol Sci 8(1):60–64 | [原文入口](https://doi.org/10.1111/j.1467-9280.1997.tb00545.x) | 原始实验 | 支持：把抑制控制效率与冲动性联系起来的早期实证报告，确立抑制作为可测个体差异的用法。限制：该刊未被 Europe PMC 收录，摘要未独立核验，本节点仅作框架性引用。 |
| (Robertson et al., 1997, Neuropsychologia) | Robertson IH; Manly T; Andrade J; Baddeley BT; Yiend J (1997). 'Oops!': Performance correlates of everyday attentional failures in traumatic brain injured and normal subjects. | Neuropsychologia 35(6):747–758 | [原文入口](https://doi.org/10.1016/S0028-3932%2897%2900015-8) | 原始实验（34 例脑外伤患者＋正常对照） | 支持：建立 SART 这一高 Go 比例变体，把失败解释为注意脱离并与日常注意失误相关。限制：解释框架改变后，同一装置测量的构念已不是反应抑制。 |
| (Kiefer et al., 1998, NeuroReport) | Kiefer M; Marzinzik F; Weisbrod M; Scherg M; Spitzer M (1998). The time course of brain activations during response inhibition: evidence from event-related potentials in a go/no go task. | NeuroReport 9(4):765–770 | [原文入口](https://doi.org/10.1097/00001756-199803090-00037) | 原始实验（ERP＋源分析） | 支持：刺激后约 260 ms 起出现下前额区抑制相关效应，300–600 ms 出现左偏侧额中央效应。限制：偶极源定位的逆问题不唯一，时间进程不等于机制序列。 |
| (Falkenstein et al., 1999, Acta Psychol) | Falkenstein M; Hoormann J; Hohnsbein J (1999). ERP components in Go/Nogo tasks and their relation to inhibition. | Acta Psychol 101(2–3):267–291 | [原文入口](https://doi.org/10.1016/S0001-6918%2899%2900008-6) | 原始实验（ERP） | 支持：高虚报率被试的 Nogo-N2 更小或更晚，支持 N2 与抑制相关。限制：同文报告听觉模态下 Nogo-N2 极小，作者自己给出不利于普遍化的反例。 |
| (Garavan et al., 1999, Proc Natl Acad Sci U S A) | Garavan H; Ross TJ; Stein EA (1999). Right hemispheric dominance of inhibitory control: An event-related functional MRI study. | Proc Natl Acad Sci U S A 96(14):8301–8306 | [原文入口](https://doi.org/10.1073/pnas.96.14.8301) | 原始实验（事件相关 fMRI） | 支持：成功抑制优势反应时出现右偏侧的中下额回、额缘区与前岛叶瞬态激活。限制：样本小；右偏侧结论后来被控制注意需求的研究部分修正。 |
| (Stanislaw & Todorov, 1999, Behav Res Methods Instrum Comput) | Stanislaw H; Todorov N (1999). Calculation of signal detection theory measures. | Behav Res Methods Instrum Comput 31(1):137–149 | [原文入口](https://doi.org/10.3758/BF03207704) | 方法学（计算工具论文） | 支持：给出 d′ 与 c 等指标的计算与校正方法，是把辨别力与反应偏向分开的标准依据。限制：只解决计分，不解决任务设计的构念问题。 |
| (Nigg, 2000, Psychol Bull) | Nigg JT (2000). On inhibition/disinhibition in developmental psychopathology: Views from cognitive and personality psychology and a working inhibition taxonomy. | Psychol Bull 126(2):220–246 | [原文入口](https://doi.org/10.1037/0033-2909.126.2.220) | 同行评议综述（分类学） | 支持：把抑制拆为执行性、动机性与自动注意性三类共 8 种，指出术语混用是跨研究不可比的主因。限制：属概念性提案，未提供任务间实证等价性检验。 |
| (Bokura et al., 2001, Clin Neurophysiol) | Bokura H; Yamaguchi S; Kobayashi S (2001). Electrophysiological correlates for response inhibition in a Go/NoGo task. | Clin Neurophysiol 112(12):2224–2232 | [原文入口](https://doi.org/10.1016/S1388-2457%2801%2900691-5) | 原始实验（高密度 EEG，n=13） | 支持：Go 与 NoGo 在 P1、N1 上无差异；N2 仅见于 NoGo，源定位指向右侧外侧眶额与扣带；NoGo-P3 更大更长且更靠前。限制：样本小，源定位空间分辨有限。 |
| (Botvinick et al., 2001, Psychol Rev) | Botvinick MM; Braver TS; Barch DM; Carter CS; Cohen JD (2001). Conflict monitoring and cognitive control. | Psychol Rev 108(3):624–652 | [原文入口](https://doi.org/10.1037/0033-295X.108.3.624) | 理论／计算模型 | 支持：提出控制需求由冲突信号触发，为 No-go 激活的冲突解释提供框架。限制：模型未针对 Go/No-Go 的具体参数做定量预测。 |
| (Nosek & Banaji, 2001, Soc Cogn) | Nosek BA; Banaji MR (2001). The Go/No-Go Association Task. | Soc Cogn 19(6):625–666 | [原文入口](https://doi.org/10.1521/soco.19.6.625.20886) | 原始实验（内隐测量方法） | 支持：同名任务用按键与不按键的结构测量内隐联想强度，说明任务名在文献中指向两种构念。限制：参数、指标与解释均与反应抑制范式不同，不可互引；该刊未被 Europe PMC 收录。 |
| (Rubia et al., 2001, NeuroImage) | Rubia K; Russell T; Overmeyer S; Brammer MJ; Bullmore ET; Sharma T; et al. (2001). Mapping motor inhibition: Conjunctive brain activations across different versions of go/no-go and stop tasks. | NeuroImage 13(2):250–261 | [原文入口](https://doi.org/10.1006/nimg.2000.0685) | 原始实验（fMRI 联合分析，n=15） | 支持：5 种抑制任务共享内侧、内下额叶与顶叶网络；Go/No-Go 版本以左半球为主，stop 版本以右半球为主。限制：联合分析只给交集，不能证明该区执行抑制。 |
| (Mostofsky et al., 2003, Cogn Brain Res) | Mostofsky SH; Schafer JGB; Abrams MT; Goldberg MC; Flower AA; Boyce A; et al. (2003). fMRI evidence that the neural basis of response inhibition is task-dependent. | Cogn Brain Res 17(2):419–430 | [原文入口](https://doi.org/10.1016/S0926-6410%2803%2900144-7) | 原始实验（事件相关 fMRI） | 支持：简单版本 No-go 激活集中在前辅助运动区，高工作记忆负荷版本额外调用右背侧前额叶。限制：两版本在规则与刺激上同时不同，工作记忆与其他要求未完全解耦。 |
| (Nieuwenhuis et al., 2003, Cogn Affect Behav Neurosci) | Nieuwenhuis S; Yeung N; van den Wildenberg W; Ridderinkhof KR (2003). Electrophysiological correlates of anterior cingulate function in a go/no-go task: Effects of response conflict and trial type frequency. | Cogn Affect Behav Neurosci 3(1):17–26 | [原文入口](https://doi.org/10.3758/CABN.3.1.17) | 原始实验（ERP） | 支持：在需要做出反应但冲突高的条件下同样出现 N2，说明 N2 反映冲突而非抑制。限制：由头皮电位推断源区，仍是间接证据。 |
| (Rubia et al., 2003, NeuroImage) | Rubia K; Smith AB; Brammer MJ; Taylor E (2003). Right inferior prefrontal cortex mediates response inhibition while mesial prefrontal cortex is responsible for error detection. | NeuroImage 20(1):351–358 | [原文入口](https://doi.org/10.1016/S1053-8119%2803%2900275-1) | 原始实验（快速混合事件相关 fMRI） | 支持：以等运动输出的对照把抑制与错误检测分开，右侧额下皮层对应抑制、内侧前额对应错误检测。限制：以 BOLD 差减推断过程，样本为成人。 |
| (Aron et al., 2004, Trends Cogn Sci) | Aron AR; Robbins TW; Poldrack RA (2004). Inhibition and the right inferior frontal cortex. | Trends Cogn Sci 8(4):170–177 | [原文入口](https://doi.org/10.1016/j.tics.2004.02.010) | 同行评议综述 | 支持：整合影像与病变证据，把反应抑制定位到右侧额下皮层。限制：立场明确，后续被注意控制解释部分修正。 |
| (Donkers & van Boxtel, 2004, Brain Cogn) | Donkers FCL; van Boxtel GJM (2004). The N2 in go/no-go tasks reflects conflict monitoring not response inhibition. | Brain Cogn 56(2):165–176 | [原文入口](https://doi.org/10.1016/j.bandc.2004.04.005) | 原始实验（ERP，go/no-go 与 go/GO 对照） | 支持：用无抑制但含冲突的 go/GO 任务，N2 在两任务均出现且随 Go 频率升高而增大，直接反驳 N2 等于抑制。限制：go/GO 对照在运动准备上并不完全等同。 |
| (Friedman & Miyake, 2004, J Exp Psychol Gen) | Friedman NP; Miyake A (2004). The relations among inhibition and interference control functions: A latent-variable analysis. | J Exp Psychol Gen 133(1):101–135 | [原文入口](https://doi.org/10.1037/0096-3445.133.1.101) | 原始实验（潜变量分析，n=220） | 支持：优势反应抑制与抗干扰共享成分，但与抗前提干扰无关，抑制不是单一功能。限制：样本为成人，因子结构依赖所选任务组合。 |
| (Chambers et al., 2006, J Cogn Neurosci) | Chambers CD; Bellgrove MA; Stokes MG; Henderson TR; Garavan H; Robertson IH; Morris AP; Mattingley JB (2006). Executive "brake failure" following deactivation of human frontal lobe. | J Cogn Neurosci 18(3):444–455 | [原文入口](https://doi.org/10.1162/jocn.2006.18.3.444) | 原始实验（TMS 暂时性失活） | 支持：失活右侧额下回岛盖部选择性损害停止已启动动作的能力，不影响反应执行与生理唤醒。限制：范式属停止信号类而非纯 Go/No-Go；TMS 空间精度为厘米量级。 |
| (Eagle et al., 2008, Psychopharmacology) | Eagle DM; Bari A; Robbins TW (2008). The neuropsychopharmacology of action inhibition: Cross-species translation of the stop-signal and go/no-go tasks. | Psychopharmacology 199(3):439–456 | [原文入口](https://doi.org/10.1007/s00213-008-1127-6) | 同行评议综述 | 支持：两任务在解剖网络与 5-HT 等神经化学调制上只有细微差别，提示不能简单互替。限制：综述层面的比较，缺少统一参数的跨任务实验。 |
| (Simmonds et al., 2008, Neuropsychologia) | Simmonds DJ; Pekar JJ; Mostofsky SH (2008). Meta-analysis of Go/No-go tasks demonstrating that fMRI activation associated with response inhibition is task-dependent. | Neuropsychologia 46(1):224–232 | [原文入口](https://doi.org/10.1016/j.neuropsychologia.2007.07.015) | 元分析（激活似然估计） | 支持：简单与复杂 Go/No-Go 的共激活模式不同，右背侧前额叶与顶下小叶在工作记忆需求高时被调用；两版本共同激活前辅助运动区与左梭状回。限制：纳入研究的基线条件不统一，方法对样本量敏感。 |
| (Smith et al., 2008, Clin Neurophysiol) | Smith JL; Johnstone SJ; Barry RJ (2008). Movement-related potentials in the Go/NoGo task: The P3 reflects both cognitive and motor inhibition. | Clin Neurophysiol 119(3):704–714 | [原文入口](https://doi.org/10.1016/j.clinph.2007.11.042) | 原始实验（ERP 与运动相关电位，n=20） | 支持：N2 的 NoGo 效应在计数与按键两版本相同，P3 的 NoGo 效应在按键版本放大，说明 P3 混有运动成分。限制：计数版本本身改变了任务要求，两版本并非只差运动输出。 |
| (Verbruggen & Logan, 2008, Trends Cogn Sci) | Verbruggen F; Logan GD (2008). Response inhibition in the stop-signal paradigm. | Trends Cogn Sci 12(11):418–424 | [原文入口](https://doi.org/10.1016/j.tics.2008.07.005) | 同行评议综述 | 支持：说明 stop-signal 是实验室量化抑制过程的适用设计。限制：其设计逻辑依赖延迟停止信号，Go/No-Go 中不存在该结构。 |
| (Verbruggen & Logan, 2009, Neurosci Biobehav Rev) | Verbruggen F; Logan GD (2009). Models of response inhibition in the stop-signal and stop-change paradigms. | Neurosci Biobehav Rev 33(5):647–661 | [原文入口](https://doi.org/10.1016/j.neubiorev.2008.08.014) | 同行评议综述（模型） | 支持：独立竞赛模型对 stop-signal 数据拟合良好，并讨论交互式竞赛等替代模型。限制：模型假设在 Go/No-Go 中没有对应的可估量。 |
| (Hampshire et al., 2010, NeuroImage) | Hampshire A; Chamberlain SR; Monti MM; Duncan J; Owen AM (2010). The role of the right inferior frontal gyrus: Inhibition and attentional control. | NeuroImage 50(3):1313–1319 | [原文入口](https://doi.org/10.1016/j.neuroimage.2009.12.109) | 原始实验（fMRI，控制注意需求） | 支持：保持刺激条件、只改变抑制要求时，右侧额下回的抑制特异反应明显减弱，提示其更多反映注意或显著性检测。限制：单一任务族的参数操作，外推需谨慎。 |
| (Lipszyc & Schachar, 2010, J Int Neuropsychol Soc) | Lipszyc J; Schachar R (2010). Inhibitory control and psychopathology: A meta-analysis of studies using the stop signal task. | J Int Neuropsychol Soc 16(6):1064–1076 | [原文入口](https://doi.org/10.1017/S1355617710000895) | 元分析 | 支持：ADHD g=0.62、强迫症 g=0.77、精神分裂症 g=0.69，焦虑与自闭接近正常。限制：基于 stop-signal 的抑制潜伏期，不能移用到 Go/No-Go 的虚报率。 |
| (Sharp et al., 2010, Proc Natl Acad Sci U S A) | Sharp DJ; Bonnelle V; De Boissezon X; Beckmann CF; James SG; Patel MC; et al. (2010). Distinct frontal systems for response inhibition, attentional capture, and error processing. | Proc Natl Acad Sci U S A 107(13):6106–6111 | [原文入口](https://doi.org/10.1073/pnas.1000175107) | 原始实验（fMRI，分离注意捕获） | 支持：剥离注意捕获后，右侧额下回更多归入腹侧注意系统，抑制与内侧额区更相关。限制：仍为相关影像证据，未做因果干预。 |
| (Aron, 2011, Biol Psychiatry) | Aron AR (2011). From reactive to proactive and selective control: Developing a richer model for stopping inappropriate responses. | Biol Psychiatry 69(12):e55–e68 | [原文入口](https://doi.org/10.1016/j.biopsych.2010.07.024) | 同行评议综述（理论） | 支持：提出反应性、前瞻性与选择性三层控制，指出纯反应性范式对精神科问题的建模能力有限。限制：框架性提案，前瞻性控制的测量范式尚未标准化。 |
| (Duckworth & Kern, 2011, J Res Pers) | Duckworth AL; Kern ML (2011). A meta-analysis of the convergent validity of self-control measures. | J Res Pers 45(3):259–268 | [原文入口](https://doi.org/10.1016/j.jrp.2011.02.004) | 元分析（282 个样本，N=33,564） | 支持：执行功能任务、延迟满足与自评他评量表的总体收敛仅 r≈0.27，其中执行功能任务最弱。限制：纳入测量高度异质，r 值不能直接解释为测量无效。 |
| (Swick et al., 2011, NeuroImage) | Swick D; Ashley V; Turken U (2011). Are the neural correlates of stopping and not going identical? Quantitative meta-analysis of two response inhibition tasks. | NeuroImage 56(3):1655–1665 | [原文入口](https://doi.org/10.1016/j.neuroimage.2011.02.070) | 元分析（激活似然估计） | 支持：两任务共同激活右前岛叶与前辅助运动区；Go/No-Go 更多调用额顶控制网络，stop-signal 更多调用扣带岛盖网络。限制：受原始研究对照条件异质性限制。 |
| (Guitart-Masip et al., 2012, NeuroImage) | Guitart-Masip M; Huys QJM; Fuentemilla L; Dayan P; Duzel E; Dolan RJ (2012). Go and no-go learning in reward and punishment: Interactions between affect and effect. | NeuroImage 62(1):154–166 | [原文入口](https://doi.org/10.1016/j.neuroimage.2012.04.024) | 原始实验（强化学习＋模型化 fMRI） | 支持：正交化动作要求与结果效价后，奖赏条件更易学会主动选择、惩罚条件更易学会被动选择。限制：测的是动作—结果学习，与反应抑制不是同一构念。 |
| (Bari & Robbins, 2013, Prog Neurobiol) | Bari A; Robbins TW (2013). Inhibition and impulsivity: Behavioral and neural basis of response control. | Prog Neurobiol 108:44–79 | [原文入口](https://doi.org/10.1016/j.pneurobio.2013.06.005) | 同行评议综述 | 支持：系统梳理反应抑制的行为与神经基础，明确抑制是多成分构念。限制：综合多物种多范式，具体数值不具跨研究可比性。 |
| (Benikos et al., 2013, Int J Psychophysiol) | Benikos N; Johnstone SJ; Roodenrys SJ (2013). Varying task difficulty in the Go/Nogo task: The effects of inhibitory control, arousal, and perceived effort on ERP components. | Int J Psychophysiol 87(3):262–272 | [原文入口](https://doi.org/10.1016/j.ijpsycho.2012.08.005) | 原始实验（ERP＋皮肤电，n=60，三档难度） | 支持：改变反应时限同时改变抑制表现、主观努力与唤醒水平，N2 与 P3 随难度变化。限制：难度与唤醒共变，无法完全解耦。 |
| (Criaud & Boulinguez, 2013, Neurosci Biobehav Rev) | Criaud M; Boulinguez P (2013). Have we been asking the right questions when assessing response inhibition in go/no-go tasks with fMRI? A meta-analysis and critical review. | Neurosci Biobehav Rev 37(1):11–23 | [原文入口](https://doi.org/10.1016/j.neubiorev.2012.11.003) | 元分析＋批判性综述（30 项 fMRI 实验） | 支持：按简单与复杂刺激分组后，多数 No-go 激活（含前辅助运动区）由注意或工作记忆负荷驱动，而非抑制本身。限制：以刺激复杂度作代理变量，分组边界有主观性。 |
| (Huster et al., 2013, Int J Psychophysiol) | Huster RJ; Enriquez-Geppert S; Lavallee CF; Falkenstein M; Herrmann CS (2013). Electroencephalography of response inhibition tasks: Functional networks and cognitive contributions. | Int J Psychophysiol 87(3):217–233 | [原文入口](https://doi.org/10.1016/j.ijpsycho.2012.08.001) | 同行评议综述 | 支持：额中线 N200／theta 偏冲突监测或反应程序更新，前部 P300／delta 偏反应相关的评价阶段，成分与心理过程非一对一。限制：综述层面的归纳，缺少决定性实验。 |
| (Weafer et al., 2013, Exp Clin Psychopharmacol) | Weafer J; Baggott MJ; de Wit H (2013). Test–retest reliability of behavioral measures of impulsive choice, impulsive action, and inattention. | Exp Clin Psychopharmacol 21(6):475–481 | [原文入口](https://doi.org/10.1037/a0033659) | 原始实验（重测信度，n=128，两次施测） | 支持：冲动性行动类任务（含 Go/No-Go）的重测相关约 0.65–0.73。限制：健康成人、施测间隔较短，不能外推到临床样本与长间隔。 |
| (Erika-Florence et al., 2014, Nat Commun) | Erika-Florence M; Leech R; Hampshire A (2014). A functional network perspective on response inhibition and attentional control. | Nat Commun 5:4073 | [原文入口](https://doi.org/10.1038/ncomms5073) | 原始实验（4 种 stop-signal 变体 fMRI） | 支持：额下皮层亚区对抑制需求没有功能唯一性，激活最强的情形是处理低频刺激，与是否需要抑制无关。限制：基于 stop-signal 变体，对 Go/No-Go 的直接检验仍少。 |
| (Wright et al., 2014, J Abnorm Psychol) | Wright L; Lipszyc J; Dupuis A; Thayapararajah SW; Schachar R (2014). Response inhibition and psychopathology: A meta-analysis of go/no-go task performance. | J Abnorm Psychol 123(2):429–439 | [原文入口](https://doi.org/10.1037/a0036295) | 元分析（318 项研究，11 类精神障碍） | 支持：虚报错误效应量从焦虑障碍 g=−0.10 到双相障碍 g=0.52；单独用作诊断指标或生物标志物的敏感性与特异性不足。限制：任务版本与计分方式不统一。 |
| (Wessel & Aron, 2017, Neuron) | Wessel JR; Aron AR (2017). On the globality of motor suppression: Unexpected events and their influence on behavior and cognition. | Neuron 93(2):259–280 | [原文入口](https://doi.org/10.1016/j.neuron.2016.12.013) | 同行评议综述（理论） | 支持：提出意外事件经额—基底节停止网络产生全局抑制，可解释 No-go 后的反应变慢。限制：解释框架，直接检验仍有限。 |
| (Hedge et al., 2018, Behav Res Methods) | Hedge C; Powell G; Sumner P (2018). The reliability paradox: Why robust cognitive tasks do not produce reliable individual differences. | Behav Res Methods 50(3):1166–1186 | [原文入口](https://doi.org/10.3758/s13428-017-0935-1) | 方法学（模拟＋实证） | 支持：任务效应稳健与个体差异信度高在统计上相互牵制，组间变异小则个体差异信度低。限制：主证来自 Stroop 与 Flanker，Go/No-Go 属同一逻辑的延伸。 |
| (Wessel, 2018, Psychophysiology) | Wessel JR (2018). Prepotent motor activity and inhibitory control demands in different variants of the go/no-go paradigm. | Psychophysiology 55(3):e12871 | [原文入口](https://doi.org/10.1111/psyp.12871) | 原始实验（EEG 四变体）＋文献调查 | 支持：只有快节奏稀有 No-go 版本可靠诱发优势运动活动；慢节奏等概率版本的抑制相关活动减少约 75%；文献中约 40% 用等概率、约 20% 用长于 4 s 的间隔。限制：单实验室样本，LRP 为间接指标。 |
| (Enkavi et al., 2019, Proc Natl Acad Sci U S A) | Enkavi AZ; Eisenberg IW; Bissett PG; Mazza GL; MacKinnon DP; Marsch LA; Poldrack RA (2019). Large-scale analysis of test–retest reliabilities of self-regulation measures. | Proc Natl Acad Sci U S A 116(12):5472–5477 | [原文入口](https://doi.org/10.1073/pnas.1818430116) | 原始实验＋文献综述（大规模重测） | 支持：自评量表信度高，行为任务导出的指标普遍偏低，文献中的估计高度变异；部分模型参数可接近原始指标的稳定性。限制：样本为在线成人，实施环境不同于实验室。 |
| (Verbruggen et al., 2019, eLife) | Verbruggen F; Aron AR; Band GP; Beste C; Bissett PG; Brockett AT; et al. (2019). A consensus guide to capturing the ability to inhibit actions and impulsive behaviors in the stop-signal task. | eLife 8:e46323 | [原文入口](https://doi.org/10.7554/eLife.46323) | 共识指南 | 支持：给出 stop-signal 设计、计分与报告的规范清单，并说明偏离规范对效度的影响。限制：针对 stop-signal，Go/No-Go 只能借用其报告透明度原则，不能借用其指标。 |
