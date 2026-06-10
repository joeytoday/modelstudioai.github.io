---
layout: doc
title: 完整上手教程
permalink: /guide/
---

# 完整上手教程

本教程带你走通 **阿里云百炼 → CLI → Skills → AI Agent** 的完整链路。

> ⏱️ 预计用时：15–25 分钟
> 🚀 在 Workshop 现场？请直接查看 [Workshop 手册 →](/workshop/)

---

## 整体架构

```
阿里云百炼平台（Aliyun Model Studio / DashScope）
        ↑ 提供 AI 模型 API（文本/图像/视频/语音/向量等）
        │
阿里云百炼 CLI（命令 bl）
        ↑ 命令行工具，每条命令即 AI Agent 的结构化工具调用
        │
你的 AI Agent 环境
   • 终端：直接 bl 调用
   • Cursor / Qwen Code / Claude Desktop / Windsurf / Cline / Trae：作为工具
   • OpenWork（开源桌面 Agent）：开箱即用
        ↑ 加载
        │
Skills（可复用的 AI 能力模块）
   • 官方 first-party：bailian-cli、bailian-docs-llm-wiki、spark-video
   • 精选社区：canvas-design、frontend-design、marketing-writer 等
```

各组件职责：

- **阿里云百炼**：模型 API 服务平台（DashScope）
- **阿里云百炼 CLI（`bl`）**：把模型能力封装成结构化命令
- **AI Agent 环境**：调用 `bl` 的载体——可以是任意支持 shell 或 MCP 的 Agent
- **OpenWork**：开源桌面 Agent，已内置 CLI 与 Skills 体系
- **Skills**：把多步工作流打包成可复用的能力模块

---

## 第一步：注册阿里云百炼并获取 API Key

### 1.1 注册账号

前往阿里云百炼平台，使用阿里云账号登录（无账号需先注册）。

### 1.2 创建 API Key

[获取 API Key →]({{ site.bailian_apikey_url }})

1. 点击「创建 API Key」
2. 给 Key 取个名称（如 `my-cli-key`）
3. 复制并妥善保存（仅创建时可见完整值）

### 1.3 关于免费额度

阿里云百炼为新用户提供免费 token 额度，足够本教程与日常探索。安装 CLI 后可用 `bl usage free` 实时查询余量。

[阿里云百炼 CLI 控制台 →]({{ site.bailian_cli_url }})

---

## 第二步：选择你的运行环境

阿里云百炼 CLI 是为 AI Agent 而生的——任何支持 shell 命令或 MCP 工具的 Agent 都能直接使用它。挑选适合你的方式：

### 方式 A：终端直接安装（最轻量）

```bash
npm install -g bailian-cli
bl --version
```

> 需要 Node.js >= 22.12

### 方式 B：在主流 AI Agent 框架中使用

无需额外配置——只要 Agent 能执行 shell，就能调用 `bl`。

| 框架 | 调用方式 |
|------|----------|
| Cursor | 终端 / Composer 调用 `bl ...` 命令 |
| Qwen Code | 作为结构化工具调用，参考 [showcase](/showcase/) |
| Claude Desktop / Claude Code | 直接 shell 调用，或通过 `bl mcp` 暴露为 MCP 工具 |
| Windsurf / Cline / Trae | 同上，支持任意能跑 shell 的 Agent |

### 方式 C：使用 OpenWork（开源桌面 Agent）

[OpenWork](/openwork/) 是阿里云百炼团队开源的桌面 Agent，已内置 CLI、Skills 体系与对话界面，下载安装即用：

[前往 GitHub Releases →](https://github.com/modelstudioai/openwork/releases)

- macOS：下载 `.dmg`，拖入「应用程序」
- Windows：下载 `.exe`，按提示安装
- Linux：下载 `.AppImage` 或 `.deb`

---

## 第三步：登录与验证

### 推荐：浏览器 OAuth 登录

```bash
bl auth login --console
```

会自动弹浏览器完成授权，登录后可使用控制台相关能力（`bl app list` 等）。

### 或：使用 API Key 登录

```bash
bl auth login --api-key sk-xxxxx
```

### 或：环境变量

```bash
export DASHSCOPE_API_KEY=sk-xxxxx
```

### 验证

```bash
bl text chat --message "你好，介绍一下你自己"
```

正常回复说明已连接成功。

---

## 第四步：安装 Skills

Skills 是阿里云百炼团队验证过的 AI 能力模块，让 Agent 能完成更复杂的工作流。

### 一键自动安装（推荐）

把这段话粘进你的 Agent：

```
请帮我安装阿里云百炼的 AI Skills：
1. 检查 Node.js 是否已安装（>= 18），未安装则自动安装
2. 执行：npx skills add modelstudioai/skills
3. 安装完成后告诉我"Bailian Skills installed"，并列出已安装的 Skills 与可用功能
```

### 手动安装

```bash
# 核心 bailian-cli skill
npx skills add modelstudioai/cli --all -g

# 精选扩展 skills
npx skills add modelstudioai/skills
```

完整列表 → [精选 Skills](/skills/)

---

## 第五步：试一试

现在你已经具备完整的 CLI + Skills 环境。挑一个场景试试：

### 文本对话

```bash
bl text chat --message "解释一下 RAG 是什么"
```

### 多模态理解

```bash
bl omni --message "描述这张图" --image ./photo.jpg
```

### 图像生成

```bash
bl image generate --prompt "一只穿宇航服的猫，赛博朋克风格" --out-dir ./images/
```

### 视频生成（图生视频）

```bash
bl video generate --image ./cat.png --prompt "让猫动起来" --download cat.mp4
```

### 让 Agent 调用 Skill

直接对你的 Agent 说：

```
> 帮我设计一张以「自由 + 蝴蝶」为主题的视觉海报
   [Agent 自动激活 canvas-design skill 完成创作]

> 给我做一支 30 秒的产品广告视频，产品图：./product.jpg，卖点是"轻便、续航长"
   [Agent 自动激活 spark-video skill 完成出片]
```

### 查询免费额度

```bash
bl usage free --model qwen3-max
```

### 模型选型建议

```bash
bl advisor recommend --message "我需要做一个能看图回答的对话机器人"
```

---

## 各类 Skill 预期耗时

| 类型 | 预期耗时 | 输出位置 |
|------|----------|----------|
| 文字类 | 5–30 秒 | 终端直显 |
| 图文类 | 30 秒 – 2 分钟 | 本地文件，终端打印路径 |
| 视频类 | 2–10 分钟 | 本地文件，终端打印路径 |

---

## 进阶

### 探索更多

- [精选 Skills 列表 →](/skills/)
- [阿里云百炼 CLI 完整文档 →](/cli/)
- [使用案例 Showcase →](/showcase/)
- [OpenWork（开源桌面 Agent）→](/openwork/)

### 常见问题

- [FAQ 常见问题 →](/faq/)
- [DashScope API 错误码 →](https://help.aliyun.com/zh/model-studio/error-code)

### 参与社区

- 分享你的使用案例 → [Showcase →](/showcase/)
- 贡献你的 Skill → [Skills 贡献指南](https://github.com/modelstudioai/skills/issues/new)
- 提 Issue / PR → [GitHub Org](https://github.com/modelstudioai)

---

> 本教程持续迭代中。[在 GitHub 上编辑此页 →](https://github.com/modelstudioai/modelstudioai.github.io/edit/main/guide/index.md)
