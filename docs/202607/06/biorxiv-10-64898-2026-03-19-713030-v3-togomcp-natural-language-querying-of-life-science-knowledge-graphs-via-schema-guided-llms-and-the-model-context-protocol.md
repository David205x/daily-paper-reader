---
title: "TogoMCP: Natural Language Querying of Life-Science Knowledge Graphs via Schema-Guided LLMs and the Model Context Protocol"
title_zh: TogoMCP：通过模式引导的大语言模型与模型上下文协议对生命科学知识图谱进行自然语言查询
authors: "Kinjo, A. R., Yamamoto, Y., Bustamante-Larriet, S., Labra-Gayo, J. E., Fujisawa, T."
date: 2026-07-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.19.713030v3.full.pdf"
tags: ["query:rl"]
score: 9.0
evidence: 使用LLM进行知识图谱查询的RAG系统
tldr: "生命科学知识图谱RDF Portal查询需要SPARQL和模式知识，多数研究者难以使用。TogoMCP通过模型上下文协议(MCP)将LLM作为推理引擎，利用MIE文件提供动态模式上下文，并采用实体解析与模式引导的SPARQL生成两阶段流程。在50个生物学问题上，相比无辅助基线提升显著（Cohen's d=1.82），胜率超80%。消融实验表明MIE模式文件是最大贡献因素，单条指令加载即可恢复平均改进，而程序性指导降低方差。结论：简洁动态的模式上下文比复杂编排更关键。"
source: biorxiv
selection_source: fresh_fetch
motivation: 查询生命科学知识图谱需要专业SPARQL和模式知识，阻碍非专家使用，需自动将自然语言转为可执行查询。
method: TogoMCP利用LLM通过MCP协议编排专用工具，使用YAML格式MIE文件动态提供数据库模式上下文，两阶段分离实体解析与SPARQL生成。
result: "在50个生物学问题上，TogoMCP相比基线大幅提升（Cohen's d=1.82），胜率超80%，MIE文件贡献最大（△=+0.50）。"
conclusion: 简洁动态的模式上下文比复杂编排更关键，程序性指导可减少性能方差，为知识图谱自然语言查询提供设计原则。
---

## 摘要
查询由DBCLS维护的RDF Portal知识图谱（聚合了约60个生命科学数据库）需要精通SPARQL和特定于数据库的RDF模式，这使得大多数研究人员难以利用这一资源。大型语言模型（LLM）原则上可以将自然语言问题翻译为可执行的SPARQL，但缺乏模式级上下文时，它们常常编造不存在的谓词，或无法将实体名称解析为数据库特定的标识符。我们提出TogoMCP，该系统将LLM重塑为一种协议驱动的推理引擎，通过模型上下文协议（MCP）协调专用工具。其设计有两个关键机制：（i）MIE（元数据-互操作性-交换）文件，一份简洁的YAML文档，在查询时动态为LLM提供每个目标数据库的结构和语义上下文；（ii）一个两阶段工作流，将外部REST API的实体解析与模式引导的SPARQL生成相分离。在涵盖5种类型、23个数据库的50个生物学问题基准上，TogoMCP相比无辅助基线取得了大幅改进（Cohen's d = 1.82，Wilcoxon p < 0.001），对于具有精确可验证答案的问题类型，胜率超过80%。消融研究表明，所有组件配置均带来显著改进，其中MIE模式文件在平均每题得分上的边际贡献最大（相对于无MIE条件，Δ = +0.50，双尾Wilcoxon p = 0.067；90%自助法CI [+0.04, +0.94]排除零）；加载相关MIE文件的一行指令恢复了与完整程序化协议相同的平均改进，而协议额外降低了下行风险（损失率1.6% vs. 4.8%，Fisher p = 0.036）。这些结果表明了一个通用设计原则：对于平均得分性能，简洁、动态提供的模式上下文比复杂的编排逻辑更有价值，而程序化指导在缩小方差方面发挥补充作用。

