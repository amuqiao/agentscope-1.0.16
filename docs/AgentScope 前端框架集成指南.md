# AgentScope 前端框架集成指南

## 一、框架概述

本文档整理了适合与 AgentScope 集成的前端 AI 框架，重点关注框架的功能特性、与 AgentScope 的集成适配性以及具体的集成方式。

## 二、核心功能需求

根据用户需求，前端 AI 框架应具备以下核心功能：

- ✅ **流式输出**：实时显示 AI 生成的内容
- ✅ **用户登录注册**：完整的用户认证系统
- ✅ **消息管理**：复制、点赞等交互功能
- ✅ **语音功能**：语音输入输出支持
- ✅ **多模型支持**：兼容不同 AI 模型
- ✅ **聊天历史管理**：保存和管理对话历史

## 三、推荐前端框架

### 1. NextChat (原 ChatGPT Next Web)

**技术栈**：React + TypeScript + Next.js

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 用户登录注册系统
- ✅ 消息复制功能
- ✅ 消息点赞功能
- ✅ 语音输入支持
- ✅ 多模型支持
- ✅ 聊天历史管理
- ✅ 完整 Markdown 渲染
- ✅ 暗色/亮色主题
- ✅ 插件系统

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：通过环境变量 `OPENAI_API_BASE_URL` 直接指向 AgentScope 服务
- **通信协议**：支持 REST API 和 WebSocket
- **适配程度**：★★★★★

**适用场景**：中大型应用，需要完整用户系统的项目

### 2. LobeChat

**技术栈**：React + TypeScript + Next.js

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 用户登录注册系统
- ✅ 消息复制功能
- ✅ 消息点赞功能
- ✅ 语音合成/识别
- ✅ 多模态交互
- ✅ 多模型支持
- ✅ 聊天历史管理
- ✅ 可扩展插件系统

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：修改 API 端点为 AgentScope 服务地址
- **通信协议**：支持 REST API 和 WebSocket
- **适配程度**：★★★★☆

**适用场景**：需要丰富交互功能的中大型应用

### 3. LibreChat

**技术栈**：React + TypeScript

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 用户登录注册系统
- ✅ 消息复制功能
- ✅ 消息点赞功能
- ✅ 语音支持
- ✅ 15+ AI 提供商支持
- ✅ 聊天历史管理
- ✅ 企业级认证

**与 AgentScope 集成适配性**：
- **集成难度**：中
- **集成方式**：添加自定义 API 端点指向 AgentScope 服务
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：企业级应用，需要多模型支持的项目

**GitHub地址**：https://github.com/danny-avila/LibreChat

### 4. Chatbot UI (Mckay Wrigley)

**技术栈**：React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 消息复制功能
- ✅ 消息点赞功能
- ✅ 1:1 复刻 ChatGPT 原生界面
- ✅ 多会话管理
- ✅ 本地存储对话记录

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：直接修改 API 调用地址指向 AgentScope 服务
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：小型项目，快速部署的应用

### 5. Chainlit

**技术栈**：Python

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 消息复制功能
- ✅ 多模态交互
- ✅ 无需前端知识
- ✅ 与 LangChain 等无缝集成

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：与 AgentScope 直接集成，无需额外配置
- **通信协议**：内置通信机制
- **适配程度**：★★★★★

**适用场景**：Python 开发者，快速原型设计

### 6. NLUX

**技术栈**：React / 原生 JavaScript

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 消息复制功能
- ✅ 适配多种 LLM
- ✅ 无外部依赖
- ✅ 轻量级集成

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：通过适配器配置 AgentScope 地址
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：嵌入式应用，小型项目

**GitHub地址**：https://github.com/nluxai/nlux

### 7. Open WebUI

**技术栈**：React + TypeScript

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 零代码搭建AI界面
- ✅ 自动识别本地Ollama模型
- ✅ 支持OpenAI兼容API
- ✅ 企业级安全
- ✅ 内置RAG

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：实现`/v1/chat/completions`和`/v1/models`端点
- **通信协议**：支持 REST API
- **适配程度**：★★★★★

**适用场景**：需要本地模型支持的应用，企业级项目

**GitHub地址**：https://github.com/Open-Webui/Open-Webui

### 8. Onyx (前Danswer)

