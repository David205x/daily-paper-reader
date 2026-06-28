---
title: Client-server interfaces enable efficient agent-driven variant calling
title_zh: 客户端-服务器接口实现高效代理驱动变异检测
authors: "Yu, X., Zheng, Z., CHEN, L., QIn, Z., Guo, X., He, M., Luo, R."
date: 2026-06-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734665v1.full.pdf"
tags: ["query:rl"]
score: 8.0
evidence: 通过客户端-服务器接口实现LLM智能体自动化变异调用
tldr: "现有生物信息学工具主要为人类专家设计，LLM agent使用它们需大量对话和token，效率低下。本研究将深度学习变体识别工具Clair3重构为客户端-服务器系统Clair3-Connect，客户端暴露schema定义的agent工具，通过单次结构化调用即可完成任务。在APOE分型任务上，60次agent运行全部正确，token消耗比shell驱动基线减少6.8-14倍，运行时间约四分之一，且token使用波动仅4%而非35%。尽管丢弃pileup和phasing阶段导致SNP F1下降0.1-0.3，但整体效果显著。结论认为，将算法重构为开发者构建的agentic接口应成为生物信息学工具开发的一等交付物。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有生物信息学工具接口为人类设计，LLM agent需大量沟通和token才能使用，导致效率低、可靠性差。
method: 将Clair3重构为客户端-服务器系统，客户端处理基因组分析并暴露结构化agent工具，服务器仅做神经网络推理，通过TLS和AES-256加密通信。
result: "APOE分型任务中，60次agent运行全正确，token消耗降低6.8-14倍，时间减少约75%，token使用波动仅4% vs 35%，SNP F1仅下降0.1-0.3。"
conclusion: 应将军工级agentic接口作为生物信息学工具开发的核心交付物，而非简单包装，以提升效率和可靠性。
---

## 摘要
背景：大语言模型（LLM）代理越来越多地自动化生物信息学分析，但大多数现有的生物信息学工具是为人类专家单独使用而构建的。驱动此类工具的代理必须从面向人类的文档中推理其安装、配置和执行，每个结果需要多次交互、大量令牌和函数调用。因此，方法如何暴露给代理可能与方法本身同样重要。通过为这些工具设计代理接口，代理可以减少此类开销并提高代理驱动分析的可靠性。发现：为了测试这一设计，我们将广泛使用的基于深度学习的长读长变异检测器Clair3重新架构为客户端-服务器系统Clair3-Connect。客户端执行所有基因组学相关处理并持有可识别数据。服务器仅运行神经网络推理，客户端仅向服务器发送特征张量，而样本标识符和基因组上下文保留在客户端。客户端暴露由模式定义的面向代理的工具，代理通过单个结构化调用调用这些工具。在一个APOE单倍型分型任务中，所有60次代理运行均正确。代理工具在3次交互中使用12K令牌，比基于shell的基线（81K-163K令牌）少6.8至14倍，耗时约为四分之一，且稳定性更高（令牌使用变异4%对比35%）。为保持客户端轻量化而省略pileup和phasing阶段，在50×覆盖度下，SNP F1值仍处于标准Clair3的0.1-0.3个点范围内，而双向TLS和AES-256-GCM加密使端到端运行时间增加7.2%。结论：将成熟算法重新构建为开发者构建的、位于安全客户端-服务器边界后的代理工具，使其比第三方封装器更高效、更可靠且更易于LLM代理部署——第三方封装器无法恢复只有其开发者知道的默认值和约定。代理接口应成为生物信息学工具开发的一等交付物。

## Abstract
Background: Large language model (LLM) agents increasingly automate bioinformatics analyses, but most existing bioinformatics tools were built for standalone use by human experts. An agent driving such a tool must reason about its installation, configuration, and execution from documentation for human, spending many turns, tokens, and tool calls per result. How a method is exposed to an agent can therefore matter as much as the method itself. By designing agentic interfaces for these tools, agent can reduce such overhead and improve the reliability of agent-driven analyses. Findings: To test this design, we re-architected Clair3, a widely used deep-learning-based long-read variant caller, into a client-server system, Clair3-Connect. The client performs all genomics related processing and holds the identifiable data. The server runs only neural-network inference, and the client sends only feature tensors to the server, while sample identifiers and genomic context remain on the client. The client exposes schema-defined agent-facing tools that an agent invokes through single structured calls. On an APOE diplotyping task, all 60 agent runs were correct. The agentic tools used 12K tokens in 3 turns, 6.8 to 14 times fewer tokens than the shell-driven baselines (81K-163K tokens), at about a quarter the wall-clock time and far more stably (4% versus 35% token usage variation). Dropping the pileup and phasing stages to keep the client light left SNP F1 within 0.1-0.3 points of standard Clair3 by 50x coverage, while mutual TLS and AES-256-GCM encryption added 7.2% to end-to-end runtime. Conclusions: Recasting an established algorithm as developer-built, agentic tools behind a secure client-server boundary makes it more efficient, reliable, and easier to deploy for an LLM agent than a third-party wrapper, which cannot recover the defaults and conventions only its developers know. Agentic interfaces should be a first-class deliverable of bioinformatics tool development.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大语言模型（LLM）代理越来越多被用于自动化生物信息学分析，但现有生物信息学工具原本为人类专家单独使用而设计。代理需要使用面向人类的文档推理安装、配置和执行，导致每项任务需要多次交互、大量 token 和函数调用，效率极低且可靠性差。
- **整体含义**：方法如何暴露给代理可能与方法本身同等重要。设计专门的“代理接口”可以显著降低开销、提升稳定性和可部署性，从而改变生物信息学工具的开发范式——代理接口应成为工具的一等交付物，而非事后包装。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将现有深度学习变体检测工具 Clair3 重构为客户端‑服务器架构（Clair3‑Connect），使 LLM 代理通过结构化、单次调用的工具接口完成任务，避免零碎的 shell 命令和文档推理。
- **关键技术细节**：
  - **客户端**：执行所有基因组相关处理（如读取处理、特征提取），持有可识别数据（样本标识符、基因组上下文），暴露由模式（schema）定义的面向代理的工具。
  - **服务器**：仅运行神经网络推理，接收来自客户端的特征张量，不接触原始样本数据。
  - **通信安全**：使用双向 TLS 和 AES‑256‑GCM 加密。
  - **代理交互**：代理通过单个结构化调用（如函数调用）调用客户端暴露的工具，仅需 3 次交互即可完成任务，比 shell 驱动方式减少大量来回通信。