## Abstract
Querying the RDF Portal knowledge graph maintained by DBCLS, which aggregates approximately 60 life-science databases, requires proficiency in both SPARQL and database-specific RDF schemas, placing this resource beyond the reach of most researchers. Large Language Models (LLMs) can, in principle, translate natural-language questions into executable SPARQL, but without schema-level context, they frequently fabricate non-existent predicates or fail to resolve entity names to database-specific identifiers. We present TogoMCP, a system that recasts the LLM as a protocol-driven inference engine orchestrating specialized tools via the Model Context Protocol (MCP). Two mechanisms are essential to its design: (i) the MIE (Metadata-Interoperability-Exchange) file, a concise YAML document that dynamically supplies the LLM with each target database's structural and semantic context at query time; and (ii) a two-stage workflow separating entity resolution via external REST APIs from schema-guided SPARQL generation. On a benchmark of 50 biologically grounded questions spanning five types and 23 databases, TogoMCP achieved a large improvement over an unaided baseline (Cohen's d = 1.82, Wilcoxon p < 0.001), with win rates exceeding 80% for question types with precise, verifiable answers. An ablation study shows that all component configurations deliver significant improvements, with MIE schema files providing the largest marginal contribution on mean per-question score ({Delta} = +0.50 relative to a no-MIE condition, two-sided Wilcoxon p = 0.067; 90% bootstrap CI [+0.04, +0.94] excludes zero); a one-line instruction to load the relevant MIE file recovers the same mean improvement as a full procedural protocol, while the protocol additionally reduces downside risk (loss rate 1.6% vs. 4.8%, Fisher p = 0.036). These results suggest a general design principle: concise, dynamically delivered schema context is more valuable than complex orchestration logic for mean-score performance, while procedural guidance plays a complementary role in narrowing variance.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：生命科学领域依赖大量专业数据库（如UniProt、ChEMBL、MeSH等），DBCLS维护的RDF Portal聚合了约60个数据库，形成一个可查询的知识图谱。然而，查询需要精通SPARQL语言和各个数据库特有的RDF模式（schema），导致大多数研究人员无法直接使用。
- **问题**：大型语言模型（LLM）理论上可将自然语言问题翻译为SPARQL，但缺乏模式级上下文时，会编造不存在的谓词、误用数据库特定词汇，或无法将自然语言实体名解析为数据库内部标识符。
- **整体含义**：TogoMCP通过将LLM塑造为协议驱动的推理引擎，利用模型上下文协议（MCP）编排专用工具，并引入MIE文件（YAML格式）动态提供模式上下文，从而弥合自然语言与知识图谱查询之间的鸿沟。

## 2. 方法论

### 核心思想
将LLM视为一个推理引擎，通过MCP协议与外部工具交互，实现从自然语言问题到可执行SPARQL查询的转换。关键在于显式、动态地提供每个目标数据库的结构和语义上下文，并将实体解析与查询生成解耦。

### 关键技术细节
- **MIE文件（Metadata-Interoperability-Exchange）**：一份400–600行（复杂数据库700–900行）的YAML文档，包含schema info、shEx形状表达式、示例RDF三元组、SPARQL示例查询、跨数据库查询、交叉引用、数据统计、反模式/常见错误等部分。每个数据库对应一个MIE文件，通过`get MIE file`工具按需传递给LLM。
- **两阶段工作流**：
    1. **实体解析**：通过专用REST API（如UniProt搜索、ChEMBL靶点搜索、NCBI E-utilities等）从自然语言实体名获取数据库内部标识符（如TP53映射为ChEMBL靶点ID）。
    2. **模式引导的SPARQL生成**：LLM参考对应MIE文件中的shape expressions、示例查询等，构建并执行SPARQL查询，返回结果后可能进一步细化。
