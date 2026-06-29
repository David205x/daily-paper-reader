---
title: Benchmarking and behavioral characterization of LLM agents for protein design
title_zh: 蛋白质设计中的LLM智能体基准测试与行为特征描述
authors: "Kim, J., Romero, P. A."
date: 2026-06-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.06.723381v2.full.pdf"
tags: ["query:rl"]
score: 6.0
evidence: LLM智能体在科学任务自动化中的基准测试
tldr: LLM代理用于科学发现缺乏标准化评估框架，蛋白质设计任务复杂。本文提出BioDesignBench基准，含76个专家任务，评估四个前沿LLM代理。最强代理超过硬编码流程但低于专家实践；行为分解显示缺陷在评估深度而非工具选择。强制多指标评估显著提升性能，表明差距是行为性的。发布基准、开源代理和排行榜，推动蛋白质工程AI评估。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有评估框架缺乏，蛋白质设计需要标准化基准以衡量LLM代理性能与行为。
method: 构建BioDesignBench基准，含76个专家任务，结合人类和非LLM基线，分析工具使用痕迹与行为指标。
result: 最强代理超越硬编码但低于专家；行为分析表明评估深度不足，强制多维度评估显著提升性能。
conclusion: LLM代理在蛋白质设计中的差距是行为性的而非能力限制，增强评估深度可改善表现。
---

## 摘要
大型语言模型（LLM）越来越多地被部署为科学发现的智能体，但在科学工作流中评估其性能和行为的标准化框架仍然缺乏。蛋白质设计提供了一个极具挑战性的测试案例，因为现代工作流结合了随机生成模型、结构预测系统和基于物理的评估工具，需要大量的候选探索和筛选。在此，我们引入BioDesignBench，这是一个包含76个专家策划的蛋白质设计任务的基准，涵盖抗体、酶、荧光蛋白、结合剂和支架，同时提供人类和非LLM基线以及基于工具使用轨迹的行为指标。我们评估了四个前沿LLM智能体在多种蛋白质设计工作流中的表现，发现最强智能体超越了确定性的硬编码流程，但始终不如专家实践。沿着工具覆盖和评估深度两个正交轴分解智能体行为，我们将差距定位在评估而非工具选择上：智能体通常选择适当的工具，但仅针对少数指标对每个候选进行评分，很少比较替代方案，并且过早终止探索。引导式工作流提高了工具覆盖，但未提升评估深度。一种计算匹配的强制深度干预要求智能体在多个互补指标类别（结构、界面、物理和学习亲和力）上评估每个候选，显著提高了性能并排除了通用支撑效应，表明差距是行为性的而非基本能力限制。所有评估均为计算机模拟。我们发布BioDesignBench、开源参考智能体和一个公开排行榜，作为评估和改进蛋白质工程AI智能体的社区资源。

## Abstract
Large language models (LLMs) are increasingly deployed as agents for scientific discovery, but standardized frame- works for evaluating their performance and behavior in scientific workflows are lacking. Protein design provides a demanding test case because modern workflows combine stochastic generative models, structure prediction systems, and physics-based evaluation tools that require extensive candidate exploration and filtering. Here we introduce BioDesignBench, a benchmark of 76 expert-curated protein design tasks spanning antibodies, enzymes, fluores- cent proteins, binders, and scaffolds, together with human and non-LLM baselines and behavioral metrics derived from tool-use traces. We evaluate four frontier LLM agents across diverse protein design workflows and find that the strongest agents surpass deterministic hardcoded pipelines but consistently underperform expert practice. Decomposing agent behavior along orthogonal axes of tool coverage and evaluation depth, we localize the gap to evaluation rather than tool selection: agents generally pick appropriate tools but score each candidate against only a narrow set of metrics, rarely compare alternatives, and terminate exploration prematurely. Guided work- flows improve tool coverage but not evaluation depth. A compute-matched forced-depth intervention that requires agents to evaluate every candidate across multiple complementary metric categories (structure, interface, physics, and learned affinity) substantially improves performance and rules out generic scaffolding effects, demonstrating that the gap is behavioral rather than a fundamental capability constraint. All evaluations are performed in silico. We release BioDesignBench, open-source reference agents, and a public leaderboard as a community resource for evaluating and improving AI agents for protein engineering.