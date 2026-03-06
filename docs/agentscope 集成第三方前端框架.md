

# GitHub 开源前端 AI 对话框架汇总

以下是从两个文档中整理的前端AI对话框架，按 GitHub 星数降序排列，包含框架名称、GitHub 地址、星数、核心功能和适配 FastAPI 情况。

## 📊 前端 AI 框架汇总表

| 框架名称 | GitHub 地址 | 星数 | 核心功能 | 适配 FastAPI |
|---------|------------|------|----------|-------------|
| **Open WebUI** | https://github.com/Open-Webui/Open-Webui | 90,900+ | 零代码搭建AI界面，自动识别本地Ollama模型，支持OpenAI兼容API，企业级安全，内置RAG | 支持，实现`/v1/chat/completions`和`/v1/models`端点 |
| **NextChat (原ChatGPT Next Web)** | https://github.com/Yidadaa/ChatGPT-Next-Web | 86,000+ | 一键部署，支持多模型，完整Markdown渲染，上下文记忆，暗色/亮色主题 | 支持，设置`OPENAI_API_BASE_URL`环境变量 |
| **LobeChat** | https://github.com/lobehub/lobe-chat | 67,000+ | 现代化设计，支持语音合成/识别，多模态交互，可扩展插件系统，多用户管理 | 支持，修改API端点为FastAPI地址 |
| **LibreChat** | https://github.com/LibreChat-AI/LibreChat | 33,900+ | 支持15+ AI提供商，兼容ChatGPT插件规范，多用户管理，企业级认证 | 支持，添加自定义API端点 |
| **Onyx (前Danswer)** | https://github.com/onyx-dot-app/onyx | 17,000+ | 企业级AI搜索与聊天平台，支持40+知识源连接，内置RAG功能 | 原生使用FastAPI作为后端 |
| **ChatGPT Web** | https://github.com/chatgpt-web-dev/chatgpt-web | 15,000+ | 基于Express和Vue3的ChatGPT页面复刻，双模型支持，多会话管理 | 支持，实现OpenAI兼容接口 |
| **Chatbot UI (Mckay Wrigley)** | https://github.com/mckaywrigley/chatbot-ui | 20,000+ | 1:1复刻ChatGPT原生界面，支持流式响应，自定义API端点，本地存储对话记录 | 支持，修改API调用地址指向FastAPI |
| **Chainlit** | https://github.com/Chainlit/chainlit | 11,400+ | Python框架，无需前端知识，支持多模态交互，与LangChain等无缝集成 | 与FastAPI天然契合，可直接集成 |
| **Assistant UI** | https://github.com/assistant-ui/assistant-ui | 7,500+ | TypeScript/React组件库，自动处理流式响应，完全可组合的原语 | 支持，实现`/api/chat`接口 |
| **Open Chat Ai** | https://github.com/suneelkumarr/Open-Chat-Ai | 5,000+ | 下一代React聊天机器人，支持任意LLM提供商，流式响应，多种人格风格 | 支持，实现`/v1/chat/completions`接口 |
| **AI Chat Assistant** | https://github.com/flyryan/ai-chat | 3,000+ | 完整前后端分离架构，支持WebSocket和HTTP fallback，实时流式响应 | 与FastAPI天然契合，示例完善 |
| **LangChat** | https://github.com/tycoding/langchat | - | 本地AI大模型部署，知识库定制，企业机器人构建，流式输出支持 | 支持，实现OpenAI兼容接口 |
| **Svelte Chat** | https://github.com/vercel/ai-chatbot-svelte | - | 流式输出支持，轻量级架构，响应式设计，实时通信 | 支持，修改API端点为FastAPI地址 |
| **ChatFlow (LangFlow)** | https://github.com/langflow-ai/langflow | - | 拖拽式工作流构建，多代理对话管理，RAG支持，零代码开发 | 支持，与FastAPI集成 |
| **CopilotKit** | https://github.com/copilotkit/copilotkit | - | 提供完整的聊天窗口组件，支持流式响应和上下文管理，内置提示组件 | 支持，通过`runtimeUrl`配置FastAPI地址 |
| **Ant Design X** | https://github.com/ant-design/ant-design | - | ChatGPT风格界面，多轮对话支持，消息编辑功能，暗黑模式 | 支持，通过`onRequest`回调调用FastAPI |
| **ChatUI (字节跳动)** | https://github.com/chatui/chatui | - | 高度可定制的聊天窗口组件，支持流式消息，Vue3/React双框架兼容 | 支持，需自行实现API对接逻辑 |
| **OpenChat UI** | https://github.com/openchat-ui/openchat-ui | - | 多租户/多用户权限管理，支持主流LLM，内置RAG能力 | 支持，通过配置文件设置API地址 |
| **NLUX** | https://github.com/nluxai/nlux | - | 支持React和Vanilla JS，适配多种LLM，流式响应支持，无外部依赖 | 支持，通过适配器配置FastAPI |
| **Flowise UI** | https://github.com/FlowiseAI/Flowise | - | 拖拽式可视化编辑器，内置数百个LLM/向量库/工具组件，一键导出API | 支持，添加「Custom API」组件配置FastAPI |
| **ChatUI (阿里开源)** | https://github.com/alibaba/chatui | - | 高度可定制的聊天窗口组件，支持流式消息，与阿里生态系统无缝集成 | 支持，需自行实现API对接逻辑 |
| **Angular Chatbot** | - | - | 完整的组件体系，流式输出支持，响应式设计，企业级安全性 | 支持，通过Angular HTTP客户端调用FastAPI