**技术栈**：React + Python

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 企业级AI搜索与聊天平台
- ✅ 支持40+知识源连接
- ✅ 内置RAG功能
- ✅ 企业级认证

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：原生使用FastAPI作为后端
- **通信协议**：支持 REST API
- **适配程度**：★★★★★

**适用场景**：企业级应用，需要强大搜索能力的项目

**GitHub地址**：https://github.com/onyx-dot-app/onyx

### 9. ChatGPT Web

**技术栈**：Vue 3 + Express

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 基于Express和Vue3的ChatGPT页面复刻
- ✅ 双模型支持
- ✅ 多会话管理

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：实现OpenAI兼容接口
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：小型项目，快速部署的应用

**GitHub地址**：https://github.com/chatgpt-web-dev/chatgpt-web

### 10. Assistant UI

**技术栈**：TypeScript + React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ TypeScript/React组件库
- ✅ 自动处理流式响应
- ✅ 完全可组合的原语

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：实现`/api/chat`接口
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要高度定制化的项目，嵌入式应用

**GitHub地址**：https://github.com/assistant-ui/assistant-ui

### 11. Open Chat Ai

**技术栈**：React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 下一代React聊天机器人
- ✅ 支持任意LLM提供商
- ✅ 多种人格风格

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：实现`/v1/chat/completions`接口
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：中小型应用，需要灵活LLM选择的项目

**GitHub地址**：https://github.com/suneelkumarr/Open-Chat-Ai

### 12. AI Chat Assistant

**技术栈**：React + Node.js

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 完整前后端分离架构
- ✅ 支持WebSocket和HTTP fallback
- ✅ 实时流式响应

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：与FastAPI天然契合，示例完善
- **通信协议**：支持 WebSocket 和 REST API
- **适配程度**：★★★★☆

**适用场景**：需要实时通信的应用

**GitHub地址**：https://github.com/flyryan/ai-chat

### 13. LangChat

**技术栈**：Vue + TypeScript

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 本地AI大模型部署
- ✅ 知识库定制
- ✅ 企业机器人构建

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：实现OpenAI兼容接口
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要本地部署AI模型的企业应用

**GitHub地址**：https://github.com/tycoding/langchat

### 14. Svelte Chat

**技术栈**：Svelte + TypeScript

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 轻量级架构
- ✅ 响应式设计
- ✅ 实时通信

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：修改API端点为FastAPI地址
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要高性能、轻量级聊天界面的项目

**GitHub地址**：https://github.com/vercel/ai-chatbot-svelte

### 15. ChatFlow (LangFlow)

**技术栈**：React + Python

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 拖拽式工作流构建
- ✅ 多代理对话管理
- ✅ RAG支持
- ✅ 零代码开发

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：与FastAPI集成
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要构建复杂AI工作流的项目

**GitHub地址**：https://github.com/langflow-ai/langflow

### 16. CopilotKit

**技术栈**：React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 提供完整的聊天窗口组件
- ✅ 支持流式响应和上下文管理
- ✅ 内置提示组件

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：通过`runtimeUrl`配置FastAPI地址
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要嵌入聊天功能的现有应用

**GitHub地址**：https://github.com/copilotkit/copilotkit

### 17. Ant Design X

**技术栈**：React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ ChatGPT风格界面
- ✅ 多轮对话支持
- ✅ 消息编辑功能
- ✅ 暗黑模式

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：通过`onRequest`回调调用FastAPI
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：企业级应用，需要统一设计风格的项目

**GitHub地址**：https://github.com/ant-design/ant-design

### 18. ChatUI (字节跳动)

**技术栈**：Vue3 / React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 高度可定制的聊天窗口组件
- ✅ 支持流式消息
- ✅ Vue3/React双框架兼容

**与 AgentScope 集成适配性**：
- **集成难度**：中
- **集成方式**：需自行实现API对接逻辑
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要高度定制化聊天界面的项目

**GitHub地址**：https://github.com/chatui/chatui

### 19. OpenChat UI

**技术栈**：React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 多租户/多用户权限管理
- ✅ 支持主流LLM
- ✅ 内置RAG能力

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：通过配置文件设置API地址
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：企业级应用，需要多用户管理的项目

