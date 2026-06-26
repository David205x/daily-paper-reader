---
title: "VFB-MCP: Natural-Language Access to Drosophila Neuroscience Grounded by an Expert-Curated Ontology-Led Knowledgebase"
title_zh: VFB-MCP：基于专家策划本体驱动知识库的果蝇神经科学自然语言访问
authors: "McLachlan, A. D., Court, R., Pilgrim, C., Longden, K., Brown, N. H. D., Osumi-Sutherland, D., Jefferis, G. S. X. E., Armstrong, D. J."
date: 2026-06-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.16.732577v1.full.pdf"
tags: ["query:rl"]
score: 6.0
evidence: 利用大语言模型和模型上下文协议自然语言访问果蝇知识库
tldr: 生物数据库的复杂查询需要专业知识，形成新用户使用障碍。VFB-MCP通过模型上下文协议将大型语言模型连接到专家策划的本体知识库Virtual Fly Brain，实现自然语言访问果蝇神经科学数据。在30个任务上，VFB-MCP的LLM在25个任务中产生精确、可验证的量化答案，远超裸LLM和网页搜索辅助。该工作展示了MCP结合本体知识图谱提升LLM在神经科学和连接组学数据查询准确性的有效性。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统数据库查询需要专业知识，阻碍新用户探索果蝇神经科学数据，尤其是连接组学数据。
method: 通过模型上下文协议（MCP）将LLM连接到专家策划的本体知识库VFB，实现自然语言查询。
result: "在30个神经科学任务上，VFB-MCP的LLM在25个任务中产生精确答案，优于裸LLM（2/30）和网页搜索（14/30），量化任务优势显著（89% vs 11%）。"
conclusion: MCP结合本体知识图谱是提升LLM在神经科学和连接组学数据查询响应质量的有效方法。
---

## 摘要
生物数据库存储经过策划的知识，研究人员传统上通过网页界面或API访问这些知识。要超越随意浏览，需要特定领域的知识和专业知识来构建探索这些数据所需的查询。这对于正在经历范式转变的科学领域的新用户来说构成了障碍。通过模型上下文协议（MCP）将这些数据库暴露给大型语言模型（LLM）可以实现自然语言访问，这是一种潜在的访问性解决方案。我们为虚拟果蝇大脑（VFB）实现了这一点，VFB是一个专家策划、本体支持的知识库，用于果蝇神经科学，提供了使最近整合的连接组可访问所需的精度。在30项神经科学任务上，与裸LLM和网页搜索辅助LLM进行基准测试，配备VFB-MCP的LLM在25/30任务上产生了精确、可验证且适当量化的答案，而网页为14/30，裸LLM为2/30（Wilcoxon p<0.01，Holm校正，所有成对比较）。对于需要数据量化的任务，MCP的优势最大（89% vs 网页的11%）。这项工作确立了基于本体支持的知识图谱的MCP作为提高LLM在神经科学和连接组学数据响应质量的有效方法。

## Abstract
Biological databases store curated knowledge that researchers traditionally access through web interfaces or APIs. To move beyond casual browsing requires domain-specific knowledge and expertise to frame the queries necessary to explore this data. This generates a barrier for new users in scientific fields undergoing paradigm shifts. Exposing these databases to large language models (LLMs) via the Model Context Protocol (MCP) enables natural-language access, a potential accessibility solution. We implement this for Virtual Fly Brain (VFB), an expert-curated and ontology-backed knowledgebase of Drosophila neuroscience, providing the precision needed to make recently-integrated connectomes accessible. Benchmarked on 30 neuroscience tasks against a bare LLM and a web-search-assisted LLM, the VFB-MCP-equipped LLM produces precise, verifiable and appropriately quantified answers on 25/30 tasks vs 14/30 for web and 2/30 for bare (Wilcoxon p<0.01, Holm-corrected, all pairwise comparisons). The MCP advantage is largest for tasks where data quantification is required (89% vs 11% web). This work establishes MCP over ontology-backed knowledge graphs as an effective method to improve LLM response quality for neuroscience and connectomics data.