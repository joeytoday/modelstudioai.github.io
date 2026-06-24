---
layout: doc
title: 阿里云百炼 CLI
permalink: /cli/
description: "阿里云百炼 CLI（bl）是为 AI Agent 而生的命令行工具——每条命令即结构化工具调用。支持文本对话、图像生成、视频生成、语音合成、视觉理解、MCP、知识检索等 15+ 能力。"
keywords: "百炼 CLI,bailian-cli,bl 命令,AI 命令行,文本对话,图像生成,视频生成,语音合成,Qwen Code,DashScope,MCP,Aliyun Model Studio"
---

# 阿里云百炼 CLI

阿里云百炼 CLI（命令 `bl`）是阿里云百炼官方命令行工具，**为 AI Agent 而生** —— 每条命令即结构化工具调用。覆盖文本、全模态对话、图像与视频生成、语音合成与识别、联网搜索、知识库检索、长期记忆、智能体与工作流等能力。

[阿里云百炼 CLI 控制台 →]({{ site.bailian_cli_url }})

---

## 使用方式

阿里云百炼 CLI 可在以下任意一种环境中使用：

| 环境 | 说明 |
|------|------|
| **终端直接使用** | 安装 `bailian-cli` 后用 `bl` 命令调用 |
| **主流 AI Agent 框架** | 在 Cursor、Qwen Code、Claude Desktop、Windsurf、Cline、Trae 等 Agent 中作为工具调用 |
| **OpenWork（开源桌面 Agent）** | 我们开源的桌面 Agent，已内置阿里云百炼 CLI，安装即用 |

---

## 安装

```bash
npm install -g bailian-cli
```

> 需要 Node.js >= 22.12

### 验证安装

```bash
bl --version
```

### 也可以使用 OpenWork（开源桌面 Agent）

OpenWork 已内置阿里云百炼 CLI，无需单独安装：[下载 OpenWork →](/openwork/)

---

## 配置

### 获取 API Key

[获取阿里云百炼 API Key →]({{ site.bailian_apikey_url }})

### 登录

```bash
# 推荐：浏览器 OAuth 登录（支持控制台能力）
bl auth login --console

# 或：使用 API Key 登录
bl auth login --api-key sk-xxxxx

# 或：环境变量
export DASHSCOPE_API_KEY=sk-xxxxx
```

### 验证配置

```bash
bl text chat --message "你好"
```

---

## 核心能力

| 能力 | 命令 | 说明 |
|------|------|------|
| 文本对话 | `bl text chat` | Qwen3.7-max，支持 agentic coding / vibe coding |
| 全模态对话 | `bl omni` | 文本 + 图片 + 音频 + 视频多模态 |
| 图像生成 | `bl image generate` | Qwen-Image 2.0，专业文字渲染、写实图、多图合成 |
| 图像编辑 | `bl image edit` | 图生图、风格迁移、多图合成 |
| 视频生成 | `bl video generate` | HappyHorse-1.0 系列，文/图/参考 → 视频 |
| 视频编辑 | `bl video edit` | 自然语言视频编辑（最多 9 张参考图） |
| 语音合成 | `bl speech synthesize` | CosyVoice 流式 TTS，5–20s 样本声音克隆 |
| 语音识别 | `bl speech recognize` | FunAudio-ASR，30 语言含 7 种中文方言 |
| 图片视频理解 | `bl vision` | Qwen-VL 长视频分析、图表/文档解析、多语 OCR |
| 知识库检索 | `bl knowledge retrieve` | 多模态 RAG 检索 |
| 长期记忆 | `bl memory` | 跨会话记忆，支持个性化对话 |
| 应用调用 | `bl app call` | 调用百炼平台已发布的智能体与工作流 |
| MCP 集成 | `bl mcp` | 编排百炼 MCP 服务，列出/检查/调用任意工具 |
| 联网搜索 | `bl search` | 实时互联网检索 |
| 模型推荐 | `bl advisor recommend` | 描述场景获取最优模型建议、模型对比 |
| 用量查询 | `bl usage free` | 查询免费额度使用情况 |

> ℹ️ **`bl mcp` 不做什么**
>
> `bl mcp` 是 **MCP 客户端**——它让你调用百炼平台已经发布的 MCP 服务。
> 它**不会**把 `bl` 本身暴露成 MCP server。如果你想让 Claude Desktop / Cursor 等通过 MCP 协议接入 `bl`，
> 目前推荐做法是直接在 Agent 配置里把 `bl` 当作 shell 命令调用（例如 `claude_desktop_config.json` 中
> `"command": "bl"`）。原生 `bl mcp serve` 模式在 roadmap 中。

> 每个 URL 参数都接受本地路径，自动上传到免费临时存储（48 小时有效期）。

---

## 使用示例

### 对话

```bash
# 文本对话
bl text chat --message "解释一下 RAG"

# 多模态：图 + 文
bl omni --message "描述这张图" --image ./photo.jpg
```

### 图像生成

```bash
bl image generate --prompt "一只穿宇航服的猫" --out-dir ./images/
```

### 视频生成

```bash
# 图生视频
bl video generate --image ./cat.png --prompt "让猫动起来" --download cat.mp4
```

### 模型推荐

```bash
bl advisor recommend --message "我需要一个视觉理解的对话机器人"
```

### 浏览应用 / 查询免费额度

```bash
bl auth login --console
bl app list
bl usage free --model qwen3-max
```

---

## 安装 Skills

阿里云百炼官方提供了精选的 Agent Skills 集合：

```bash
# 安装核心 bailian-cli skill
npx skills add modelstudioai/cli --all -g

# 安装精选扩展 skills
npx skills add modelstudioai/skills
```

查看可用列表 → [精选 Skills](/skills/)

---

## 配置管理

```bash
# 查看当前配置
bl config show

# 设置默认值
bl config set --key region --value us
bl config set --key default_text_model --value qwen-turbo
bl config set --key timeout --value 600

# 自更新到最新版本
bl update
```

> 配置文件位置：`~/.bailian/config.json`

---

## 更多资源

- [CLI 源码 →](https://github.com/modelstudioai/cli)
- [完整上手教程 →](/guide/)
- [精选 Skills →](/skills/)
- [Workshop 手册 →](/workshop/)
- [DashScope API 文档 →](https://help.aliyun.com/zh/model-studio/)

---

> [在 GitHub 上编辑此页 →](https://github.com/modelstudioai/modelstudioai.github.io/edit/main/cli/index.md)
