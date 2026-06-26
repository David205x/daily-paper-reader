---
title: "F.A.D.E. (Fully Agentic Drug Engine): A Conversational AI Platform for Drug Discovery"
title_zh: F.A.D.E.（全代理药物引擎）：面向药物发现的对话式AI平台
authors: "Kantorow, J., Mani, N., Mohanraj, N. R., Zong, X."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.20.733481v1.full.pdf"
tags: ["query:rl"]
score: 8.0
evidence: 使用大语言模型智能体进行药物发现的多智能体平台
tldr: 药物发现成本高、周期长，现有计算工具碎片化且使用门槛高。F.A.D.E.平台基于多智能体架构，将自然语言查询自动转化为候选药物，集成结构预测、结合口袋检测、等变扩散配体生成与亲和力评估。在EGFR和CRBP1靶点上验证，生成化合物的QED得分达0.85，显著优于共晶参考配体的0.46。该平台大幅降低计算药物发现的专业壁垒，能可靠生成类药小分子。
source: biorxiv
selection_source: fresh_fetch
motivation: 降低药物发现中计算工具的使用门槛，让无深度交叉学科背景的研究者也能通过自然语言生成候选药物。
method: 采用三分支层级架构，根据蛋白结构数据可用性自适应选择路径，整合结构预测、结合口袋检测、等变扩散配体生成及结合亲和力评估。
result: 在EGFR靶点上，生成配体QED得分0.85（参考配体0.46），CRBP1靶点同样生成化学可处理的类药分子。
conclusion: F.A.D.E.作为开源多智能体平台，可高效将自然语言转化为类药候选物，显著降低计算药物发现门槛。
---

## 摘要
药物发现仍是制药流程中成本最高、耗时最长的环节之一，平均每种药物的研发成本超过23亿美元，研发周期长达十多年，且临床试验失败率超过90%。尽管计算方法已扩展了可搜索的化学空间，但当前流程仍碎片化，且缺乏深度跨学科专业知识的研究人员难以使用。本文提出F.A.D.E.（全代理药物引擎），一个多代理、开源平台，能将自然语言查询转化为潜在候选药物，大幅降低进入先进计算药物发现领域的专业壁垒。F.A.D.E.采用三分支分层架构，能根据任何蛋白质靶点的可用结构数据水平自适应调整，将结构预测、结合口袋检测、基于等变扩散的从头配体生成以及结合亲和力估计集成到单一自动化流程中。我们在两个结构不同的靶点上验证了F.A.D.E.：表皮生长因子受体激酶结构域（EGFR，一个成熟的肿瘤靶点）和细胞视黄醇结合蛋白1（CRBP1，一种参与类视黄醇代谢的脂质结合蛋白）。对于EGFR，我们生成的候选药物的QED分数达到0.85，而共结晶参考配体为0.46，表明预测的药物相似性显著改善。两个靶点的结果均证实，F.A.D.E.能从简单的自然语言输入中可靠地生成化学上易处理的、类药性高的先导化合物，覆盖不同蛋白质类别。

## Abstract
Drug discovery remains one of the costliest and most time-intensive endeavors in the pharmaceutical pipeline, with average development costs exceeding $2.3 billion per drug, timelines spanning more than a decade, and attrition rates above 90% in clinical trials. While computational methods have expanded the searchable chemical space, current pipelines remain fragmented and largely inaccessible to researchers without deep interdisciplinary expertise. Here we present F.A.D.E. (Fully Agentic Drug Engine), a multi-agent, open-source platform that converts natural language queries into potential drug candidates, substantially lowering the expertise barrier to advanced computational drug discovery. F.A.D.E. employs a three-branch hierarchical architecture that adapts to the level of available structural data for any protein target, integrating structure prediction, binding pocket detection, equivariant diffusion-based de novo ligand generation, and binding affinity estimation into a single automated pipeline. We validate F.A.D.E. on two structurally distinct targets: the epidermal growth factor receptor kinase domain (EGFR), a well-established oncology target, and cellular retinol-binding protein 1 (CRBP1), a lipid-binding protein involved in retinoid metabolism. For EGFR, our generated candidates achieved QED scores of 0.85 compared to 0.46 for the co-crystallised reference ligand, demonstrating marked improvement in predicted drug-likeness. Results across both targets confirm that F.A.D.E. can reliably generate chemically tractable, drug-like hit compounds across diverse protein classes from simple natural language input.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：药物发现成本高昂（单药平均超23亿美元）、周期漫长（超过10年）、临床失败率高（>90%）。现有的计算方法虽然扩展了化学空间，但流程碎片化，且需要深厚的跨学科专业知识，导致广大研究人员难以使用。  
- **整体含义**：本文旨在通过构建一个多智能体、开源平台F.A.D.E.，将自然语言查询自动转化为候选药物分子，显著降低计算药物发现的进入门槛，实现“端到端”的自动化药物设计。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用**三分支层级架构**，根据目标蛋白的结构数据可用性自适应选择路径，集成多个先进工具，形成一个完整的自动化流水线。  
- **关键技术细节**：
  - **三分支架构**：
    - **分支1**：当存在高分辨率（<3.0 Å）的配体-蛋白共晶结构时，直接提取实验结合位点，然后进行从头配体生成。
    - **分支2**：当只有无配体的蛋白结构时，使用**fpocket**计算结合口袋，再进行配体生成。
    - **分支3**：当没有任何实验结构时，从UniProt获取序列，用**Boltz-2**预测结构，再用fpocket识别口袋，最后配体生成。
  - **配体生成**：使用**DiffSBDD**（一种基于等变扩散的结构药物设计模型），以结合口袋几何为条件生成新配体。
  - **候选筛选与排序**：生成的分子经过多指标过滤（QED ≥ 0.5、SA ≤ 6、Tanimoto相似度<0.85、化学有效性、唯一性），然后按QED、SA和Boltz-2预测的结合亲和力排序。
  - **结合亲和力预测**：使用**Boltz-2**联合预测蛋白-配体复合物的三维结构和结合亲和力。
