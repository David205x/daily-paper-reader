<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-18
- 运行时间：2026-08-18 21:04:29 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：7
- 速读区：11

### 今日简报（AI）
今日精读7篇、速读11篇，聚焦强化学习与LLM推荐系统；最值得关注的是RLHF中情感漂移的归因机制，以及多轮推荐中“主动提问”提升置信度的策略；建议普通读者优先把握这两篇的核心结论，速读部分可留意机器人技能复用与智能体自进化方向。
- 详情：[/202608/18/README](/202608/18/README)

### 精读区论文标签
1. [Why Summaries Turn Neutral: Policy Attribution for Sentiment Drift in Reinforcement Learning from Human Feedback](/202608/18/2608.15530v1-why-summaries-turn-neutral-policy-attribution-for-sentiment-drift-in-reinforcement-learning-from-human-feedback)  
   标签：评分：9.0/10、query:rl
   evidence：基于人类反馈的强化学习对齐；通过策略归因分析情感漂移与奖励模型和KL惩罚的关系
2. [Ask to Be Sure: Informative Interactions for Confident Multi-Turn LLM Recommendation](/202608/18/2608.15949v1-ask-to-be-sure-informative-interactions-for-confident-multi-turn-llm-recommendation)  
   标签：评分：9.0/10、query:rl
   evidence：以推荐熵降为奖励，强化学习优化多轮对话推荐交互
3. [Learn What's Left, Not What's Mastered: Saturation Aware Advantage Reweighting for Multi-Reward Policy Optimization](/202608/18/2608.16072v1-learn-whats-left-not-whats-mastered-saturation-aware-advantage-reweighting-for-multi-reward-policy-optimization)  
   标签：评分：9.0/10、query:rl
   evidence：面向语言模型推理后训练的多奖励策略优化方法
4. [TRCA: Transition-wise Rubric Credit Assignment for Long-horizon LLM Agents](/202608/18/2608.16156v1-trca-transition-wise-rubric-credit-assignment-for-long-horizon-llm-agents)  
   标签：评分：9.0/10、query:rl
   evidence：提出逐转移规则表信用分配，为长程LLM智能体在稀疏终端奖励下生成步骤级奖励监督。
5. [STAGE: Controlled Objective Admission for Multi-Preference LLM Alignment](/202608/18/2608.16553v1-stage-controlled-objective-admission-for-multi-preference-llm-alignment)  
   标签：评分：9.0/10、query:rl
   evidence：面向多偏好LLM对齐的目标受控准入方法，优化策略学习
6. [Ask, Condition or Abstain: Reinforcement Learning for Missing-Premise Reasoning](/202608/18/2608.16554v1-ask-condition-or-abstain-reinforcement-learning-for-missing-premise-reasoning)  
   标签：评分：9.0/10、query:rl
   evidence：提出ACA-RL，用结构化奖励的强化学习处理缺失前提推理
7. [Le Critique: Privileged Value Functions for LLM Reinforcement Learning](/202608/18/2608.16739v1-le-critique-privileged-value-functions-for-llm-reinforcement-learning)  
   标签：评分：9.0/10、query:rl
   evidence：改进LLM强化学习中的值函数设计以降低方差

### 速读区论文标签
1. [SkillComposer: Learning Reusable Skills for Natural-Language Robot Programming](/202608/18/2608.14944v1-skillcomposer-learning-reusable-skills-for-natural-language-robot-programming)  
   标签：评分：8.0/10、query:rl
   evidence：面向自然语言机器人编程的LLM智能体与可复用技能学习
2. [LLM-Based Hierarchical Coordinated Control with Continuation-Aware Policy Learning](/202608/18/2608.15041v1-llm-based-hierarchical-coordinated-control-with-continuation-aware-policy-learning)  
   标签：评分：8.0/10、query:rl
   evidence：将GRPO强化学习策略优化应用于LLM协调控制器，并通过延续感知的奖励评估影响后续决策
3. [Evo-Harness: Context-to-Harness Skill Compilation for Self-Evolving Agents](/202608/18/2608.15071v1-evo-harness-context-to-harness-skill-compilation-for-self-evolving-agents)  
   标签：评分：8.0/10、query:rl
   evidence：提出在线操作框架学习，使LLM智能体在复杂真实任务中持续自我进化。
4. [RLCascadeRouter: Quality-Estimator-Free Cascade Routing via Reinforcement Learning](/202608/18/2608.15817v1-rlcascaderouter-quality-estimator-free-cascade-routing-via-reinforcement-learning)  
   标签：评分：8.0/10、query:rl
   evidence：基于强化学习的LLM级联路由以优化成本与性能
5. [Exploration-Driven Personalized Federated Reinforcement Learning via Intrinsic Motivation](/202608/18/2608.10499v1-exploration-driven-personalized-federated-reinforcement-learning-via-intrinsic-motivation)  
   标签：评分：7.0/10、query:rl
   evidence：通过内在好奇心驱动的探索奖励设计，缓解个性化联邦强化学习中稀疏奖励下的探索不足
6. [SkillCommit: Evolving Agent Skills through Behaviorally Validated Scope Expansion](/202608/18/2608.15165v1-skillcommit-evolving-agent-skills-through-behaviorally-validated-scope-expansion)  
   标签：评分：7.0/10、query:rl
   evidence：面向LLM智能体的在线技能演化框架，将历史经验转化为层次化可复用技能库以提升任务执行质量
7. [HyMem: Hierarchical Context Management for Long-Horizon Agents via Information Isolation](/202608/18/2608.15703v1-hymem-hierarchical-context-management-for-long-horizon-agents-via-information-isolation)  
   标签：评分：7.0/10、query:rl
   evidence：面向长时程LLM智能体的分层上下文管理
8. [SEER: Long-Context Reasoning via Selective Visual-Text Compression](/202608/18/2608.15962v1-seer-long-context-reasoning-via-selective-visual-text-compression)  
   标签：评分：7.0/10、query:rl
   evidence：面向长上下文推理的选择性检索相关文本内容
9. [RoutePack: Expert Placement and Attention-Aware Data Packing for MoE Reinforcement Learning](/202608/18/2608.12146v1-routepack-expert-placement-and-attention-aware-data-packing-for-moe-reinforcement-learning)  
   标签：评分：6.0/10、query:rl
   evidence：面向MoE强化学习的专家路由与数据打包优化
10. [MobileMem: Learning from a Year of Mobile Experiences](/202608/18/2608.13606v2-mobilemem-learning-from-a-year-of-mobile-experiences)  
   标签：评分：6.0/10、query:rl
   evidence：面向移动AI智能体的长期记忆框架与基准
11. [LOCAL: Enabling Learning On-device Contiguously for Agent LLMs](/202608/18/2608.15241v1-local-enabling-learning-on-device-contiguously-for-agent-llms)  
   标签：评分：6.0/10、query:rl
   evidence：面向智能体LLM的设备端连续学习，使模型能从交互中持续适应


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
