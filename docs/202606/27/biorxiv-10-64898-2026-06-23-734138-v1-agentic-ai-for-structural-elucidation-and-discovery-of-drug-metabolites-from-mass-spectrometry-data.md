---
title: Agentic AI for Structural Elucidation and Discovery of Drug Metabolites from Mass Spectrometry Data
title_zh: 代理型AI用于质谱数据中药物代谢物的结构解析与发现
authors: "Wang, X., Patan, A., Zhao, H. N., Charron-Lamoureux, V., Shin, Y., Petras, D., Hong, Y., Bowen, B. P., Northen, T. R., Dorrestein, P. C., Wang, M."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.23.734138v1.full.pdf"
tags: ["query:rl"]
score: 8.0
evidence: 基于LLM的智能体系统，自动进行代谢物结构解析与发现
tldr: 多数质谱信号的结构未知，大语言模型（LLM）可生成新结构但存在幻觉。本文构建GNPS2智能体系统，结合谱图对齐、分子式推断、结构枚举、谱图预测和专家自然语言假设，自动生成分析流程。系统从公共数据中注释了磷酸化羟嗪、对乙酰氨基酚-对香豆酸酯等新代谢物，并发现两个氧化布洛芬-肉碱结合物，经实验验证。结果表明LLM驱动推理与领域知识结合可生成可测试的新结构假设。
source: biorxiv
selection_source: fresh_fetch
motivation: 绝大多数代谢组学质谱信号结构未定义，需利用LLM生成能力提出从未描述分子结构，但需约束幻觉并实现验证。
method: 开发GNPS2智能体系统，集成谱图对齐、分子式推断、规则结构枚举、机器学习谱图预测和自然语言专家假设，动态生成分析工作流。
result: 从公共数据预测并实验确认了磷酸化羟嗪、对乙酰氨基酚-对香豆酸酯酯及两个新氧化布洛芬-肉碱结合物。
conclusion: LLM驱动的智能体推理结合领域工具可生成可测试的结构假设，实现未知代谢物发现。
---

## 摘要
公共代谢组学数据库中检测到的大部分化学信号仍未被结构鉴定。大型语言模型（LLM）是概率性系统，其生成超出训练数据的能力（这可能导致幻觉）也使其适用于假设那些从未被描述过的分子结构。我们旨在构建一个系统，能够利用LLM的生成能力，结合领域特定工具/框架来约束幻觉并产生经过验证的发现。我们开发了一个GNPS2代理型AI系统，通过整合光谱对齐、分子式推断、基于规则的结构枚举、基于机器学习的谱图预测，并将领域专家的自然语言假设转化为动态生成的分析工作流，从而解释LC-MS/MS数据。我们展示了在化学假设引导下，从公共数据中注释未知药物代谢物的过程。该代理预测了磷酸化的羟嗪、对乙酰氨基酚-对香豆酸酯，并通过实验确认，同时从公共数据库中鉴定出两种新的氧化布洛芬-肉碱结合物。这些结果表明，LLM驱动的代理推理与领域专业知识相结合，确实能够利用跨库数据生成先前未表征代谢物的可实验验证的结构假设。

## Abstract
The majority of chemical signals detected in public metabolomics repositories remain structurally undefined. Large language models (LLMs) are probabilistic systems whose capacity to generate outputs beyond their training data, which can cause hallucinations, makes them also potentially suited to hypothesize structures for molecules that have never been described. We aimed to build a system that could harness this LLM generative capacity combined with domain specific tools/framework to constrain hallucination and produce validated discoveries. We developed a GNPS2 agentic AI system that interprets LC-MS/MS data by integrating spectral alignment, molecular formula inference, rule-based structural enumeration, machine learning-based spectrum prediction, and translates natural language hypotheses from domain experts into dynamically generated analytical workflows. We demonstrate the annotation of unknown drug metabolites from public data guided by chemical hypotheses. The agent predicted, and we experimentally confirmed, a phosphorylated hydroxyzine, an acetaminophen-p-coumaric acid ester, and identified two new oxidative ibuprofen-carnitine conjugates from public repositories. These results demonstrate that LLM-driven agentic reasoning, when combined with domain expertise, can indeed generate experimentally testable structural hypotheses for previously uncharacterized metabolites leveraging pan repository data.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：公共代谢组学数据库中绝大多数质谱信号（MS/MS）的结构未知，传统方法难以对从未描述过的分子进行结构解析。大语言模型（LLM）虽然具备生成新结构的能力，但其“幻觉”问题导致生成结果不可靠，需要约束和验证机制。
- **研究动机**：利用LLM的生成能力提出新分子结构假设，同时结合领域专用工具（谱图对齐、分子式推断、结构枚举、谱图预测等）限制幻觉，实现从公共数据中发现并验证未知药物代谢物。
- **整体含义**：提出一种“LLM驱动的代理推理 + 领域专业知识”的范式，使机器能够自主生成可实验验证的结构假设，从而加速代谢组学中的化合物发现。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：构建一个名为GNPS2的代理型AI系统，通过集成多个分析工具并利用LLM（如GPT系列）进行推理决策，动态生成分析工作流，自动注释质谱数据中未知代谢物的结构。
- **关键技术细节**：
  - **谱图对齐**：将实验MS/MS谱图与数据库或预测谱图进行比对。
  - **分子式推断**：基于精确质量同位素分布推断候选分子式。
  - **基于规则的结构枚举**：利用化学规则（如官能团、代谢反应规则）生成可能的结构候选。
  - **基于机器学习的谱图预测**：使用模型（如CFM-ID、SIRIUS等）预测候选结构的碎裂谱。
  - **自然语言假设转化**：将领域专家的假设（以自然语言描述，如“该代谢物可能为磷酸化形式”）转化为可执行的分析步骤。
  - **LLM智能体**：负责协调上述工具，根据结果不确定性动态调整工作流，生成最终结构假设。
