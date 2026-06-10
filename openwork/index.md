---
layout: doc
title: OpenWork
permalink: /openwork/
description: "OpenWork 是阿里云百炼团队开源的桌面 AI Agent——内置 CLI、Skills 体系与对话界面，下载安装即用，零配置体验完整的 Agent 工作流。macOS / Windows / Linux 全平台支持。"
keywords: "OpenWork,开源桌面 Agent,阿里云百炼桌面,AI 桌面应用,Agent 工作空间,CLI 集成,Agent Skills,本地 AI 助手,Desktop Agent"
---

# OpenWork

**OpenWork（开源桌面 Agent）** 是阿里云百炼团队开源的桌面 AI Agent 工作空间——内置阿里云百炼 CLI、Skills 体系与对话界面，下载即用，支持 Skills 自动激活、MCP 工具编排与多模态输入。

> 🛡️ MIT 协议开源 · macOS / Windows / Linux 全平台

[GitHub 仓库 →](https://github.com/modelstudioai/openwork) · [前往 Releases 下载 →](https://github.com/modelstudioai/openwork/releases)

---

## 为什么选择 OpenWork

| 痛点 | OpenWork 的解法 |
|------|----------------|
| 不想配命令行环境 | 内置阿里云百炼 CLI（`bl`），打开即用 |
| Skills 安装繁琐 | UI 内置 Skills 市场，一键安装/启用 |
| 多个 Agent 框架来回切 | 一个桌面环境覆盖对话、工作流、多模态 |
| 需要管理凭证与配额 | 内置 API Key 配置面板与额度查询 |

> OpenWork 是阿里云百炼 CLI 的**官方开源运行环境**之一——若你已熟悉 Cursor / Qwen Code / Claude Desktop / Windsurf / Cline，也可以在那些 Agent 中直接使用 `bl` 命令；OpenWork 提供的是一个开箱即用的备选方案。

---

## 下载安装

[前往 GitHub Releases →](https://github.com/modelstudioai/openwork/releases)

### macOS

1. 下载最新 `.dmg` 文件
2. 打开 `.dmg`，将 OpenWork 拖入「应用程序」
3. 首次打开如遇安全提示 → 系统设置 → 隐私与安全性 → 仍要打开

### Windows

1. 下载最新 `.exe` 安装包
2. 运行安装程序，按提示完成
3. 从开始菜单启动 OpenWork

### Linux

1. 下载 `.AppImage` 或 `.deb`
2. AppImage 方式：

```bash
chmod +x OpenWork-*.AppImage
./OpenWork-*.AppImage
```

3. deb 方式：

```bash
sudo dpkg -i OpenWork-*.deb
```

---

## 配置 API Key

### 方式一：界面配置（推荐）

1. 打开 OpenWork → 设置（Settings）
2. 找到「API Key」配置项
3. 粘贴 API Key → 保存

还没有 API Key？[获取阿里云百炼 API Key →]({{ site.bailian_apikey_url }})

### 方式二：命令行配置

OpenWork 内置终端中执行：

```bash
# 浏览器 OAuth 登录（推荐，可使用控制台能力）
bl auth login --console

# 或：API Key 登录
bl auth login --api-key sk-xxxxx
```

---

## 内置阿里云百炼 CLI

OpenWork 已内置 `bl` 命令，无需额外安装。在内置终端中验证：

```bash
bl --version
bl text chat --message "你好"
```

完整 CLI 命令参考 → [阿里云百炼 CLI 文档](/cli/)

---

## 加载并使用 Skills

OpenWork 内置 Skills 体系，支持从社区仓库一键安装：

### 安装核心 Skills

```bash
# 核心 bailian-cli skill
npx skills add modelstudioai/cli --all -g

# 精选扩展 skills
npx skills add modelstudioai/skills
```

### 让 Agent 自动调用 Skill

无需手动「加载 → 运行」。直接对 OpenWork 说：

```
> 帮我设计一张「自由 + 蝴蝶」主题的海报
[OpenWork 自动激活 canvas-design skill]

> 用我的产品图做一支 30 秒广告视频
[OpenWork 自动激活 spark-video skill]
```

查看可用 Skills → [精选 Skills](/skills/)

---

## 核心特性

- **多模态对话**：文本、图片、音频、视频统一输入
- **Skills 自动激活**：根据对话内容自动选用合适 Skill
- **MCP 工具编排**：通过 `bl mcp` 调用任意 MCP Server
- **本地工作目录**：生成内容直接落到本地，文件管理更自由
- **跨会话记忆**：通过 `bl memory` 实现长期记忆
- **应用调用**：连接阿里云百炼控制台已发布的智能体与工作流

---

## 与其他 AI Agent 框架的关系

OpenWork 是阿里云百炼 CLI 的**一种**运行环境，并不是唯一选择：

| 你的现有环境 | 推荐做法 |
|--------------|----------|
| 已使用 Cursor / Windsurf | 直接在终端 / Composer 调用 `bl` 命令即可 |
| 已使用 Qwen Code / Claude Code | 把 `bl` 当作结构化工具调用，无需额外配置 |
| 还没有 Agent 桌面环境 | 直接装 OpenWork，开箱即用 |
| 想做开源二次开发 | Fork [openwork](https://github.com/modelstudioai/openwork) 即可 |

---

## 更新

```bash
# CLI 自更新
bl update
```

OpenWork 桌面客户端建议定期访问 Releases 检查新版本：

[查看最新版本 →](https://github.com/modelstudioai/openwork/releases)

---

## 更多资源

- [OpenWork 源码 →](https://github.com/modelstudioai/openwork)
- [完整上手教程 →](/guide/)
- [阿里云百炼 CLI 文档 →](/cli/)
- [精选 Skills →](/skills/)
- [Workshop 手册 →](/workshop/)

---

> [在 GitHub 上编辑此页 →](https://github.com/modelstudioai/modelstudioai.github.io/edit/main/openwork/index.md)
