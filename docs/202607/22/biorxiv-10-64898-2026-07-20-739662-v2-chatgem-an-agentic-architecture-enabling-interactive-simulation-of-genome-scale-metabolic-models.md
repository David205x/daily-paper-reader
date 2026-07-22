---
title: "ChatGEM: An Agentic Architecture Enabling Interactive Simulation of Genome-Scale Metabolic Models"
title_zh: ChatGEM：一种实现基因组规模代谢模型交互式模拟的代理架构
authors: "Chowdhury, N., George, A., Purohit, S., Contolesi, A., Bredeweg, E. L., Czajka, J., Stratton, K. G., Gao, Y., Stephenson, M., Elmore, J. R., Scott, A., Leach, D. T., Jerger, A., Lemmon, T., Piehowski, P., Tate, K., Fulcher, J. M., Beliaev, A., Burnum-Johnson, K., Rigor, P., Bardhan, J."
date: 2026-07-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.20.739662v2.full.pdf"
tags: ["query:rl"]
score: 7.0
evidence: 检索增强生成应用于基因组模拟等知识密集型任务
tldr: 基因组规模代谢模型（GEM）需要计算专业知识，限制了其广泛应用。ChatGEM基于多智能体ADEPT框架，集成COBRApy和检索增强生成（RAG）架构，通过自然语言交互实现GEM模拟。在三个复杂度递增的任务中，RAG使代码生成平均性能从2.63提升至4.20，并显著缩短执行时间。应用于恶臭假单胞菌工程菌株的酶约束GEM，识别出组成型菌株为琥珀酸超产最佳底盘，与实验一致。ChatGEM降低了代谢建模门槛，加速科学发现。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1533, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1733, \"height\": 1237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1723, \"height\": 1346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1725, \"height\": 1969, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1757, \"height\": 1626, \"label\": \"Table\"}]"
motivation: 降低基因组规模代谢模型使用门槛，使无计算专长的研究者也能通过自然语言进行交互式模拟。
method: 基于ADEPT多智能体框架，结合COBRApy与检索增强生成（RAG）架构，通过专用智能体协调代码生成与执行。
result: RAG使平均性能评分从2.63提升至4.20，复杂任务执行时间显著减少；成功预测琥珀酸超产最佳底盘菌株。
conclusion: ChatGEM通过自然语言交互实现GEM模拟，推动代谢建模的民主化，加速科学发现。
---

## 摘要
基因组规模代谢模型（GEM）是预测细胞表型和指导微生物菌株工程的有力工具，但由于需要计算专业知识，其广泛应用仍具有挑战性。为克服这一障碍，我们提出了ChatGEM，这是一个代理平台，可以通过自然语言实现交互式GEM模拟。基于多代理ADEPT框架，ChatGEM将COBRApy集成到检索增强生成（RAG）架构中，通过专门代理协调代码生成与执行。在三个复杂度递增的任务上进行基准测试表明，启用RAG的代码生成将平均总体性能得分从2.63提高到4.20，同时从常规任务到复杂任务显著减少了执行时间。使用酶约束GEM（ecGEM）对四种工程化恶臭假单胞菌KT2440菌株应用ChatGEM，通过琥珀酸泄漏指数鉴定组成型菌株为琥珀酸过量生产的最佳底盘——这一预测得到了实验验证。因此，ChatGEM通过使缺乏计算专业知识的研究人员能够通过自然语言执行基于GEM的复杂分析，从而民主化代谢建模，进而加速科学发现。

## Abstract
Genome-scale metabolic models (GEMs) are powerful tools for predicting cellular phenotypes and guiding microbial strain engineering, yet broad adoption remains challenging due to the computational expertise required. To overcome that, we present ChatGEM, an agentic platform that enables interactive GEM simulation through natural language. Built on the multi-agent ADEPT framework, ChatGEM integrates COBRApy within a retrieval-augmented generation (RAG) architecture that coordinates code generation and execution through specialized agents. Benchmarking across three tasks of increasing complexity showed that RAG-enabled code generation improved the mean overall performance score from 2.63 to 4.20 while reducing the execution time significantly starting from routine to complex tasks. Application of ChatGEM using an enzyme-constrained GEM (ecGEM) for four engineered Pseudomonas putida KT2440 strains identified the constitutive strain as the optimal chassis for succinate overproduction using a succinate leakage index - a prediction observed experimentally. Therefore, ChatGEM democratizes metabolic modeling by enabling researchers without computational expertise to perform sophisticated GEM-based analyses through natural language, and, hence, accelerating scientific discovery.