**GitHub地址**：https://github.com/openchat-ui/openchat-ui

### 20. Flowise UI

**技术栈**：React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 拖拽式可视化编辑器
- ✅ 内置数百个LLM/向量库/工具组件
- ✅ 一键导出API

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：添加「Custom API」组件配置FastAPI
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要可视化构建AI工作流的项目

**GitHub地址**：https://github.com/FlowiseAI/Flowise

### 21. ChatUI (阿里开源)

**技术栈**：React

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 高度可定制的聊天窗口组件
- ✅ 支持流式消息
- ✅ 与阿里生态系统无缝集成

**与 AgentScope 集成适配性**：
- **集成难度**：中
- **集成方式**：需自行实现API对接逻辑
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：需要与阿里生态系统集成的项目

**GitHub地址**：https://github.com/alibaba/chatui

### 22. Angular Chatbot

**技术栈**：Angular + TypeScript

**核心功能**：
- ✅ 流式输出（Stream）
- ✅ 完整的组件体系
- ✅ 响应式设计
- ✅ 企业级安全性

**与 AgentScope 集成适配性**：
- **集成难度**：低
- **集成方式**：通过Angular HTTP客户端调用FastAPI
- **通信协议**：支持 REST API
- **适配程度**：★★★★☆

**适用场景**：企业级应用，需要严格类型安全的项目

**GitHub地址**：https://github.com/ChatBot-All/angular-chatbot

## 四、AgentScope 集成方式

### 1. 前后端分离架构

**架构组成**：
- **前端**：选择上述框架之一
- **后端**：AgentScope 智能体服务
- **API 层**：FastAPI 或 Flask 创建的 API 服务
- **认证**：JWT 或 OAuth2 实现用户认证

### 2. 具体集成步骤

#### 前端配置
1. **API 端点配置**：
   - NextChat：设置 `OPENAI_API_BASE_URL` 环境变量
   - LobeChat：修改 API 端点配置
   - 其他框架：配置相应的 API 地址

2. **认证配置**：
   - 配置登录注册界面
   - 实现 JWT 令牌管理
   - 处理认证状态

3. **流式输出配置**：
   - 确保前端支持 SSE 或 WebSocket
   - 配置流式响应处理

#### 后端集成
1. **API 服务搭建**：
   ```python
   from fastapi import FastAPI
   from fastapi.middleware.cors import CORSMiddleware
   from fastapi.responses import StreamingResponse
   
   app = FastAPI()
   
   # CORS 配置
   app.add_middleware(
       CORSMiddleware,
       allow_origins=["*"],
       allow_credentials=True,
       allow_methods=["*"],
       allow_headers=["*"],
   )
   ```

2. **AgentScope 集成**：
   ```python
   from agentscope.agent import ReActAgent
   from agentscope.model import OpenAIChatModel
   from agentscope.memory import InMemoryMemory
   
   # 创建智能体
   agent = ReActAgent(
       name="assistant",
       sys_prompt="You're a helpful assistant.",
       model=OpenAIChatModel(
           model_name="gpt-4",
           api_key="YOUR_API_KEY",
       ),
       memory=InMemoryMemory(),
   )
   ```

3. **流式响应实现**：
   ```python
   async def stream_response(user_message):
       # 流式调用 AgentScope 智能体
       async for chunk in agent.stream_chat(user_message):
           yield f"data: {json.dumps({'content': chunk})}\n\n"
       yield "data: [DONE]\n\n"
   
   @app.post("/v1/chat/completions")
   async def chat_completions(request: dict):
       user_message = request["messages"][-1]["content"]
       return StreamingResponse(
           stream_response(user_message),
           media_type="text/event-stream"
       )
   ```

### 3. 通信协议

| 协议类型 | 适用场景 | 实现方式 |
|---------|---------|----------|
| **SSE (Server-Sent Events)** | 单向流式输出 | FastAPI `StreamingResponse` |
| **WebSocket** | 双向实时通信 | FastAPI WebSocket 支持 |
| **REST API** | 同步操作 | 标准 HTTP 请求 |

## 五、功能特性对比

### 核心功能对比表

