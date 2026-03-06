> 本文档详细介绍如何使用 uv 工具安装虚拟环境、指定 Python 版本、安装项目依赖、配置模型以及启动服务。

## 1. 安装 uv 工具

如果您尚未安装 uv，可以通过以下命令安装：

```bash
# 使用 pip 安装 uv
pip install uv

# 或者使用官方安装脚本
curl -Ls https://astral.sh/uv/install.sh | sh
```

## 2. 创建虚拟环境并指定 Python 版本

根据项目的 `pyproject.toml` 文件，AgentScope 需要 Python 3.10 或更高版本。使用 uv 创建虚拟环境并指定 Python 版本：

```bash
# 在项目根目录创建虚拟环境，指定 Python 3.10
uv venv --python 3.10

# 激活虚拟环境
source .venv/bin/activate  # macOS/Linux
# 或
source .venv/Scripts/activate # Windows
```

## 3. 安装项目依赖

### 3.1 安装基本依赖

**为什么使用可编辑模式安装**：
- **功能**：`-e` 参数表示以可编辑模式安装项目，创建源码的符号链接而非复制
- **作用**：修改源码后立即生效，无需重新安装，提高开发效率
- **必要性**：开发过程中需要频繁修改源码时，可编辑模式能确保环境直接使用最新代码
- **示例依赖**：`examples` 目录下的所有示例代码均依赖 agentscope 包，可编辑模式确保示例能使用本地修改后的代码

使用国内镜像安装基本依赖，避免网络连接问题：

```bash
# 使用阿里云 PyPI 镜像安装基本依赖
uv pip install -e . --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```

### 3.2 安装实时功能依赖

如果需要运行实时语音智能体服务，安装实时功能依赖：

**为什么使用 `.[realtime]` 语法**：
- `realtime` 是在 `pyproject.toml` 中定义的可选依赖组
- 该依赖组包含 `websockets>=14.0` 和 `scipy` 两个包
- `.[realtime]` 语法告诉包管理器安装项目的同时，额外安装 `realtime` 依赖组中的所有包

```bash
# 安装实时功能依赖
uv pip install -e ".[realtime]" --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```

### 3.3 安装 Web 服务依赖

实时语音智能体服务需要 FastAPI 和 Uvicorn：

```bash
# 安装 FastAPI 和 Uvicorn
uv pip install fastapi uvicorn --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```

### 3.4 安装 A2A 功能依赖

如果需要运行 A2A 智能体服务，安装 A2A 功能依赖：

```bash
# 安装 A2A 功能依赖
uv pip install -e ".[a2a]" --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```

### 3.5 安装完整依赖（可选）

如果需要所有功能，可以安装完整依赖：

```bash
# 安装完整依赖
uv pip install -e ".[full]" --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```

## 4. 模型配置

### 4.1 模型配置路径

AgentScope 的模型配置主要通过以下文件实现：

- **模型基类**：`src/agentscope/model/_model_base.py`
- **OpenAI 模型**：`src/agentscope/model/_openai_model.py`
- **Anthropic 模型**：`src/agentscope/model/_anthropic_model.py`
- **Gemini 模型**：`src/agentscope/model/_gemini_model.py`
- **DashScope 模型**（包含 Qwen 模型）：`src/agentscope/model/_dashscope_model.py`
- **Ollama 模型**：`src/agentscope/model/_ollama_model.py`
- **全局配置**：`src/agentscope/_run_config.py`

### 4.2 配置方法

#### 方法一：通过环境变量配置

1. **设置环境变量**：
   - **永久设置**（推荐）：
     - 在 macOS/Linux 中，在 `.bashrc` 或 `.zshrc` 文件中添加：
       ```bash
       # OpenAI 模型
       export OPENAI_API_KEY="your-openai-api-key"
       
       # Anthropic 模型
       export ANTHROPIC_API_KEY="your-anthropic-api-key"
       
       # Gemini 模型
       export GOOGLE_API_KEY="your-google-api-key"
       
       # DashScope 模型（Qwen）
       export DASHSCOPE_API_KEY="your-dashscope-api-key"
       
       # Ollama 模型（可选）
       export OLLAMA_BASE_URL="http://localhost:11434"
       ```
     - 在 Windows 中，通过系统属性设置环境变量。
   - **临时设置**（仅当前终端有效）：
     - 在 macOS/Linux 中，直接在终端中运行：
       ```bash
       export DASHSCOPE_API_KEY="your-dashscope-api-key"
       ```

