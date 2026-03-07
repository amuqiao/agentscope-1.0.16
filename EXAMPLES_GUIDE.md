# AgentScope 示例指南

本文档详细介绍 AgentScope 项目中 `examples` 目录下的示例项目，包括各示例的功能、使用方法和启动命令。

## 目录结构

AgentScope 的示例目录按照功能和应用场景进行了分类，主要包括以下几个类别：

- **agent/**: 各种类型的智能体示例
- **deployment/**: 部署相关示例
- **evaluation/**: 评估相关示例
- **functionality/**: 功能演示示例
- **game/**: 游戏相关示例
- **integration/**: 集成示例
- **tuner/**: 调优示例
- **workflows/**: 工作流示例

## 详细示例说明

### 1. agent/ 目录

#### 1.1 a2a_agent
- **功能**: 演示如何使用 AgentScope 的 `A2AAgent` 连接到外部 A2A (Agent-to-Agent) 服务器
- **主要文件**:
  - `main.py`: 运行 A2A 智能体的主脚本
  - `setup_a2a_server.py`: 设置简单的 A2A 服务器的脚本
  - `agent_card.py`: A2A 智能体的卡片定义
- **启动命令**:
  1. 安装依赖: `pip install a2a-sdk[http-server] agentscope[a2a]`
  2. 启动 A2A 服务器: `uvicorn setup_a2a_server:app --host 0.0.0.0 --port 8000`
  3. 运行示例: `python main.py`

#### 1.2 a2ui_agent
- **功能**: 演示如何在 AgentScope 中集成 A2UI (Agent-to-Agent UI) 协议，使智能体能够生成交互式用户界面
- **主要文件**:
  - `samples/client/lit`: A2UI 客户端示例应用
  - `samples/general_agent`: 实现 A2UI 功能的智能体
- **启动命令**:
  1. 克隆 A2UI 仓库: `git clone https://github.com/google/A2UI.git`
  2. 复制渲染器和规范: `cp -r A2UI/renderers AgentScope/examples/agent/a2ui_agent && cp -r A2UI/specification AgentScope/examples/agent/a2ui_agent`
  3. 运行餐厅查找演示: `cd AgentScope/examples/agent/a2ui_agent/samples/client/lit && npm run demo:restaurant`

#### 1.3 browser_agent
- **功能**: 演示如何使用 AgentScope 的 BrowserAgent 进行网页自动化任务
- **主要文件**:
  - `browser_agent.py`: 浏览器智能体实现
  - `main.py`: 运行浏览器智能体的主脚本
- **启动命令**:
  1. 安装 AgentScope: `pip install -e .`
  2. 设置环境变量: `export DASHSCOPE_API_KEY="your_dashscope_api_key_here"`
  3. 运行示例: `cd examples/agent/browser_agent && python main.py`

#### 1.4 deep_research_agent
- **功能**: 演示如何使用 AgentScope 实现深度研究智能体，执行多步骤研究并生成综合报告
- **主要文件**:
  - `deep_research_agent.py`: 深度研究智能体实现
  - `main.py`: 运行深度研究智能体的主脚本
- **启动命令**:
  1. 设置环境变量: `export DASHSCOPE_API_KEY="your_dashscope_api_key_here" && export TAVILY_API_KEY="your_tavily_api_key_here"`
  2. 测试 Tavily MCP 服务器: `npx -y tavily-mcp@latest`
  3. 运行示例: `python main.py`

#### 1.5 meta_planner_agent
- **功能**: 演示如何构建一个规划智能体，将复杂任务分解为可管理的子任务，并协调子智能体完成这些任务
- **主要文件**:
  - `main.py`: 运行规划智能体的主脚本
  - `tool.py`: 包含创建子智能体的工具函数
- **启动命令**:
  1. 安装 AgentScope: `pip install agentscope`
  2. 设置环境变量 (可选): `export GAODE_API_KEY="your_gaode_api_key" && export GITHUB_TOKEN="your_github_token"`
  3. 运行示例: `python main.py`

### 2. functionality/ 目录

#### 2.1 agent_skill
- **功能**: 演示如何在 AgentScope 中集成 Agent Skills，提高智能体在特定任务上的能力
- **主要文件**:
  - `main.py`: 运行示例的主脚本
  - `skill/analyzing-agentscope-library`: 帮助智能体了解 AgentScope 框架的技能
- **启动命令**:
  1. 安装 AgentScope: `pip install agentscope --upgrade`
  2. 运行示例: `python main.py`

#### 2.2 long_term_memory
- **功能**: 演示 AgentScope 的长期记忆功能，包括使用 mem0 和 reme 两种记忆后端
- **子目录**:
  - `mem0`: 使用 mem0 作为记忆后端的示例
  - `reme`: 使用 reme 作为记忆后端的示例
- **启动命令**:
  - mem0 示例: `cd examples/functionality/long_term_memory/mem0 && python memory_example.py`
  - reme 示例: `cd examples/functionality/long_term_memory/reme && python personal_memory_example.py`

#### 2.3 rag
- **功能**: 演示 AgentScope 的检索增强生成 (RAG) 功能，包括基本用法、多模态 RAG 和与 ReAct 智能体的集成
- **主要文件**:
  - `basic_usage.py`: RAG 的基本用法示例
  - `multimodal_rag.py`: 多模态 RAG 示例
  - `react_agent_integration.py`: RAG 与 ReAct 智能体集成的示例
- **启动命令**:
  - 基本用法: `cd examples/functionality/rag && python basic_usage.py`
  - 多模态 RAG: `cd examples/functionality/rag && python multimodal_rag.py`
  - 与 ReAct 智能体集成: `cd examples/functionality/rag && python react_agent_integration.py`

### 3. game/ 目录

#### 3.1 werewolves
- **功能**: 一个九人狼人杀游戏示例，展示多智能体交互、基于角色的游戏玩法和结构化输出处理
- **主要文件**:
  - `main.py`: 运行游戏的主脚本
  - `game.py`: 游戏逻辑实现
  - `prompt.py`: 游戏提示模板
- **启动命令**:
  1. 设置环境变量: `export DASHSCOPE_API_KEY="your_dashscope_api_key_here"`
  2. 运行游戏: `python main.py`

### 4. workflows/ 目录

#### 4.1 multiagent_conversation
- **功能**: 演示如何使用 AgentScope 中的 `MsgHub` 构建多智能体对话工作流
- **主要文件**:
  - `main.py`: 运行多智能体对话的主脚本
- **启动命令**:
  1. 安装 AgentScope: `pip install agentscope --upgrade`
  2. 运行示例: `python examples/workflows/multiagent_conversation/main.py`

#### 4.2 multiagent_debate
- **功能**: 演示多智能体辩论工作流
- **主要文件**:
  - `main.py`: 运行多智能体辩论的主脚本
- **启动命令**:
  1. 安装 AgentScope: `pip install agentscope --upgrade`
  2. 运行示例: `python examples/workflows/multiagent_debate/main.py`

### 5. evaluation/ 目录

#### 5.1 ace_bench
- **功能**: 演示 AgentScope 中的智能体导向评估，使用 Ray 进行分布式并行评估
- **主要文件**:
  - `main.py`: 运行 ACEBench 评估的主脚本
- **启动命令**:
  1. 安装 AgentScope: `pip install agentscope --upgrade`
  2. 运行评估: `python main.py --data_dir {data_dir} --result_dir {result_dir}`

## 总结

AgentScope 的示例目录提供了丰富的示例，覆盖了以下功能领域：

- **智能体类型**: A2A 智能体、A2UI 智能体、浏览器智能体、深度研究智能体、规划智能体等
- **核心功能**: 长期记忆、短期记忆、RAG、结构化输出、技能集成、TTS 等
- **工作流**: 多智能体对话、多智能体辩论、多智能体并发等
- **游戏**: 狼人杀游戏等
- **评估**: 智能体导向评估等

这些示例展示了 AgentScope 的强大功能和灵活性，为开发者提供了学习和参考的资源。通过运行这些示例，开发者可以快速了解 AgentScope 的使用方法，并将其应用到自己的项目中。

## 注意事项

1. 大多数示例需要设置相应的 API 密钥环境变量，如 `DASHSCOPE_API_KEY`、`TAVILY_API_KEY` 等
2. 部分示例依赖外部 MCP 服务器，需要先启动这些服务器
3. 不同示例可能需要不同的依赖包，建议根据示例的 README.md 文件安装相应的依赖
4. 对于使用 DashScope 模型的示例，如果要更改模型，需要同时更改相应的格式化器