- **省略阶段**：为保持客户端轻量，丢弃了原始 Clair3 中的 pileup 和 phasing 阶段。

## 3. 实验设计：数据集、场景、基准与对比方法
- **任务/场景**：APOE 单倍型分型任务（APOE diplotyping）。
- **数据集**：未具体说明样本来源，但覆盖度提到 50×，应为长读长测序数据（与 Clair3 目标一致）。
- **基准（Benchmark）**：标准 Clair3（原始全流程）作为性能基准（SNP F1 对比）。
- **对比方法**：
  - **基于 shell 驱动的基线**：代理通过传统 shell 命令调用 Clair3，需大量 token 和交互。
  - **Clair3‑Connect 代理工具**：通过客户端‑服务器接口的代理工具。
- **评价指标**：token 消耗、交互轮数、运行时间、稳定性（token 使用变异系数）、准确性（SNP F1）。

## 4. 资源与算力
- **论文未明确说明** GPU 型号、数量、训练时长等硬件细节。
- 仅提及端到端运行时间（代理工具约为 shell 基线的四分之一）以及加密带来的 7.2% 额外时间开销。
- 原始 Clair3 的训练资源未在本文讨论范围内。

## 5. 实验数量与充分性
- **实验数量**：一个主要任务（APOE 分型），进行了 **60 次 agent 运行**（全部正确）；对比了三种 shell 驱动基线（可能对应不同设置）。
- **充分性分析**：
  - **正面**：60 次重复运行提供了统计稳定性，token 和时间的变异系数报告明确（4% vs 35%），证据充分。
  - **不足**：仅测试单一任务（APOE 分型），未在其他变体检测任务（如全基因组 SNP/INDEL）上验证；未与其他代理接口方案（如第三方包装器）直接对比；舍弃 pileup 和 phasing 的影响只在 50×覆盖度下评估，缺乏多覆盖度消融。
  - **客观性**：实验设计直接，指标合理，但缺乏更广泛的跨任务通用性验证，因此结论的泛化能力有限。

## 6. 论文的主要结论与发现
- **效率提升**：代理工具使用 12K token、3 次交互完成任务；shell 基线使用 81K‑163K token，降低 **6.8–14 倍**。
- **速度提升**：运行时间约为 shell 基线的 **四分之一**。
- **稳定性提升**：token 使用变异系数仅 4%，而 shell 基线达 35%。
- **准确性**：在 50×覆盖度下，SNP F1 值仅下降 0.1–0.3 个百分点（因舍弃 pileup 和 phasing）。
- **安全性**：加密仅增加 7.2% 时间，可接受。
- **最终结论**：将成熟算法重构为开发者构建的、位于安全客户端‑服务器边界后的 agentic 工具，比第三方封装器更高效、更可靠、更易部署；代理接口应成为生物信息学工具开发的一等交付物。

## 7. 优点：方法或实验设计上的亮点
- **设计创新**：客户端‑服务器分离，客户端负责基因组处理并暴露结构化工具，服务器仅做推理，既保护数据隐私（样本标识符留在客户端）又降低代理认知负担。
- **效率突出**：单次结构化调用代替多轮 shell 交互，token 消耗降低一个数量级，时间减少 75%。
- **稳定性好**：token 使用变异仅 4%，远低于 shell 驱动方式，代理行为可预测。
- **安全性内置**：双向 TLS + AES‑256‑GCM 加密通信，适应敏感基因组数据场景。
- **实验设计合理**：60 次重复运行、明确的对比基线、报告变异系数等统计指标，证据扎实。

## 8. 不足与局限
- **任务覆盖单一**：仅测试 APOE 分型，未验证其他变体检测任务（如全基因组、INDEL、SV）或不同测序平台。
- **准确性有损**：因轻量化舍弃 pileup 和 phasing，SNP F1 下降 0.1–0.3 点，虽小但不可忽略；在较低覆盖度下损失可能更大（未测试）。
- **未与其他代理接口方案对比**：仅与 shell 驱动基线对比，未与类似“工具封装器”（如 LangChain 工具）对比，无法证明其优于所有第三方封装。
- **通用性依赖开发者**：该方法要求工具原开发者从头重构架构，第三方难以复制（因为恢复默认值和约定需要开发者知识），推广成本高。
- **算力资源未报告**：缺少 GPU 类型、数量、训练 / 推理硬件细节，可复现性不足。
- **消融实验不全**：未系统分析省略每个阶段对准确性的具体影响，仅给出了整体结果。

（完）