| 框架名称 | 流式输出 | 登录注册 | 消息复制 | 消息点赞 | 语音功能 | 多模型支持 | 聊天历史 | 集成难度 | GitHub地址 |
|---------|---------|---------|---------|---------|---------|-----------|---------|----------|------------|
| **NextChat** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/Yidadaa/ChatGPT-Next-Web |
| **LobeChat** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/lobehub/lobe-chat |
| **LibreChat** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 中 | https://github.com/danny-avila/LibreChat |
| **Chatbot UI** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 低 | https://github.com/mckaywrigley/chatbot-ui |
| **Chainlit** | ✅ | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ | 低 | https://github.com/Chainlit/chainlit |
| **NLUX** | ✅ | ❌ | ✅ | ❌ | ❌ | ✅ | ❌ | 低 | https://github.com/nluxai/nlux |
| **Open WebUI** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/Open-Webui/Open-Webui |
| **Onyx** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/onyx-dot-app/onyx |
| **ChatGPT Web** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 低 | https://github.com/chatgpt-web-dev/chatgpt-web |
| **Assistant UI** | ✅ | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ | 低 | https://github.com/assistant-ui/assistant-ui |
| **Open Chat Ai** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 低 | https://github.com/suneelkumarr/Open-Chat-Ai |
| **AI Chat Assistant** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/flyryan/ai-chat |
| **LangChat** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/tycoding/langchat |
| **Svelte Chat** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 低 | https://github.com/vercel/ai-chatbot-svelte |
| **ChatFlow** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/langflow-ai/langflow |
| **CopilotKit** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 低 | https://github.com/copilotkit/copilotkit |
| **Ant Design X** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 低 | https://github.com/ant-design/ant-design |
| **ChatUI (字节跳动)** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 中 | https://github.com/chatui/chatui |
| **OpenChat UI** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/openchat-ui/openchat-ui |
| **Flowise UI** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/FlowiseAI/Flowise |
| **ChatUI (阿里开源)** | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | 中 | https://github.com/alibaba/chatui |
| **Angular Chatbot** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | 低 | https://github.com/ChatBot-All/angular-chatbot |

### 技术栈对比

| 框架名称 | 技术栈 | GitHub 星数 | 社区活跃度 |
|---------|-------|------------|------------|
| **Open WebUI** | React + TypeScript | 90,900+ | 高 |
| **NextChat** | React + TypeScript + Next.js | 86,000+ | 高 |
| **LobeChat** | React + TypeScript + Next.js | 67,000+ | 高 |
| **LibreChat** | React + TypeScript | 20,000+ | 中 |
| **Onyx** | React + Python | 17,000+ | 中 |
| **ChatGPT Web** | Vue 3 + Express | 15,000+ | 中 |
| **Chatbot UI** | React | 20,000+ | 中 |
| **Chainlit** | Python | 11,400+ | 中 |
| **Assistant UI** | TypeScript + React | 7,500+ | 中 |
| **Open Chat Ai** | React | 5,000+ | 中 |
| **AI Chat Assistant** | React + Node.js | 3,000+ | 中 |
| **NLUX** | React / 原生 JavaScript | - | 中 |
| **LangChat** | Vue + TypeScript | - | 中 |
| **Svelte Chat** | Svelte + TypeScript | - | 中 |
| **ChatFlow** | React + Python | - | 中 |
| **CopilotKit** | React | - | 中 |
| **Ant Design X** | React | - | 高 |
| **ChatUI (字节跳动)** | Vue3 / React | - | 中 |
| **OpenChat UI** | React | - | 中 |
| **Flowise UI** | React | - | 中 |
| **ChatUI (阿里开源)** | React | - | 中 |
| **Angular Chatbot** | Angular + TypeScript | - | 中 |

## 六、部署策略

### 1. 容器化部署

