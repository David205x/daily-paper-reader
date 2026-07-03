---
title: Inverse reinforcement learning reveals action-oriented value signals in naturalistic decision making
title_zh: 逆向强化学习揭示自然决策中面向行动的价值信号
authors: "Lee, S. H., Chung, C., Oh, M.-h., Ahn, W.-Y."
date: 2026-06-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.24.733779v1.full.pdf"
tags: ["query:rl"]
score: 6.0
evidence: 逆强化学习用于推断奖励函数
tldr: 自然决策中标准模型难以计算实时行为价值。本研究在fMRI驾驶任务中用逆强化学习(IRL)推断逐刻奖励轨迹，发现其与背侧纹状体价值动作选择信号最相关，并涉及认知控制、感觉运动区域。结果表明IRL奖励是行动导向估价的神经代理，揭示了价值与多脑区交互的机制。
source: biorxiv
selection_source: fresh_fetch
motivation: 标准决策模型在自然范式中受限，逆强化学习的神经可解释性未知，需探究其价值信号基础。
method: 采用fMRI实时驾驶任务，利用逆强化学习从行为观测推断奖励轨迹，并与全脑BOLD信号进行回归分析。
result: IRL奖励轨迹与背侧纹状体激活最强相关，同时协调认知控制与感觉运动网络的分布式活动。
conclusion: IRL奖励为自然决策中的行动导向估价提供了行为基础且时间解析的神经代理，反映价值与多过程的整合。
---

## 摘要
认知神经科学的一个主要挑战是解释复杂自然环境中目标导向行为的价值如何计算。标准的决策计算模型在受控的、基于试验的范式中非常成功，但往往不适合自然范式中实时展开的行为。逆向强化学习（IRL）提供了一种方法，可以从自然环境中观察到的行为推断潜在的评估状态，但其神经可解释性仍然很大程度上未知。在这里，我们研究了在fMRI扫描期间执行实时驾驶任务时，从IRL得出的瞬时奖励轨迹是否映射到大脑中的价值信号。IRL衍生的奖励轨迹与背侧纹状体（一个通常与价值引导的行动选择相关的区域）的活动最为强烈相关。它们还与支持额外过程（包括认知控制和感觉运动处理）的分布式区域表现出关联。这种模式表明，IRL奖励捕获了以奖励回路为中心的分布式神经活动，可能反映了估值如何与其他过程相互作用。总之，这些发现表明，IRL奖励为自然决策中面向行动的估值提供了基于行为、时间分辨的代理。

## Abstract
A major challenge for cognitive neuroscience is to explain how value of a goal-directed behavior is computed in complex and naturalistic environments. Standard computational models of decision making have been highly successful in controlled, trial-based paradigms, but they are often ill-suited to real-time behavior unfolding in naturalistic paradigms. Inverse reinforcement learning (IRL) offers a way to infer latent evaluative state from observed behavior in naturalistic environments, but its neural interpretability remains largely unknown. Here, we investigated whether moment-to-moment reward trajectories derived from IRL map onto value signals in the brain during a real-time driving task performed during fMRI scanning. IRL-derived reward trajectories were most robustly associated with activity in the dorsal striatum, a region often linked to value-guided action selection. They also showed associations with distributed regions supporting additional processes, including cognitive control and sensorimotor processing. This pattern suggests that IRL reward captures distributed neural activity centered on the reward circuitry, potentially reflecting how valuation interacts with other processes. Together, these findings suggest that IRL reward provides a behaviorally grounded, temporally resolved proxy for action-oriented valuation during naturalistic decision making.