---
title: "ChatGEM: An Agentic Architecture Enabling Interactive Simulation of Genome-Scale Metabolic Models"
title_zh: ChatGEM：一种支持基因组规模代谢模型交互模拟的智能体架构
authors: "Chowdhury, N., George, A., Purohit, S., Contolesi, A., Bredeweg, E. L., Czajka, J., Stratton, K. G., Gao, Y., Stephenson, M., Elmore, J. R., Scott, A., Leach, D. T., Jerger, A., Lemmon, T., Piehowski, P., Tate, K., Fulcher, J. M., Beliaev, A., Burnum-Johnson, K., Rigor, P., Bardhan, J."
date: 2026-07-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.20.739662v1.full.pdf"
tags: ["query:rl"]
score: 8.0
evidence: 基于RAG的LLM智能体用于科研任务自动化
tldr: 基因组规模代谢模型(GEM)需要计算专业知识，限制了广泛使用。为解决这一挑战，提出了ChatGEM，一种基于多智能体ADEPT框架的交互式平台，通过集成COBRApy和检索增强生成(RAG)架构，实现自然语言驱动的GEM仿真。在三个复杂度递增的任务上，RAG使平均性能从2.63提升至4.20，并大幅减少执行时间。应用于酶约束GEM的假单胞菌菌株，成功识别出最佳琥珀酸生产底盘，预测与实验一致。ChatGEM降低了代谢建模门槛，使非计算专家也能进行复杂分析，加速科学发现。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1533, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1733, \"height\": 1237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1723, \"height\": 1346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1725, \"height\": 1969, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1757, \"height\": 1626, \"label\": \"Table\"}]"
motivation: GEM分析需要计算专业知识，阻碍了生物学家广泛应用，需要更易用的交互工具。
method: 基于多智能体ADEPT框架，集成COBRApy和RAG，通过专门智能体协调代码生成与执行，支持自然语言交互。
result: RAG使性能从2.63提升至4.20，执行时间显著减少；在ecGEM菌株中准确识别最优琥珀酸生产底盘。
conclusion: ChatGEM实现了自然语言驱动的GEM仿真，使非计算专家也能进行复杂分析，加速代谢工程研究。
---

## 摘要
基因组规模代谢模型（GEMs）是预测细胞表型和指导微生物菌株工程的有力工具，但由于需要计算专业知识，其广泛采用仍面临挑战。为克服这一难题，我们提出了ChatGEM，一个通过自然语言实现交互式GEM模拟的智能体平台。基于多智能体ADEPT框架，ChatGEM在检索增强生成（RAG）架构中集成了COBRApy，通过专门智能体协调代码生成与执行。在三个复杂度递增的任务上进行基准测试表明，启用RAG的代码生成将平均整体性能得分从2.63提高到4.20，同时从常规任务到复杂任务显著缩短了执行时间。使用酶约束GEM（ecGEM）对四种工程改造的恶臭假单胞菌KT2440菌株应用ChatGEM，通过琥珀酸泄漏指数确定了组成型菌株为琥珀酸过量生产的最佳底盘——这一预测已通过实验观测得到验证。因此，ChatGEM通过使缺乏计算专业知识的研究人员能够通过自然语言执行基于GEM的复杂分析，从而民主化了代谢建模，进而加速科学发现。

## Abstract
Genome-scale metabolic models (GEMs) are powerful tools for predicting cellular phenotypes and guiding microbial strain engineering, yet broad adoption remains challenging due to the computational expertise required. To overcome that, we present ChatGEM, an agentic platform that enables interactive GEM simulation through natural language. Built on the multi-agent ADEPT framework, ChatGEM integrates COBRApy within a retrieval-augmented generation (RAG) architecture that coordinates code generation and execution through specialized agents. Benchmarking across three tasks of increasing complexity showed that RAG-enabled code generation improved the mean overall performance score from 2.63 to 4.20 while reducing the execution time significantly starting from routine to complex tasks. Application of ChatGEM using an enzyme-constrained GEM (ecGEM) for four engineered Pseudomonas putida KT2440 strains identified the constitutive strain as the optimal chassis for succinate overproduction using a succinate leakage index - a prediction observed experimentally. Therefore, ChatGEM democratizes metabolic modeling by enabling researchers without computational expertise to perform sophisticated GEM-based analyses through natural language, and, hence, accelerating scientific discovery.