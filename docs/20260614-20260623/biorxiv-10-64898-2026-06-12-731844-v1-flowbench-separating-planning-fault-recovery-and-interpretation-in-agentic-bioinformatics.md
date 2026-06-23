---
title: "FlowBench: separating planning, fault recovery and interpretation in agentic bioinformatics"
title_zh: FlowBench：在智能体生物信息学中分离规划、故障恢复与解释
authors: "Kurjan, A., Cribbs, A. P."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731844v1.full.pdf"
tags: ["query:rl"]
score: 7.0
evidence: 生物信息学中的LLM智能体任务自动化基准
tldr: 生物信息学中的智能体大语言模型系统性能评估常混淆规划、故障恢复与解释能力。FlowBench将评估分解为规划、故障恢复、生物解释和端到端输出保真度。基于FlowAgent框架评估了23个模型，发现规划趋于饱和，但从生物意图推断工具链仍困难；故障恢复和数据解释未解决；安全性与能力无关。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单一指标评估掩盖了智能体系统不同组件的独立失败模式，需分离规划、故障恢复与解释能力。
method: 构建FlowBench基准，分解评估维度；开发FlowAgent模块化框架，支持组件消融和模型互换。
result: "规划任务高完成度，但生物意图推断仅44-57%通过率；依赖结构计划和反思步骤提升性能，验证重试反而降低结构质量；故障恢复与数据解释未解决。"
conclusion: 规划饱和后，智能体架构和拒答校准比模型规模更重要，安全不随能力自然涌现。
---

## 摘要
AO_SCPLOWBSTRACTC_SCPLOW智能体大语言模型（LLM）系统在生物信息学中的部署速度超过了人们对它们的理解速度，而单一指标的评估会混淆独立失效的能力。我们提出了FlowBench，一个将智能体生物信息学性能分解为规划、故障恢复、生物学解释以及端到端输出保真度的基准测试。现有系统的计划完整性很高，但其封闭、单一供应商的设计使得无法将性能归因于脚手架还是底层模型。因此，我们构建了FlowAgent，一个模块化、供应商无关的框架，其组件可以选择性地禁用，主干模型可以在共享平台上的不同供应商之间切换，并用于评估来自三个主要供应商的23个模型。有三项发现。首先，从命名的工具链生成有效的工作流规划在很大程度上已解决，而仅从生物意图推断合适的工具链则普遍困难，无论模型等级如何，所有模型都被压缩在狭窄的44-57%通过率区间内。其次，消融实验表明，依赖结构化的计划和完整性反思步骤推动了性能，而添加相同上下文的验证器驱动重试则使结构质量变差。第三，故障恢复和数据驱动的解释仍未解决。模型经常提出强制干净退出但使底层数据无效的修复方案，而数据驱动的解释始终落后于内部知识回忆。安全性并非源于能力，推理级模型在识别不可恢复故障方面最不可靠。一旦规划饱和，智能体架构和拒绝校准，而非模型规模，才是富有成效的前沿。

可用性与实现FlowAgent和FlowBench在GPLv3许可下可在https://github.com/EnteloBio/flowagent获取

联系adam@entelo.bio

## Abstract
AO_SCPLOWBSTRACTC_SCPLOWAgentic large language model (LLM) systems are being deployed in bioinformatics faster than they are understood, and single-metric evaluations conflate capabilities that fail independently. We introduce FlowBench, a benchmark that decomposes agentic bioinformatics performance into planning, fault recovery, biological interpretation, and end-to-end output-fidelity. Existing systems achieve high plan completeness, but their closed, single-provider designs prevent attribution of performance to scaffolding versus the underlying model. We therefore built FlowAgent, a modular, provider-agnostic framework whose components can be selectively disabled and whose backbone model can be swapped across providers on a shared harness, and used it to evaluate 23 models from three main providers. Three findings emerge. First, generating a valid workflow plan from a named toolchain is largely solved, whereas inferring an appropriate toolchain from biological intent alone is uniformly difficult regardless of model tier, compressing all models into a narrow 44-57% pass-rate band. Second, ablation shows that the dependency-structured plan and a completeness-reflection step drive performance, while adding a same-context validator-driven retry makes structural quality worse. Third, fault recovery and data-grounded interpretation remain unsolved. Models frequently propose fixes that force a clean exit while leaving the underlying data invalid, and data-grounded interpretation lags internal-knowledge recall by a consistent margin. Safety does not emerge from capability, and reasoning-tier models were among the least reliable at recognising unrecoverable faults. Once planning saturates, agent architecture and refusal calibration, not model scale, are the productive frontier.

Availability and implementationFlowAgent and FlowBench are available under a GPLv3 licence at https://github.com/EnteloBio/flowagent

Contactadam@entelo.bio