**Docker 配置示例**：
```dockerfile
# 前端 Dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]

# 后端 Dockerfile
FROM python:3.10-alpine
WORKDIR /app
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### 2. 部署架构

- **前端**：静态文件部署（Vercel、Netlify 等）
- **后端**：云服务器或容器服务（AWS、GCP、阿里云等）
- **数据库**：MySQL、PostgreSQL 等（用于用户数据和聊天历史）

## 七、推荐选择

### 最佳适配框架

1. **NextChat**：最推荐，功能完整，集成简单，界面体验优秀
2. **LobeChat**：功能丰富，支持多模态交互，适合需要语音功能的项目
3. **Open WebUI**：零代码搭建AI界面，自动识别本地Ollama模型，适合本地部署场景
4. **Chainlit**：对 Python 开发者友好，无需前端知识，快速原型设计
5. **Chatbot UI**：轻量级，易于定制，适合小型项目
6. **NLUX**：嵌入式集成，适合现有应用添加 AI 功能
7. **Onyx**：企业级AI搜索与聊天平台，支持40+知识源连接，适合需要强大搜索能力的项目
8. **LangChat**：支持本地AI大模型部署，适合企业内部应用
9. **Svelte Chat**：性能优异，加载速度快，适合构建轻量级聊天应用
10. **ChatFlow (LangFlow)**：可视化工作流构建，适合构建复杂AI工作流的项目

### 场景推荐

| 场景 | 推荐框架 | 理由 |
|------|---------|------|
| **企业级应用** | LibreChat、LobeChat、Onyx、OpenChat UI | 完整的用户系统，多模型支持，企业级认证，强大的搜索能力 |
| **中大型项目** | NextChat、LobeChat、Open WebUI | 功能丰富，界面美观，社区活跃，支持本地模型 |
| **小型项目** | Chatbot UI、NLUX、Svelte Chat | 快速部署，轻量级集成，性能优异 |
| **Python 开发者** | Chainlit | 无需前端知识，与 AgentScope 天然契合 |
| **嵌入式应用** | NLUX、Assistant UI、CopilotKit | 轻量级，易于集成到现有系统 |
| **本地模型部署** | Open WebUI、LangChat | 自动识别本地Ollama模型，支持本地部署 |
| **复杂AI工作流** | ChatFlow (LangFlow)、Flowise UI | 可视化工作流构建，零代码开发 |
| **搜索增强应用** | Onyx | 支持40+知识源连接，内置RAG功能 |
| **实时通信需求** | AI Chat Assistant | 支持WebSocket和HTTP fallback，实时流式响应 |
| **企业内部应用** | LangChat、Angular Chatbot | 本地AI大模型部署，企业级安全性 |

## 八、集成示例

### NextChat 与 AgentScope 集成

1. **前端配置**：
   ```env
   # .env.local
   OPENAI_API_BASE_URL=http://your-agentscope-server:8000/v1
   OPENAI_API_KEY=sk-placeholder
   ```

2. **后端 API 实现**：
   ```python
   # main.py
   from fastapi import FastAPI
   from fastapi.middleware.cors import CORSMiddleware
   from fastapi.responses import StreamingResponse
   import json
   import asyncio
   
   from agentscope.agent import ReActAgent
   from agentscope.model import OpenAIChatModel
   
   app = FastAPI()
   
   # CORS 配置
   app.add_middleware(
       CORSMiddleware,
       allow_origins=["*"],
       allow_credentials=True,
       allow_methods=["*"],
       allow_headers=["*"],
   )
   
   # 初始化 AgentScope 智能体
   agent = ReActAgent(
       name="assistant",
       sys_prompt="You're a helpful assistant.",
       model=OpenAIChatModel(
           model_name="gpt-4",
           api_key="YOUR_API_KEY",
       ),
   )
   
   @app.post("/v1/chat/completions")
   async def chat_completions(request: dict):
       messages = request.get("messages", [])
       user_message = messages[-1]["content"]
       
       async def stream_generator():
           async for chunk in agent.stream_chat(user_message):
               await asyncio.sleep(0.1)
               yield f"data: {json.dumps({'choices': [{'delta': {'content': chunk}}]})}\n\n"
           yield "data: [DONE]\n\n"
       
       return StreamingResponse(stream_generator(), media_type="text/event-stream")
   ```

## 九、总结

选择适合的前端框架与 AgentScope 集成，需要考虑以下因素：

1. **功能需求**：根据项目需要的功能特性选择
2. **技术栈**：考虑开发团队的技术背景
3. **集成难度**：评估与 AgentScope 的适配程度
4. **部署环境**：考虑部署平台和资源限制
5. **社区支持**：选择社区活跃、维护良好的框架

通过合理选择前端框架并正确集成 AgentScope，可以快速构建功能完善、用户体验良好的 AI 聊天应用。