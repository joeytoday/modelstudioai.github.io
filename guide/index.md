---
layout: doc
title: 完整上手教程
permalink: /guide/
description: "5 步从零到一：注册阿里云百炼、获取 API Key、安装 CLI、加载 Skill、跑出你的第一个 AI 产物。覆盖 Cursor、Qwen Code、Claude Desktop、OpenWork 等主流 Agent 集成路径。"
keywords: "阿里云百炼上手,百炼 CLI 安装,API Key 获取,bailian-cli 教程,AI Agent 入门,Qwen 调用,Cursor 集成,Claude Desktop,Quick Start"
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

## 五分钟先认识四个词

正式开干前，先用一张图记住四个名词的关系——它们贯穿全教程：

![四个名词的关系图](/guide/assets/bailian-cli-relationship-diagram.jpg)

一句话类比，便于回忆：

| 名词 | 一句话类比 |
|------|------------|
| <img src="/guide/assets/bailian-cli-card-01-bailian.jpg" width="100"> **百炼** | 阿里云的「**模型超市**」——Qwen / DeepSeek / Kimi / GLM / MiniMax / 通义万相都在货架上，按需取用 |
| <img src="/guide/assets/bailian-cli-card-02-apikey.jpg" width="100"> **API Key** | 你的「**身份证 + 充值卡**」——证明你是合法用户，账户里挂着新人免费额度 |
| <img src="/guide/assets/bailian-cli-card-03-cli.jpg" width="100"> **CLI（`bl`）** | 「**万能遥控器**」——一句话或一行命令，让 Agent 调用模型超市里任何一个模型 |
| <img src="/guide/assets/bailian-cli-card-04-mcp.jpg" width="100"> **MCP** | 「**通用插头**」——AI 世界的 USB-C，让任意 Agent 一插即用百炼能力 |

> 👶 **小白专属**：如果你看不懂下方任何一条命令，**完全没关系**——本教程支持纯对话路径，所有命令都可以让 Agent 替你跑。继续往下看 Step 2。

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

> ✋ **不想敲命令？跳过本节直接看 Step 4。**
>
> 如果你**不熟悉终端、不会 npm、看见命令行就头大**——选下面的「方式 C：OpenWork 桌面 Agent」就够了。下载 .dmg/.exe 双击安装，跟微信一样傻瓜。CLI、Skills 在 OpenWork 里全部内置好了，**你只需要在对话框里说人话**：
>
> > 帮我安装阿里云百炼，跑一下你内置的 demo
>
> Agent 会自动替你完成所有命令行操作并把结果贴回来。后续 Step 5 的「让 Agent 调用 Skill」、Step 6 的「跑通你的第一支视频广告」**全部都是纯对话**，不需要打任何字符的命令。

### 我应该选哪条路径？

| 你的现状 | 推荐路径 | 大概体验 |
|---------|----------|---------|
| 完全没装过任何 AI Agent，看见黑色终端就紧张 | 方式 C（OpenWork） | 像装微信一样，下载即用，全程对话 |
| 已经在用 Cursor / Qoder / Claude Desktop | 方式 B | 零额外配置，把命令交给你已有的 Agent |
| 习惯命令行，想要最轻量 | 方式 A | 一行 npm install，全靠肌肉记忆 |

拿不准？**默认选方式 C**。

阿里云百炼 CLI 是为 AI Agent 而生的——任何支持 shell 命令或 MCP 工具的 Agent 都能直接使用它。挑选适合你的方式：

### 方式 A：终端直接安装（最轻量）

```bash
npm install -g bailian-cli
bl --version
```