- **协议驱动控制（TogoMCP Usage Guide）**：一个嵌入LLM上下文的行为协议，包含问题类型分类（五种）、强制工作流顺序（`find databases` → entity resolution → `get MIE file` → `run sparql`）、SPARQL调用预算（最多连续2次）、工具优先级（结构化查找>文本搜索>直接SPARQL）、探索性查询先LIMIT 10等防错策略。
- **系统架构**：使用FastMCP库构建Python服务，挂载多个外部MCP服务器（PubMed、OLS4、PubDictionaries），每个数据库映射到CSV配置。支持28个RDF数据库（分布在8个SPARQL端点），其中16个有专用REST实体搜索工具，其余12个回退到SPARQL文本搜索。

（无数学公式或算法伪代码）

## 3. 实验设计

### 数据集/场景
- **基准**：50个具有生物学基础的问题，涵盖5种类型（yes/no、factoid、list、summary、choice），每种10个。问题要求涉及至少2个数据库（60%），至少3个数据库（20%），覆盖所有23个当时支持的数据库。问题需确保通过RDF数据库访问才能回答（排除LLM预训练或文献可得的）。每个问题有精确答案（类型相关）和理想答案（专家撰写的段落）作为黄金标准。
- **对比方法**：
    - **基线**：Claude Sonnet 4.5（无任何工具，仅LLM自身知识）。
    - **TogoMCP agent**：同一模型 + MCP工具（RDF Portal访问、搜索API等，禁止网络搜索）。
- **消融条件**：
    - With Guide：完整系统（TogoMCP Usage Guide + MIE文件）。
    - MIE-Instr：移除Usage Guide，但显式提示调用`find databases`和`get MIE file`。
    - No-Instr：无Usage Guide，无显式提示。
    - No MIE：完全移除`get MIE file`工具（但仍可使用其他工具和自发现）。

### 评估方式
- **自动评估**：由LLM评委（Claude Opus 4.7）在四个维度（信息召回、精确性、非冗余性、可读性）上打分，每维度1–5分，总分4–20。每个问答对运行5次独立评估取均值，以减少随机噪声。
- **手动验证**：从50个问题中分层随机抽取20个（每类型4个），由3位领域专家匿名、随机顺序地对基线和TogoMCP答案进行相同维度的评分，对比LLM评委的一致性。

## 4. 资源与算力

- 论文中未提及使用特定GPU型号、数量或训练时长。所有实验均基于API调用**Anthropic的模型**（Claude Sonnet 4.5用于生成，Claude Opus 4.7用于评估），属于推理阶段，无需训练。
- **性能指标**：
    - 平均延迟：137秒（是基线的17.4倍）
    - 平均成本：$0.38/问题（是基线的70倍）
- **说明**：未涉及训练算力，仅报告了推理开销。消融实验中各条件成本相近（$0.38–$0.41/问题）。

## 5. 实验数量与充分性

- **数量**：
    - 主实验：50个问题 × 5次评估 = 250个问答对，每个条件均独立运行。
    - 消融实验：4种条件（With Guide, MIE-Instr, No-Instr, No MIE），共50×5×4=1000次评估。
    - 手动验证：20个问题 × 3位专家 = 60次手动评分。
- **统计检验**：使用Cohen's d、Wilcoxon符号秩检验、Bootstrap置信区间、Fisher精确检验、Levene方差检验等，严格控制多重比较。
- **充分性**：
    - **充分**：覆盖多种问题类型（验证、事实、列表、总结、选择）和23个数据库；手动验证与自动评估结果高度一致（Pearson r=0.908 on totals）；消融实验设计清晰，隔离了MIE文件、Usage Guide、指令等组件。
    - **可能不足**：
        - 仅测试了Claude模型系列（Sonnet 4.5和Opus 4.7），未测试其他LLM（如GPT-4、Llama等），泛化性未知。
        - 基准问题仅50个，虽精心设计但仍算小规模。
        - 手动验证中三位注释者之间一致性中等（ICC(2,1)=0.675 on totals），但均值后上升到良好。
        - 评估主要依赖LLM作为评判（存在系统偏差），手动验证仅在子集上完成。

## 6. 主要结论与发现

