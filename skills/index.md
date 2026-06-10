---
layout: doc
title: 精选 Skills
permalink: /skills/
---

# 精选 Skills

精选 Skills 是阿里云百炼团队验证过的高质量 Agent Skills 集合，覆盖**图文、视频、文字**与开发协作等多个场景。每个 Skill 都是一个独立可组合的工作流单元，经过实际验证，标记为「可用」后才会收录。

> 📦 仓库：[modelstudioai/skills](https://github.com/modelstudioai/skills) · 详细分类与示例 Prompt：[AWESOME_SKILLS.md](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md)

---

## 使用前提

1. 已[获取阿里云百炼 API Key]({{ site.bailian_apikey_url }})
2. 已安装 [阿里云百炼 CLI](/cli/) 或 [OpenWork（开源桌面 Agent）](/openwork/)
3. Node.js >= 18

---

## 一、官方 First-party Skills

由阿里云百炼团队自行开发与维护，随仓库交付：

| Skill | 用途 |
|-------|------|
| [`bailian-cli`](https://github.com/modelstudioai/cli) | 核心 Skill，封装 `bl` 全部能力（文本/全模态/图像/视频/语音/视觉/RAG/记忆等） |
| [`bailian-docs-llm-wiki`](https://github.com/modelstudioai/skills/tree/main/skills/bailian-docs-llm-wiki) | 阿里云百炼文档知识库：模型规格、价格、API 错误码、智能体/RAG/知识库/插件等一站查询 |
| [`spark-video`](https://github.com/modelstudioai/skills/tree/main/skills/spark-video) | 端到端短片制作：编剧 ↔ 导演（每场景）→ 并行渲染 DAG → 单片 QA → 合片，一句话出片 |

---

## 二、精选 Curated Skills（社区共建）

### 🎨 图文 / 设计

| Skill | 示例 Prompt | 来源 |
|-------|-------------|------|
| [canvas-design](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#canvas-design) | 设计一张以「自由 + 蝴蝶」为主题的视觉海报 | [anthropics/skills](https://github.com/anthropics/skills) |
| [frontend-design](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#frontend-design) | 为小米手机设计一个高质量推广页 | [anthropics/skills](https://github.com/anthropics/skills) |
| [shadcn-ui](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#shadcn-ui) | 用 shadcn-ui 组件库做一个聊天室页面 | [google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills) |
| [ui-ux-pro-max](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#ui-ux-pro-max) | 用 50 种风格中的一种设计个人博客 UI | [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates) |
| [baoyu-xhs-images](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md) | 把这篇内容拆成小红书图文系列（10 风格 × 8 版式） | 社区 |

### 🎬 视频 / 音频

| Skill | 示例 Prompt | 来源 |
|-------|-------------|------|
| [spark-video](https://github.com/modelstudioai/skills/tree/main/skills/spark-video) | 给我做一支产品广告——这是产品图，卖点一句话 | [JohnKeating1997/spark-video](https://github.com/JohnKeating1997/spark-video) |
| [shanyin-screenwriting-master](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#shanyin-screenwriting-master) | 做一个《小红帽》故事的真人风格视频 | [Shanyin-ai/shanyin-screenwriting-master](https://github.com/Shanyin-ai/shanyin-screenwriting-master) |

### 📝 文字 / 写作

| Skill | 示例 Prompt | 来源 |
|-------|-------------|------|
| [marketing-writer](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#marketing-writer) | 给徕芬吹风机写一段营销文案 | [gushuaialan1/marketing-writer](https://github.com/gushuaialan1/marketing-writer) |
| [internal-comms](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#internal-comms) | 写 2026 年 5 月第一周的团队周报 | [anthropics/skills](https://github.com/anthropics/skills) |
| [doc-coauthoring](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#doc-coauthoring) | 写一篇技术设计文档，结构化分三阶段产出 | [anthropics/skills](https://github.com/anthropics/skills) |
| [AI-Vibe-Writing-Skills](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#ai-vibe-writing-skills) | 把这段文案改写得不那么 AI 味 | [donghuixin/AI-Vibe-Writing-Skills](https://github.com/donghuixin/AI-Vibe-Writing-Skills) |
| [social-media-skills](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#social-media-skills) | 规划一份社媒内容策略 | [blacktwist/social-media-skills](https://github.com/blacktwist/social-media-skills) |
| [finance-skills](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#finance-skills) | 写一篇近期基金涨幅的爆款财经文章 | [digoal/blog](https://github.com/digoal/blog/tree/master/skills) |

### 📄 文档 / Office

| Skill | 示例 Prompt | 来源 |
|-------|-------------|------|
| [xlsx / docx / pdf / pptx](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#office-suite-xlsx--docx--pdf--pptx) | 做一份 2025 全年国货美妆销售数据的 PPT | [anthropics/skills](https://github.com/anthropics/skills) |

### 💻 代码开发

| Skill | 示例 Prompt | 来源 |
|-------|-------------|------|
| [mcp-builder](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#mcp-builder) | 帮我做一个让 Claude 能调用天气服务的 MCP Server | [anthropics/skills](https://github.com/anthropics/skills) |
| [goframe-v2](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#goframe-v2) | 用 GoFrame v2 写一个登录 API | [gogf/skills](https://github.com/gogf/skills) |

### 🛠️ Skill 管理 / 协作

| Skill | 示例 Prompt | 来源 |
|-------|-------------|------|
| [skill-creator](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#skill-creator) | 帮我写一个分析"小红书宠物视频为何爆款"的 Claude Code Skill | [anthropics/skills](https://github.com/anthropics/skills) |
| [find-skills](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#find-skills) | 给我找一个做 PPT 的 Skill | [vercel-labs/skills](https://github.com/vercel-labs/skills) |
| [skills-mcp](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#skills-mcp) | 帮我找最新的 AI Skill | [skills-mcp/skills-mcp](https://github.com/skills-mcp/skills-mcp) |

### 🧪 测试 / 质量

| Skill | 示例 Prompt | 来源 |
|-------|-------------|------|
| [e2e-testing](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md#e2e-testing) | 写覆盖注册→登录→浏览→购物车→结算的 e2e 测试 | [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code) |

> 完整列表（含示例 Prompt 与分类）：[AWESOME_SKILLS.md →](https://github.com/modelstudioai/skills/blob/main/AWESOME_SKILLS.md)

---

## 如何安装

### 方式一：让你的 Agent 自动安装（推荐）

把下面这段话粘进你的 AI Agent（Cursor / Qwen Code / Claude Desktop / Windsurf / OpenWork 等）：

```
请帮我安装阿里云百炼的 AI Skills：
1. 检查 Node.js 是否已安装（>=18），未安装则自动安装
2. 执行：npx skills add modelstudioai/skills
3. 安装完成后告诉我「Bailian Skills installed」，并列出已安装的 Skills 与可用功能
```

### 方式二：手动安装

```bash
# 安装核心 bailian-cli skill（强烈推荐先装这个）
npx skills add modelstudioai/cli --all -g

# 安装精选扩展 skills（按提示选择需要的项）
npx skills add modelstudioai/skills
```

---

## 如何运行

Skills 安装后无需手动「加载」与「运行」——你的 AI Agent 会根据对话内容自动激活合适的 Skill。例如：

```
> 帮我做一个产品宣传视频，产品图在 ./product.jpg，卖点是"轻便、续航长"

[Agent 自动调用 spark-video skill，依次执行编剧→导演→渲染→合片]
```

或显式提示 Agent 使用某个 Skill：

```
> 用 canvas-design skill 设计一张「自由蝴蝶」主题海报
```

各类 Skill 预期耗时参考：

| 类型 | 预期耗时 |
|------|----------|
| 文字类 | 5–30 秒 |
| 图文类 | 30 秒 – 2 分钟 |
| 视频类 | 2–10 分钟（取决于片长与片段数） |

---

## 贡献 Skill

如果你开发了实用的 Skill，欢迎共建社区仓库：

- [Skill 仓库 →](https://github.com/modelstudioai/skills)
- [贡献指南 →](https://github.com/modelstudioai/skills/issues/new)
- 需要先在真实场景验证，标记为「可用」后才会被收录

---

## 相关资源

- [完整上手教程 →](/guide/)
- [Workshop 手册 →](/workshop/)
- [阿里云百炼 CLI →](/cli/)
- [OpenWork（开源桌面 Agent）→](/openwork/)

---

> ⚠️ **声明** — Skills 通过 `bl` 调用 DashScope / 阿里云百炼 API，按你的阿里云账号计费。生成内容可能存在偏差，请审核后使用；妥善保管 API Key。

> [在 GitHub 上编辑此页 →](https://github.com/modelstudioai/modelstudioai.github.io/edit/main/skills/index.md)
