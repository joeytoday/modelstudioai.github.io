---
layout: doc
title: Workshop
permalink: /workshop/
---

# 阿里云百炼 CLI 动手实验

欢迎参加 6.11 阿里云百炼 CLI 线下分享会！本页是你的全程操作指引——按步骤从零搭建一个**节点式 AI 自媒体工作流编辑器**。

> **预计用时：90 分钟** | 现场 tokens 管够，放心使用。

---

## 演示项目：Maidan-Studio

**节点式 AI 自媒体工作流编辑器** — 自媒体内容生产的 ComfyUI。

把「选题 → 文案 → 平台分发 → 封面 → 多页内容图」这条自媒体内容生产链路，变成可拖拽、可编排、可保存为模板的可视化工作流。

| 项目 | 说明 |
|------|------|
| 仓库地址 | [github.com/CzzzzzzJ/bailian-cli](https://github.com/CzzzzzzJ/bailian-cli) |
| 作者 | 麦当mdldm（[@CzzzzzzJ](https://github.com/CzzzzzzJ)） |
| 技术栈 | Next.js 15 + React Flow + Supabase + 阿里云百炼 CLI（bl） |

**两条内置生产线：**

| 模板 | 流水线 |
|------|--------|
| 小红书日更-轻量版 | 关键词 → 选题搜索 → 多维评分 → 选 1 → 脚本生成 → 三平台改写 + 封面 |
| Omi 小红书图文-精装版 | 素材 → 笔记导演 → 资产看板 → 封面 + 多页内容图 |

---

## Step 1：获取阿里云百炼 API Key

点击下方链接，注册/登录阿里云百炼平台并创建 API Key：

👉 [获取 API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

操作步骤：

1. 点击链接，使用阿里云账号登录（支持支付宝/钉钉扫码）
2. 进入「API-KEY 管理」页面
3. 点击「创建新的 API Key」
4. 复制生成的 Key（格式为 `sk-xxxxxxxxxxxxxxxx`），保存好备用

> 没有阿里云账号？注册是免费的，新用户默认有免费调用额度。

---

## Step 2：安装阿里云百炼 CLI

```bash
npm install -g bailian-cli
```

> 需要 Node.js >= 22.12

安装后确认：

```bash
bl --version
```

### 配置 API Key

```bash
bl auth login --api-key sk-xxxxx
```

或通过环境变量：

```bash
export DASHSCOPE_API_KEY=sk-xxxxx
```

### 快速测试

```bash
# 聊天测试
bl text chat --message "你好，自我介绍一下"

# 生成图片
bl image generate --prompt "一只穿宇航服的猫" --out-dir ./images/
```

> 阿里云百炼 CLI 为 AI Agent 而生，每条命令即工具调用。除了终端直接使用外，也可在 Cursor、Qwen Code、Claude Desktop、Windsurf、Cline 等主流 AI Agent 框架中作为工具集成。

---

## Step 3：克隆演示项目

```bash
git clone https://github.com/CzzzzzzJ/bailian-cli.git
cd bailian-cli
pnpm install
```

> 前置依赖：Node.js >= 22.12、pnpm >= 9

---

## Step 4：配置环境

复制 `.env.example` 到 `.env.local`：

```env
# 阿里云百炼
DASHSCOPE_API_KEY=sk-your-key

# Supabase（用于登录 + 模板持久化）
NEXT_PUBLIC_SUPABASE_URL=https://<project>.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

### 数据库迁移

在 Supabase Dashboard → SQL Editor 依次执行：

```bash
supabase/schema.sql        # 8 张表 + 触发器
supabase/policies.sql      # RLS 策略
```

---

## Step 5：启动项目

```bash
pnpm --filter @maidan/web exec next dev --turbopack -p 3030
```

打开 `http://localhost:3030` → 注册账号 → 选择模板 → 修改 PromptTemplate 里的关键词 → 点击运行。

---

## Step 6：动手体验工作流

### 核心玩法

每个节点 = 一个阿里云百炼 CLI 的能力封装；连线 = 数据从上游产物喂给下游。

**节点 → CLI 命令对照：**

| 节点 | 调用命令 | 说明 |
|------|----------|------|
| TopicSearch | `bl text chat`（qwen3.7-max） | 选题搜索，结构化 JSON 输出 |
| ScriptGen | `bl text chat`（qwen3.7-max / qwq-plus） | 脚本生成，开思考链切 qwq-plus |
| CoverGen | `bl image generate`（qwen-image-2.0） | 封面生成 |
| AssetGen | `bl image edit` | 图生图，IP 形象 + 风格 |
| XHSContentGen | `bl image edit`（并行） | 多页内容图并行生成 |

### 操作要点

- **拖图入画布**：直接将图片拖入画布 → 自动上传 → 创建 ImageInput 节点 → 连线到 AssetGen 作为 IP 形象
- **Skill 模板挂载**：节点抽屉里挂载 Skill markdown，运行时自动拼入 system prompt
- **人工审核节点**：流程执行到「人工审核」节点时暂停，等你确认后继续

### 推荐体验路径

1. 选「小红书日更-轻量版」模板
2. 修改 PromptTemplate 中的关键词（比如换成「用 AI 做自媒体」）
3. 点击运行，观察节点逐个变绿
4. 查看产出：选题评分、脚本文案、三平台改写、封面图片
5. 尝试挂载不同的 Skill，对比输出差异

---

## 阿里云百炼 CLI 核心能力一览

除了本演示项目用到的能力，阿里云百炼 CLI 还覆盖：

| 能力 | 命令 | 说明 |
|------|------|------|
| 文本对话 | `bl text chat` | Qwen3.7-max，支持 agentic coding |
| 全模态对话 | `bl omni` | 文本 + 图片 + 音频 + 视频多模态 |
| 图像生成 | `bl image generate` | Qwen-Image 2.0，专业文字渲染 |
| 图像编辑 | `bl image edit` | 图生图、风格迁移、多图合成 |
| 视频生成 | `bl video generate` | HappyHorse-1.0，文/图/参考 → 视频 |
| 语音合成 | `bl speech synthesize` | CosyVoice 流式 TTS + 声音克隆 |
| 语音识别 | `bl speech recognize` | FunAudio-ASR，30 语言覆盖 |
| 图片理解 | `bl vision` | Qwen-VL，长视频分析、文档解析 |
| 知识库 | `bl knowledge retrieve` | 多模态 RAG 检索 |
| 联网搜索 | `bl search` | 实时互联网检索 |
| MCP 集成 | `bl mcp` | 编排百炼 MCP 服务 |
| 模型推荐 | `bl advisor recommend` | 描述场景获取最优模型建议 |

更多命令参考 → [阿里云百炼 CLI 控制台](https://bailian.console.aliyun.com/cli?source_channel=cli_github&)

---

## 常见问题

| 问题 | 解决方案 |
|------|----------|
| `bl: command not found` | 重新安装：`npm install -g bailian-cli`，确保 Node.js >= 22.12 |
| API Key 无效 | 确认 Key 以 `sk-` 开头，在百炼控制台检查是否已激活 |
| 图片生成超时 | 图片生成通常需要 10-30s，耐心等待；如持续超时检查网络 |
| pnpm install 失败 | 确认 pnpm >= 9：`npm install -g pnpm@latest` |
| Supabase 连接失败 | 确认 `.env.local` 中的 URL 和 Key 正确，Supabase 项目已运行 |
| 节点执行报错 | 查看节点状态变 error 后，点击节点查看详情抽屉中的错误信息 |

---

## 社区与资源

- 阿里云百炼 CLI GitHub：[github.com/modelstudioai/cli](https://github.com/modelstudioai/cli)
- 演示项目源码：[github.com/CzzzzzzJ/bailian-cli](https://github.com/CzzzzzzJ/bailian-cli)
- Agent Skills 精选：[github.com/modelstudioai/skills](https://github.com/modelstudioai/skills)
- OpenWork（开源桌面 Agent）：[github.com/modelstudioai/openwork](https://github.com/modelstudioai/openwork)
- [阿里云百炼 CLI 控制台](https://bailian.console.aliyun.com/cli?source_channel=cli_github&) | [获取 API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)