2. **使用模型**：
   ```python
   from agentscope.model import OpenAIChatModel, DashScopeChatModel

   # 自动从环境变量读取配置
   openai_model = OpenAIChatModel(model_name="gpt-4o")
   qwen_model = DashScopeChatModel(model_name="qwen-plus")
   ```

3. **验证配置**：
   创建并运行测试脚本验证模型配置是否成功：
   ```python
   # test_qwen_model.py
   import asyncio
   import os
   from agentscope.model import DashScopeChatModel

   async def test_qwen_model():
       # 创建 Qwen 模型实例
       model = DashScopeChatModel(
           model_name="qwen-plus",
           api_key=os.getenv("DASHSCOPE_API_KEY")
       )

       # 测试模型生成
       print("Testing Qwen model...")
       # 创建消息列表
       messages = [{"role": "user", "content": "你好，Qwen！请介绍一下你自己。"}]
       # 异步调用模型
       response = await model(messages)
       print("Response:")
       # 处理异步生成器
       async for chunk in response:
           if hasattr(chunk, 'text'):
               print(chunk.text)

   if __name__ == "__main__":
       asyncio.run(test_qwen_model())
   ```

   运行测试脚本：
   ```bash
   python test_qwen_model.py
   ```

   若配置成功，您将看到 Qwen 模型的自我介绍响应。

#### 方法二：在代码中直接配置

您可以在项目的任何 Python 文件中直接配置模型，常见的位置包括：

- **示例代码文件**：`examples/agent/react_agent/main.py`、`examples/agent/realtime_voice_agent/run_server.py` 等
- **自定义应用文件**：您创建的任何 Python 脚本或模块

```python
from agentscope.model import OpenAIChatModel, DashScopeChatModel

# 配置 OpenAI 模型
openai_model = OpenAIChatModel(
    model_name="gpt-4o",
    api_key="your-openai-api-key",
    base_url="https://api.openai.com/v1"  # 可选
)

# 配置 Qwen 模型
qwen_model = DashScopeChatModel(
    model_name="qwen-plus",
    api_key="your-dashscope-api-key"
)

# 使用模型进行推理
import asyncio

async def test_model():
    messages = [{"role": "user", "content": "你好，Qwen！请介绍一下你自己。"}]
    response = await qwen_model(messages)
    async for chunk in response:
        if hasattr(chunk, 'text'):
            print(chunk.text)

asyncio.run(test_model())
```

**示例文件位置**：
- `examples/agent/react_agent/main.py`：React 智能体示例
- `examples/agent/realtime_voice_agent/run_server.py`：实时语音智能体服务
- `examples/agent/a2a_agent/main.py`：A2A 智能体客户端
- `examples/agent/deep_research_agent/main.py`：深度研究智能体示例

#### 方法三：使用配置文件

AgentScope 支持通过 `init` 函数加载配置文件，配置文件可以放在以下位置：

1. **自定义路径**：您可以指定任何路径，如项目根目录或配置目录
2. **默认路径**：如果不指定路径，AgentScope 会在当前工作目录查找 `config.json` 文件

```python
import agentscope

# 加载自定义路径的配置文件
agentscope.init(config="config/config.json")  # 相对路径
# 或
agentscope.init(config="/absolute/path/to/config.json")  # 绝对路径

# 加载默认路径的配置文件（当前工作目录下的 config.json）
agentscope.init()

# 然后使用模型
from agentscope.model import OpenAIModel
model = OpenAIModel(model="gpt-4o")
```

配置文件示例 (`config.json`)：

```json
{
  "model": {
    "openai": {
      "api_key": "your-api-key",
      "base_url": "https://api.openai.com/v1"
    },
    "dashscope": {
      "api_key": "your-dashscope-key"
    },
    "gemini": {
      "api_key": "your-google-api-key"
    },
    "anthropic": {
      "api_key": "your-anthropic-api-key"
    },
    "ollama": {
      "base_url": "http://localhost:11434"
    }
  }
}
```

