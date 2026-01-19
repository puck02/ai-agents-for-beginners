# Course 02 学习总结（Explore AI Agent Frameworks）

- 日期：2026-01-18
- 学习时长：约 1 小时

## 课程目标与核心收获
- 认识 AI Agent Frameworks 的作用：用标准化组件（SDKs）、运行时（runtime）、记忆（memory/RAG）、工具调用（tool/plugin）与多代理编排，把模型能力工程化为可运行的智能体系统。
- 理解两类运行时：Stand-alone runtime（单进程/同语言，低延迟、实现简单）与 Distributed runtime（跨进程/跨机/跨语言，便于伸缩与容错）。
- 掌握关键术语（保留英文名）：
  - SDKs（Software Development Kit）：软件开发工具包；提供连接器、插件、模板等。
  - runtime：负责 agent 生命周期管理、消息路由、并发调度与安全边界。
  - LLM / SLM：LLM=Large Language Model；SLM=Small Language Model（低资源、低延迟、适合本地/边缘）。
  - RAG（Retrieval-Augmented Generation）：检索增强生成，用向量检索为生成提供事实依据。
  - Tool Use / Tool Invocation：智能体调用外部 API/函数的能力。

## 框架对比与适用场景
- AutoGen（开源，多代理、事件驱动与分布式协作）：
  - 擅长多角色并行、复杂协议与异步消息；适合研究/原型与多代理编排。
  - 记忆层非内建向量存储；可通过工具/插件接入向量数据库或文件存储实现长期记忆。
- Semantic Kernel（工程化 SDK，Python/C#）：
  - 内建 memory 抽象、AI connectors、函数/插件调用与 agent 框架；适合长期会话、RAG 与从原型走向工程化。
  - 更容易管理上下文与函数选择，便于稳定维护与扩展。
- Azure AI Agent Service（Azure 托管的企业级平台）：
  - 深度整合 Azure 生态（Search、Functions、Identity、监控），面向生产与合规场景，支持大规模与审计。
  - 需要 Azure 账号与相应配置，按用量计费。

## 实践建议（结合当前条件）
- 预算有限：
  - 先用 Semantic Kernel + GitHub Models（免费/有限）或本地模型（Ollama/vLLM）做有记忆与检索的助理原型。
  - 当需要多代理协作/并行流程，再引入 AutoGen 做编排与角色分工。
- 本地硬件：普通 macOS 开发即可；如需本地 7B+ 模型，Apple Silicon/更大内存更佳，否则优先云模型。

## 下一步可选行动
  - Semantic Kernel 入门：[01-intro-to-ai-agents/code_samples/01-semantic-kernel.ipynb]
  - AutoGen 入门：[02-explore-agentic-frameworks/code_samples/02-autogen.ipynb]
  - 复试助手（RAG + memory + Tool Use）：展示检索流程、记忆效果与工具调用；解释 embeddings/Vector DB 与 runtime 的作用。
## Course 03 简短预习（Understanding AI Agentic Design Patterns）
- 目标：提前熟悉常见 Agent 设计模式及关键英文术语（保留并解释）。
- 关键术语与模式：
  - ReAct（Reasoning + Acting）：推理与行动结合；在推理步骤中决定是否调用外部工具（act）。
  - Planner / Executor（Planner‑Solver）：将复杂任务分解为子任务，由执行器逐步执行与验证，适合 multi‑step problems。
  - RAG（Retrieval‑Augmented Generation）：检索增强生成；Embeddings + Vector DB 检索上下文后交给 LLM 生成。
  - Memory（Short‑term / Long‑term）：短期为会话上下文；长期为向量库中的持久化信息。
  - Tool Use / Tool Invocation：Agent 调用外部 API/函数；通过 Tool Registry/插件管理。
  - Chain‑of‑Thought（CoT）：显式展开中间推理步骤的提示技术，提升复杂推理稳定性。
  - Multi‑Agent Patterns（Leader‑Worker、BlackBoard 等）：多 Agent 的协作/协调模式。
  - Orchestration / Runtime：运行时负责调度、消息路由、并发与安全边界（stand‑alone vs distributed）。
  - Embeddings & Vector DB：文本向量化与相似度检索；向量数据库用于高效查询。
  - MCP（Model Context Protocol）：模型/Agent 之间的上下文通信协议。