> ⚙️ **环境前置说明**
> - `bailian-cli` 本体（`bl` 命令）：**Node.js ≥ 22.12**（package.json engines 字段硬要求，低于此版本 `npm install` 会直接报错）
> - `skills` CLI（`npx skills add ...`，第四步用到）：Node.js ≥ 18 即可
>
> 没装 Node 或版本低于 22.12？建议直接装最新 LTS（v22 或更高）一劳永逸，推荐使用 [nvm](https://github.com/nvm-sh/nvm) / [fnm](https://github.com/Schniz/fnm) 管理版本。

### 方式 B：在主流 AI Agent 框架中使用

无需额外配置——只要 Agent 能执行 shell，就能调用 `bl`。

| 框架 | 调用方式 |
|------|----------|
| Cursor | 终端 / Composer 调用 `bl ...` 命令 |
| Qwen Code | 作为结构化工具调用，参考 [showcase](/showcase/) |
| Claude Desktop / Claude Code | 直接 shell 调用即可（在 `claude_desktop_config.json` 里把 `command` 设为 `bl`）。若要让 Agent 调用百炼平台托管的 MCP 服务（如官方天气、日历等），用 `bl mcp list` / `bl mcp call` |
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
1. 检查 Node.js 是否已安装且版本 >= 22.12（bailian-cli 硬要求），未达到则升级到最新 LTS
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

> 💬 **不必打命令——对 Agent 说人话就行**
>
> 下面给的命令是「**最底层操作**」，方便高级用户做精细控制。如果你在 OpenWork / Cursor / Qoder / Claude Desktop 里，**完全可以不打任何命令**，直接对 Agent 说：
>
> > 帮我用 bailian-cli 生成一张图，主题是"穿宇航服的猫，赛博朋克风格"
>
> Agent 会自动选择正确的 `bl image generate` 命令、补齐参数、跑完后把结果路径告诉你。
>
> **判断你是不是在对话流里**：你能否用中文一句话提需求、Agent 直接给结果？是→你已经在对话流里，下面的命令直接当作"原理科普"读就行。

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

## 第六步（可选）：跑通你的第一支视频广告

前面五步都偏「**单个能力点**」。这一步用一条对话指令，让 Agent 自己 clone 仓库、读故事板、调百炼，**端到端跑出一支日系青春汽水广告片**——和我们 5 分钟视频教学里展示的是同一个 demo。

### 你需要做什么？

**只需要一句话。** 在你的 Agent 对话框（OpenWork / Cursor / Qoder / Claude Desktop 任一）里粘贴：

> 帮我从 GitHub clone modelstudioai 的 awesome-happyhorse-prompts 仓库，
> 按 `cases/r2v-1.1.md` 第 3 个 case「Happy Run Citrus」的 prompt 和 `assets/` 里的故事板图，
> 给我跑一支 720P 的视频。完成后把视频路径告诉我。

### 幕后发生了什么？

Agent 会**按顺序自动**：

1. `git clone https://github.com/modelstudioai/awesome-happyhorse-prompts`
2. 读 `cases/r2v-1.1.md` 第 3 个 case 的完整 prompt（9 镜头日剧 CM 分镜）
3. 加载 `assets/` 目录下的 3×3 故事板图（**这就是为什么必须 clone**——R2V 模型必须吃故事板图）
4. 调用 `bl video ref`（HappyHorse 1.1 R2V 模型）
5. 等 3–5 分钟出片

### 想直接在浏览器里试？

不想 clone 也想感受一下？打开 [HappyHorse 1.1 文生视频体验页]({{ site.happyhorse_t2v_url }})，直接在网页上输入 prompt 就能出片。但**只有 clone 仓库**才能拿到 Happy Run Citrus 这一套完整的故事板图，跑出和示例一模一样的成片。

### 跑通了？

- 给 [`modelstudioai/awesome-happyhorse-prompts`](https://github.com/modelstudioai/awesome-happyhorse-prompts) 点个 ⭐ Star
- 把你的成片提交到 [Showcase](/showcase/)
- 改 prompt 换品牌，做属于你自己的产品广告

> 💸 **关于费用**：HappyHorse 1.1 R2V 模型 720P 价格 ¥0.9/秒，30 秒约 ¥27；新用户有 10 秒免费额度，第一次跑可零成本。2026-07-06 前还有 6 折优惠。

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