- **算法流程（文字说明）**：
  1. 输入未知MS/MS谱图。
  2. 智能体调用谱图对齐，若匹配到已知结构则输出；否则进入下一步。
  3. LLM基于专家假设或规则生成候选分子式/子结构。
  4. 使用分子式推断和结构枚举生成候选结构列表。
  5. 使用ML谱图预测生成候选谱图，与实验谱图相似度评分。
  6. 智能体综合所有证据，输出最可能的候选结构，并给出置信度。
  7. 返回结果供实验验证。

### 3. 实验设计：数据集、基准、对比方法
- **数据集**：主要使用**公共代谢组学数据**（未明确具体库，推测为GNPS、MassIVE等），具体案例包括：
  - 磷酸化羟嗪（hydroxyzine）的代谢物
  - 对乙酰氨基酚-对香豆酸酯（acetaminophen-p-coumaric acid ester）
  - 两种新的氧化布洛芬-肉碱结合物（oxidative ibuprofen-carnitine conjugates）
- **基准（benchmark）**：未明确设立传统benchmark，而是通过**实验验证**（合成标准品或体内外实验）确认代理系统提出的结构假设是否正确。
- **对比方法**：未提及与其他方法（如SIRIUS、GNPS经典流程）的定量对比，主要是展示代理系统能发现先前未被注释的结构。

### 4. 资源与算力
- 论文**未明确说明**使用的GPU型号、数量或训练时长。可能依赖于调用云端的LLM API（如OpenAI GPT-4）以及本地运行的工具（如结构枚举、谱图预测模型），但未提供具体算力信息。

### 5. 实验数量与充分性
- **实验数量**：主要展示了**3个案例**（磷酸化羟嗪、对乙酰氨基酚-对香豆酸酯、两个氧化布洛芬-肉碱共轭物），其中后两个属于同一类（布洛芬-肉碱）。数量较少，仅作为概念验证。
- **充分性**：不够充分。缺乏系统性的消融实验（如去掉某一工具后性能变化）、大规模数据集测试（如从公共数据中随机抽取未知谱图）或与现有方法的定量比较。但论文强调了“从公共数据中发现并通过实验确认”，验证了可行性，对于一篇方法学预印本尚可接受。
- **客观性/公平性**：未建立公平的对比基准，因此难以评估方法在通用场景下的优势。

### 6. 论文的主要结论与发现
- LLM驱动的代理AI系统（GNPS2）能够结合领域工具约束幻觉，从公共质谱数据中自动生成可测试的结构假设。
- 成功发现了磷酸化羟嗪、对乙酰氨基酚-对香豆酸酯这两种未知药物代谢物，并获得了实验确认。
- 从公共存储库中鉴定出两种新的氧化布洛芬-肉碱结合物，进一步验证了方法对不同药物代谢类型（氧化、偶联、磷酸化）的适用性。
- 结论：综合LLM推理和领域知识，能够利用跨库数据生成先前未表征代谢物的实验可验证假设。

### 7. 优点：方法或实验设计上的亮点
- **创新性**：首次将LLM智能体与多种质谱分析工具深度集成，通过自然语言假设驱动分析流程，实现了自动化结构发现。
- **可解释性**：每个步骤的推理过程可由LLM解释，且最终输出结构假设可通过实验验证，增加了可信度。
- **实用性**：直接利用公共数据，无需额外湿实验数据即可提出新发现，降低了代谢组学中未知物鉴定的门槛。
- **灵活性**：能够整合专家假设（自然语言），将人类知识融入AI工作流。

### 8. 不足与局限
- **实验覆盖有限**：仅测试了3个案例，且均为药物代谢物，未涵盖更广泛的天然产物、环境污染物等，通用性存疑。
- **缺乏消融和对比实验**：未评估单独使用某一工具或去除LLM时的性能，也未与SIRIUS、GNPS经典流程等对比，难以证明代理系统的优势来源。
- **幻觉问题仍存在**：虽然通过工具约束，但LLM生成的假设质量高度依赖提示词和训练数据，潜在错误结构可能被误判为合理。
- **计算成本未评估**：未报告每次分析所需的LLM调用次数、时间或API费用，对实际部署的成本不清晰。
- **可重复性**：由于依赖外部API和特定数据库版本，代码和完整工作流未公开或难以精确复现（论文可能尚未提供代码）。
- **依赖专家假设**：在案例中提到了采用专家假设引导，意味着对于完全未知的化合物（无任何线索），系统性能可能下降。

（完）