- **算法流程**（文字说明）：
  1. 用户输入自然语言查询 → 代理解析目标。
  2. 分层数据库搜索（RCSB PDB → UniProt + Boltz-2→ fpocket）确定分支。
  3. 根据分支获取/计算结合位点坐标。
  4. 使用DiffSBDD基于结合位点生成多个候选小分子。
  5. 对候选分子进行多指标过滤和排序。
  6. 输出排名靠前的候选分子及属性。

## 3. 实验设计：数据集/场景、基准、对比方法

- **实验场景**：选取了两个结构不同的蛋白靶点：
  - **EGFR（表皮生长因子受体激酶结构域）**：已知多结构，使用分支1（共晶结构PDB ID: 4G5J）。
  - **CRBP1（细胞视黄醇结合蛋白1）**：无高分辨共晶结构，使用分支2（apo结构PDB ID: 5H9A）。
- **基准**：将生成候选的QED、SA、预测结合亲和力与共晶参考配体（EGFR: 0WN, 0WM；CRBP1: 内置参考）进行比较。
- **对比方法**：论文未进行与其他方法的直接对比，而是定性讨论了与ChemCrow、DrugAgent、AgentD、Prompt-to-Pill的区别，强调F.A.D.E.的独特优势（多分支、开源、物理基础工具集成）。

## 4. 资源与算力

- **未明确说明**：论文未提及训练模型所使用的GPU型号、数量、训练时长等具体算力资源。仅提到使用了DiffSBDD（预训练模型）和Boltz-2（预训练模型），未说明推理时的硬件配置。

## 5. 实验数量与充分性

- **实验数量**：仅做了两个靶点的案例验证（EGFR和CRBP1），每个靶点生成10个候选分子并展示前几名。无大规模消融实验或对比实验。
- **充分性评价**：实验覆盖了分支1和分支2，但分支3未实际验证（论文说明分支3尚未完成，是“immediate next step”）。仅两个靶点，覆盖性有限，缺乏对更多靶点类型（如GPCR、离子通道）的测试。未进行合成实验或体外验证。整体实验偏初步，充分性不足，但作为预印本可接受。

## 6. 论文的主要结论与发现

- F.A.D.E.能够可靠地将自然语言查询转化为类药候选分子，QED得分显著提升（EGFR: 生成配体0.85 vs 参考0.46）。
- 生成的候选分子具有结构新颖性（Tanimoto相似度低于0.85），且能探索不同化学空间区域。
- 在CRBP1上，fpocket成功识别多个可药性口袋（包括已知主要结合口袋），并生成多个结合位点的候选分子，展示了多口袋探索能力。
- 平台开源（GitHub），降低专业壁垒，可扩展性强。

## 7. 优点：方法或实验设计上的亮点

- **自然语言界面**：将复杂计算流程简化为对话式交互，极大降低使用门槛。
- **三分支自适应架构**：根据数据可用性自动选择最优路径，覆盖从高到低结构信息场景，鲁棒性强。
- **集成开源物理工具**：采用Boltz-2、DiffSBDD、fpocket等公开工具，确保可复现性和可扩展性。
- **多指标联合筛选**：结合QED、SA、结合亲和力，避免单一指标偏倚。
- **代码开源**：社区可参与改进，促进合作。

## 8. 不足与局限

- **分支3未验证**：论文承认分支3（基于序列预测结构）尚未完成，目前仅覆盖分支1和2，限制了在无结构靶点上的适用性。
- **实验规模小**：仅两个靶点，缺乏消融实验、与基线方法的系统对比，实验充分性不足。
- **结合亲和力预测弱**：生成配体的预测结合亲和力弱于参考配体（可能因优化方向偏向类药性而非亲和力），论文解释为初始先导优化步骤，但未展示后续优化方法。
- **合成可行性未实验验证**：SA分数中等（~4.0），但未经合成可行性实际测试。
- **未包含实验验证**：无细胞实验或动物实验数据，仅限于计算预测。
- **算力与效率未报告**：缺乏推理耗时等实际性能数据。

（完）