**推荐配置文件路径**：
- 项目根目录：`./config.json`
- 配置目录：`./config/config.json`
- 环境特定配置：`./config/production.json` 或 `./config/development.json`

## 5. 启动服务

### 5.1 启动实时语音智能体服务

```bash
# 进入实时语音智能体示例目录
cd examples/agent/realtime_voice_agent

# 启动服务
python run_server.py
```

服务启动后，您应该能看到类似以下输出：

```
INFO:     Started server process [12345]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)
```

### 5.2 启动 A2A 智能体服务

A2A 智能体服务需要先启动服务器，然后再运行客户端：

1. **启动 A2A 服务器**：
   ```bash
   # 进入 A2A 智能体示例目录
   cd examples/agent/a2a_agent
   
   # 启动 A2A 服务器
   uvicorn setup_a2a_server:app --host 0.0.0.0 --port 8000
   ```

2. **运行 A2A 客户端**：
   ```bash
   # 在另一个终端中进入 A2A 智能体示例目录
   cd examples/agent/a2a_agent
   
   # 运行客户端
   python main.py
   ```

### 5.3 启动其他服务

#### 启动多智能体实时交互服务

```bash
# 进入多智能体实时交互示例目录
cd examples/workflows/multiagent_realtime

# 启动服务
python run_server.py
```

服务启动后，您应该能看到类似以下输出：

```
INFO:     Will watch for changes in these directories: ['/path/to/agentscope/examples/workflows/multiagent_realtime']
INFO:     Uvicorn running on http://localhost:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [12345] using WatchFiles
INFO:     Started server process [67890]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

**验证服务**：
- 服务成功启动后，访问 http://localhost:8000 可以查看服务状态
- 服务运行正常，无错误信息

## 6. 验证配置

### 6.1 验证服务启动

服务启动后，查看终端输出，确保没有错误信息，并且服务正在运行。

### 6.2 验证 AgentScope 安装

```bash
# 检查 AgentScope 版本
python -c "import agentscope; print(agentscope.__version__)"

# 运行简单示例
python examples/agent/react_agent/main.py
```

### 6.3 验证模型配置

```python
from agentscope.model import DashScopeModel

# 创建 Qwen 模型实例
model = DashScopeModel(model="qwen-plus")

# 测试模型生成
response = model.generate("Hello, Qwen! Tell me about AgentScope.")
print(response.text)
```

## 7. 故障排除

### 7.1 网络连接问题

如果遇到网络连接问题，可以尝试：
- 使用不同的 PyPI 镜像（如清华大学镜像）
- 检查网络连接和防火墙设置
- 尝试使用代理服务器

### 7.2 依赖缺失问题

如果遇到依赖缺失问题，可以：
- 检查错误信息中提到的缺失包
- 使用 `uv pip install` 命令安装缺失的依赖
- 确保安装了所有必要的可选依赖

### 7.3 端口占用问题

如果遇到端口占用问题，可以：
- 修改服务代码中的端口号
- 停止占用该端口的其他进程

### 7.4 A2A 服务错误

如果遇到 A2A 服务的 405 Method Not Allowed 错误：
- 确保 A2A 服务器正在运行
- 按照正确的顺序启动服务（先启动服务器，再运行客户端）
- 检查服务器 URL 配置是否正确

## 8. 完整命令序列

以下是完整的命令序列，从创建虚拟环境到启动服务：

```bash
# 1. 安装 uv
pip install uv

# 2. 创建虚拟环境
uv venv --python 3.10

# 3. 激活虚拟环境
source .venv/bin/activate

# 4. 安装基本依赖
uv pip install -e . --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com

# 5. 安装实时功能依赖
uv pip install -e ".[realtime]" --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com

# 6. 安装 Web 服务依赖
uv pip install fastapi uvicorn --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com

# 7. 安装完整依赖
uv pip install -e ".[full]" --index-url https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com

# 8. 启动实时语音智能体服务
cd examples/agent/realtime_voice_agent
python run_server.py
```