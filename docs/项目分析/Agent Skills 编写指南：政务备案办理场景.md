# Agent Skills 编写指南：政务备案办理场景

在 AgentScope 中，**Agent Skills** 是领域知识包，通过 `SKILL.md` 文件提供特定任务的专业指导，帮助 Agent 在执行过程中做出正确决策。对于政务备案办理场景，Skills 应包含以下核心内容：

## 一、Skills 的作用

- **提供领域知识**：为 Agent 提供政务办理的专业规则和流程
- **指导工具使用**：明确何时使用何种工具及使用方法
- **规范操作步骤**：定义标准化的执行流程和最佳实践
- **处理异常情况**：提供常见错误的应对策略

## 二、Skills 目录结构

```
skills/
├── gov-filing-login/        # 登录相关知识
│   └── SKILL.md
├── gov-filing-cert/         # 证书上传相关知识
│   └── SKILL.md
└── gov-filing-form/         # 表单填写相关知识
    └── SKILL.md
```

## 三、SKILL.md 内容示例

### 1. 登录技能（gov-filing-login/SKILL.md）

```markdown
---
name: gov-filing-login
description: 政务系统登录策略，包含验证码处理与会话保持方法
---

# 政务系统登录指南

## 登录流程
1. 导航至登录页，等待页面完全加载（使用 browser_snapshot 确认）
2. 定位账号和密码输入框（通常为 type=text 和 type=password）
3. 使用 browser_type 填入凭证
4. 若存在图形验证码，使用 image_understanding 识别验证码文本再填入
5. 点击登录按钮，通过 browser_snapshot 确认跳转成功

## 验证码策略
- 图形验证码：使用 image_understanding 工具，task 参数设为 "读取验证码文字"
- 短信验证码：等待用户输入后继续（可通过 UserAgent 交互）

## 失败处理
- 若登录失败，截图分析错误提示，最多重试 3 次
- 常见错误：账号密码错误、验证码过期、网络超时

## 会话保持
- 登录成功后，保持浏览器会话活跃，避免页面刷新导致会话丢失
- 后续操作前先使用 browser_snapshot 确认登录状态
```

### 2. 证书上传技能（gov-filing-cert/SKILL.md）

```markdown
---
name: gov-filing-cert
description: 备案证上传规范与格式要求
---

# 备案证上传指南

## 文件要求
- 格式：支持 PNG、JPG、PDF 格式
- 大小：不超过 5MB
- 清晰度：确保文字清晰可辨，避免反光和遮挡

## 上传流程
1. 导航至上传页面，定位文件选择控件
2. 使用 browser_file_upload 工具选择本地证书文件
3. 等待上传进度完成，通过 browser_snapshot 确认上传成功
4. 若上传失败，检查文件格式和大小，重试上传

## 常见问题
- 文件格式不支持：转换为 PNG 或 PDF 格式
- 上传超时：检查网络连接，尝试分块上传
- 清晰度不足：重新拍摄或扫描证书

## 状态确认
- 上传后确认系统显示"上传成功"或类似提示
- 若系统生成文件 ID，记录该 ID 用于后续步骤
```

### 3. 表单填写技能（gov-filing-form/SKILL.md）

```markdown
---
name: gov-filing-form
description: 申报表单字段规则与提交规范
---

# 申报表单填写指南

## 字段要求
- 备案证编号：必填，格式为 15 位数字或字母组合
- 公司名称：必填，与营业执照一致
- 有效期：必填，选择证书上的截止日期
- 域名：必填，格式为 example.com
- 联系人信息：必填，包括姓名、电话、邮箱

## 填写流程
1. 从 InMemoryMemory 中读取 OCR 提取的证书字段
2. 逐一填写对应表单字段，使用 browser_type 工具
3. 检查必填项是否完整，格式是否正确
4. 点击提交按钮，等待系统处理

## 校验规则
- 域名格式：必须包含 .com、.cn 等顶级域名
- 日期格式：YYYY-MM-DD
- 电话号码：11 位数字
- 邮箱格式：包含 @ 符号

## 错误处理
- 字段校验失败：根据错误提示修正对应字段
- 提交超时：检查网络连接，重试提交
- 系统错误：截图记录错误信息，等待系统恢复后重试
```

## 四、Skills 如何被 Agent 使用

1. **注册 Skills**：在主程序中通过 `toolkit.register_agent_skill()` 注册
   ```python
   toolkit.register_agent_skill("./skills/gov-filing-login")
   toolkit.register_agent_skill("./skills/gov-filing-cert")
   toolkit.register_agent_skill("./skills/gov-filing-form")
   ```

2. **注入 System Prompt**：Agent 在执行对应阶段前，会读取 Skills 中的知识，注入到推理过程中

3. **指导工具调用**：Skills 中的操作步骤和工具使用建议，会指导 Agent 选择正确的工具和参数

4. **处理异常情况**：Skills 中的错误处理策略，帮助 Agent 在遇到问题时做出合理决策

## 五、编写 Skills 的最佳实践

1. **结构清晰**：使用 Markdown 标题和列表，组织内容层次
2. **步骤具体**：提供详细的操作步骤，包括工具名称和参数
3. **覆盖异常**：考虑各种可能的错误情况和应对策略
4. **语言明确**：使用简洁、直接的语言，避免歧义
5. **定期更新**：根据政务系统的变化，及时更新 Skills 内容

通过编写高质量的 Skills，Agent 可以更准确、高效地执行政务备案办理流程，特别是在处理复杂的表单填写和异常情况时，能够参考领域知识做出正确决策。