1. **TogoMCP大幅优于无辅助基线**：平均总分从15.10提升到18.55（Δ=+3.45，Cohen's d=1.82，p<0.001），胜率94.4%，损失率仅1.6%。基线从未获得满分20，而TogoMCP在107/250次评估中达到20分（覆盖26个不同问题）。
2. **增益集中在信息召回和精确性**：召回+2.23（5分制），精确性+1.04，非冗余性和可读性边际提升。
3. **不同问题类型增益差异**：yes/no（Δ=+4.22，100%胜率）> factoid（+3.82）> list（+3.58）> choice（+3.20）> summary（+2.44）。精确可验证的问题受益最大。
4. **MIE文件是最大的边际贡献者**：移除MIE文件使平均改善降低0.50分（90% Bootstrap CI [0.04, 0.94]排除零）。单条指令加载MIE文件即可恢复与完整Usage Guide相同的平均改善（Δ=+3.46 vs +3.45，p=0.877）。
5. **Usage Guide的价值在于降低方差和失败率**：With Guide的损失率1.6%，显著低于MIE-Instr的4.8%（p=0.036）和No-Instr的6.0%（p=0.009）。Guide缩小了问题间性能波动（SD从2.71降至1.90）。
6. **工具调用数量与性能负相关**：最优区间5–9次工具调用（均值19.1），超出15次后降到16.7。过度链式调用通常反映初始错误后的补偿行为。

## 7. 优点

- **方法设计**：
    - 两阶段工作流（实体解析 → SPARQL生成）有效分离关注点，避免LLM在单一提示中同时处理文本匹配和图形遍历。
    - MIE文件格式紧凑（400–600行）、标准化、可扩展（从23个数据库扩展到28个），并包含反模式指导，提升LLM正确使用数据库特定词汇的能力。
    - 协议驱动控制（Usage Guide）通过问题类型分类、SPARQL预算限制、工具优先级等降低无效探索。
- **实验设计**：
    - 系统性的消融实验（4种条件）清晰隔离了MIE文件和Usage Guide各自的贡献。
    - 多重统计检验（Cohen's d、Wilcoxon、Bootstrap、Fisher）增强结论可信度。
    - 手动验证子集（20问题×3专家）与LLM评委高度一致（r=0.908），增强了自动评估的可信度。
    - 基准问题设计严谨：要求RDF数据库访问、涵盖多个数据库、排除可记忆或文献可得的答案、验证过聚合查询的算术一致性。
- **实用性**：
    - 系统已在线上部署（https://togomcp.rdfportal.org/），并开源代码。
    - 平均成本$0.38/问题在可接受范围，对于需要精确数据库检索的查询而言性价比高。

## 8. 不足与局限

1. **评估依赖LLM作为评判**：自动评估由Claude Opus 4.7进行，虽与手动验证相关度高，但存在系统偏差（对风格维度如非冗余性和可读性的评分与人类差距较大）。
2. **模型族局限性**：仅使用Anthropic Claude系列模型，未测试GPT-4、Llama、Gemini等其他主流LLM，通用性未验证。
3. **基准规模较小**：仅50个问题，虽跨类型但可能不足以代表生物学家真实查询的全部多样性。新增的5个数据库未包含在基准中。
4. **手工维护开销**：MIE文件的创建和审查需要专家人工（每数据库2–4小时），虽然流程已半自动化，但大规模扩展仍需持续投入。此外，随着底层本体和端点演化，MIE文件可能过时（目前靠周期性人工检查，未自动化）。
5. **跨端点查询缺陷**：系统不支持原生SPARQL 1.1 SERVICE联邦查询（因可靠性问题），而是通过顺序多查询+VALUES桥接。这带来错误传播风险——若第一个查询遗漏某些标识符，后续查询返回的不完整结果不会触发错误。
6. **未测试开放域假设生成**：虽然论文展示了阿尔茨海默病分析示例，但正式基准仅包含边界明确的问答题类型，未涵盖假设生成、多跳跨数据库推理、负例查询等更复杂的实际使用场景。
7. **手动验证一致性有限**：三位领域专家间的单评分者ICC仅为0.675（中等），尽管平均后提高到0.862（良好），暗示独立评估仍存在一定分歧。

（完）
