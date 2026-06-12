---
layout: doc
title: Workshop
permalink: /workshop/
description: "阿里云百炼 · 自然语言交互动手实验——用一句句人话指挥 AI 助手，完成从安装 CLI 到跑通 Maidan-Studio 全流程。约 90 分钟。"
keywords: "百炼Workshop,自然语言交互,AI Agent,Maidan-Studio,百炼CLI,动手实验,AI工作流"
---

# 阿里云百炼 · 自然语言交互动手实验

这是一份阿里云百炼的动手实验指引。我们换一种玩法：**不再手敲命令，而是用一句句"人话"指挥你的 AI 助手完成全程搭建**。你只要把想做的事说清楚，AI 助手会在背后自动调用阿里云百炼 CLI（`bl`）这套工具帮你执行。

> **预计用时**：约 90 分钟。

---

## 你需要先准备什么

本实验假设你手边有一个**通用 AI Agent**（任意支持工具调用的 AI 助手皆可），并且它已经能够调用阿里云百炼 CLI 作为工具——可以是终端访问能力，也可以是通过 MCP 集成的百炼工具集。

后面每一步，你看到的都是「**👉 对你的 AI 助手说**」加上一段自然语言。你照着说即可，剩下的安装、配置、执行、排错都交给 AI 助手。如果某一步它需要你确认（比如安装软件、写入文件），按提示确认就好。

> 💡 从"敲命令"到"说人话"：原来要记 `bl text chat --message "..."`，现在只要说"帮我测试一下对话，问它你好"。命令是 AI 助手的事，意图才是你的事。

---

## 演示项目：Maidan-Studio

**节点式 AI 自媒体工作流编辑器 —— 自媒体内容生产的 ComfyUI。**

把「选题 → 文案 → 平台分发 → 封面 → 多页内容图」这条自媒体内容生产链路，变成可拖拽、可编排、可保存为模板的可视化工作流。

| 项目 | 说明 |
| --- | --- |
| 技术栈 | Next.js 15 + React Flow + Supabase + 阿里云百炼 CLI（bl） |

**两条内置生产线：**

| 模板 | 流水线 |
| --- | --- |
| 小红书日更-轻量版 | 关键词 → 选题搜索 → 多维评分 → 选 1 → 脚本生成 → 三平台改写 + 封面 |
| Omi 小红书图文-精装版 | 素材 → 笔记导演 → 资产看板 → 封面 + 多页内容图 |

---

## Step 1：获取阿里云百炼 API Key

这一步是在网页上完成的，需要你亲自操作（涉及账号登录，AI 助手不会替你登录或保管密钥）。

点击下方链接，注册/登录阿里云百炼平台并创建 API Key：

👉 **[获取 API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)**

操作步骤：

1. 点击链接，使用阿里云账号登录（支持支付宝/钉钉扫码）
2. 进入「API-KEY 管理」页面
3. 点击「创建新的 API Key」
4. 复制生成的 Key（格式为 `sk-xxxxxxxxxxxxxxxx`），保存好备用

> 没有阿里云账号？注册是免费的，新用户默认有免费调用额度。

---

## Step 2：安装并配置阿里云百炼 CLI

让 AI 助手帮你把工具装好、把钥匙配上。

**👉 对你的 AI 助手说：**

> "帮我全局安装阿里云百炼 CLI（bailian-cli），装完确认一下版本。我的 Node.js 版本你也帮我检查一下，要求 ≥ 22.12。"

AI 助手会在背后完成安装并核对版本（相当于执行 `npm install -g bailian-cli` 和 `bl --version`）。如果 Node.js 版本不够，它会提醒你升级。

**配置 API Key：**

**👉 对你的 AI 助手说：**

> "用这个 API Key 给百炼 CLI 登录配置好：`sk-xxxxx`。"

AI 助手会把密钥配置妥当（相当于 `bl auth login --api-key sk-xxxxx` 或设置 `DASHSCOPE_API_KEY` 环境变量）。

> ⚠️ API Key 是敏感凭证。建议只在你信任的本地环境里交给 AI 助手配置，不要发到公开渠道。

**快速测试一下：**

**👉 对你的 AI 助手说：**

> "用百炼帮我测试一下对话，让它做个自我介绍。"
>
> "再用百炼生成一张图：一只穿宇航服的猫，存到 images 文件夹。"

如果对话有回复、图片能生成，说明工具已经通了。

> 阿里云百炼 CLI 为 AI Agent 而生，每条命令即一次工具调用。所以你完全可以用自然语言驱动它——无论是在终端，还是在 Cursor、Qwen Code、Claude Desktop、Windsurf、Cline 等主流 AI Agent 框架里把它当工具集成。

---

## Step 3：克隆演示项目

**👉 对你的 AI 助手说：**

> "帮我把这个项目克隆下来并安装依赖：https://github.com/CzzzzzzJ/bailian-cli.git ，用 pnpm 安装。"

AI 助手会完成克隆、进入目录、安装依赖（相当于 `git clone` + `cd` + `pnpm install`）。

> **前置依赖**：Node.js ≥ 22.12、pnpm ≥ 9。如果 pnpm 没装或版本太低，可以顺带让 AI 助手："帮我把 pnpm 升级到最新版。"

---

## Step 4：配置环境

**👉 对你的 AI 助手说：**

> "帮我基于 .env.example 创建一个 .env.local，把下面这些值填进去：
> - 百炼的 DASHSCOPE_API_KEY 用我刚才那个 key
> - Supabase 的 URL 和 anon key 我等下给你（用于登录 + 模板持久化）"

需要填入的环境变量：

```
# 阿里云百炼
DASHSCOPE_API_KEY=sk-your-key

# Supabase（用于登录 + 模板持久化）
NEXT_PUBLIC_SUPABASE_URL=https://<project>.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

**数据库迁移：**

数据库迁移需要在 Supabase Dashboard → SQL Editor 里手动执行（这部分在网页控制台完成）。依次运行项目里的两个 SQL 文件：

- `supabase/schema.sql` —— 8 张表 + 触发器
- `supabase/policies.sql` —— RLS 策略

> 不确定文件内容时可以问 AI 助手："帮我打开 supabase/schema.sql，把要执行的 SQL 贴给我，我去 Supabase 控制台跑。"

---

## Step 5：启动项目

**👉 对你的 AI 助手说：**

> "帮我把这个 web 应用跑起来，用 3030 端口、开启 turbopack。起好后告诉我访问地址。"

AI 助手会启动开发服务器（相当于 `pnpm --filter @maidan/web exec next dev --turbopack -p 3030`）。

启动后：打开 **http://localhost:3030** → 注册账号 → 选择模板 → 修改 PromptTemplate 里的关键词 → 点击运行。

---

## Step 6：动手体验工作流

### 核心玩法

每个节点 = 一个阿里云百炼能力的封装；连线 = 数据从上游产物喂给下游。

下面这张表，左边是画布上的节点，中间是它在背后调用的百炼能力（以及你用自然语言描述同一件事时大概会怎么说）：

| 节点 | 背后调用的能力 | 用自然语言怎么描述 |
| --- | --- | --- |
| TopicSearch | 文本对话（qwen3.7-max） | "帮我做选题搜索，按结构化 JSON 输出候选选题" |
| ScriptGen | 文本对话（qwen3.7-max / qwq-plus） | "根据选定的题目生成脚本；要深度思考就切到带思考链的模型" |
| CoverGen | 图像生成（qwen-image-2.0） | "根据脚本生成一张封面图" |
| AssetGen | 图像编辑（图生图） | "用这张图做图生图，套上 IP 形象和风格" |
| XHSContentGen | 图像编辑（并行） | "并行生成多页小红书内容图" |

> 在画布上，你通常是点节点跑流程。但理解这层对应关系后，你也可以脱离画布、直接对 AI 助手用自然语言要同样的产物。

### 操作要点

- **拖图入画布**：直接把图片拖进画布 → 自动上传 → 创建 ImageInput 节点 → 连线到 AssetGen 作为 IP 形象。
- **Skill 模板挂载**：在节点抽屉里挂载 Skill markdown，运行时会自动拼进 system prompt。
- **人工审核节点**：流程跑到「人工审核」节点会暂停，等你确认后再继续。

### 推荐体验路径

1. 选「小红书日更-轻量版」模板。
2. 修改 PromptTemplate 中的关键词（比如换成「用 AI 做自媒体」）。
3. 点击运行，观察节点逐个变绿。
4. 查看产出：选题评分、脚本文案、三平台改写、封面图片。
5. 尝试挂载不同的 Skill，对比输出差异。

> 想更"对话化"地玩？可以直接对 AI 助手说："这次帮我围绕'用 AI 做自媒体'这个关键词，先搜 5 个选题并打分，选最好的一个生成脚本，再改写成抖音、小红书、公众号三个版本，最后配一张封面。"——这正是「小红书日更-轻量版」流水线的自然语言版本。

---

## 阿里云百炼能力一览（自然语言版）

除了本演示项目用到的能力，阿里云百炼 CLI 还覆盖下面这些。你不必记命令，记住"能让 AI 助手帮你做什么"就够了：

| 能力 | 对 AI 助手可以这么说 | 说明 |
| --- | --- | --- |
| 文本对话 | "用百炼和我对话/帮我写一段" | Qwen3.7-max，支持 agentic coding |
| 全模态对话 | "把这段文字+图片+音视频一起理解一下" | 文本 + 图片 + 音频 + 视频多模态 |
| 图像生成 | "帮我生成一张图，要求是……" | Qwen-Image 2.0，专业文字渲染 |
| 图像编辑 | "把这张图做风格迁移/多图合成/图生图" | 图生图、风格迁移、多图合成 |
| 视频生成 | "用这段文字（或这张图）生成一段视频" | HappyHorse-1.0，文/图/参考 → 视频 |
| 语音合成 | "把这段文字读出来/克隆这个声音" | CosyVoice 流式 TTS + 声音克隆 |
| 语音识别 | "把这段录音转成文字" | FunAudio-ASR，30 语言覆盖 |
| 图片理解 | "看看这张图/这段长视频/这份文档讲了什么" | Qwen-VL，长视频分析、文档解析 |
| 知识库 | "在我的知识库里检索一下……" | 多模态 RAG 检索 |
| 联网搜索 | "联网帮我查一下最新的……" | 实时互联网检索 |
| MCP 集成 | "帮我编排/调用这个百炼 MCP 服务" | 编排百炼 MCP 服务 |
| 模型推荐 | "我的场景是……，推荐个最合适的模型" | 描述场景获取最优模型建议 |

> 更多能力参考 → [阿里云百炼 CLI 控制台](https://bailian.console.aliyun.com/cli?source_channel=cli_github&)。

---

## 常见问题

| 问题 | 解决方案 |
| --- | --- |
| AI 助手说找不到 `bl` 命令 | 让它重新安装：`npm install -g bailian-cli`，并确认 Node.js ≥ 22.12 |
| API Key 无效 | 确认 Key 以 `sk-` 开头，去百炼控制台检查是否已激活 |
| 图片生成超时 | 图片生成通常需要 10–30s，耐心等待；持续超时就让 AI 助手帮你检查网络 |
| `pnpm install` 失败 | 让 AI 助手确认 pnpm ≥ 9，必要时"帮我把 pnpm 升级到最新版" |
| Supabase 连接失败 | 确认 .env.local 里的 URL 和 Key 正确、Supabase 项目已运行 |
| 节点执行报错 | 节点状态变 error 后，点开节点看详情抽屉里的错误信息；也可以把报错贴给 AI 助手让它帮你诊断 |

---

## 提交你的作品

跑通 Workshop 之后，把你的实践提交到社区，让更多人看到 —— 整个过程只要 3 步：

1. 点击提交入口 👉 **[新建 Issue](https://github.com/modelstudioai/modelstudioai.github.io/issues/new?template=showcase.md&title=%E3%80%90%E6%A1%88%E4%BE%8B%E3%80%91)**（已预填模板）。
2. 按模板填四个板块：

   | 板块 | 写什么 |
   | --- | --- |
   | 我做了什么 | 简述你用了哪个 Skill，完成了什么任务 |
   | 使用的工具 | 例如：OpenWork + 阿里云百炼 CLI + canvas-design |
   | 效果展示 | 贴一张截图，或描述产出结果（截图可直接粘贴到编辑框） |
   | 踩坑记录（可选） | 遇到了什么问题？怎么解决的？ |

3. 点击「Submit new issue」提交。

我们会把优秀的案例收录到 [Showcase 页面](/showcase/)。

> 💡 小贴士：截图直接 Ctrl+V 粘贴即可；几句话 + 一张图就够；跑了多个 Skill 可以分别提交多个 issue。

---

## 社区与资源

- 阿里云百炼 CLI GitHub：[github.com/modelstudioai/cli](https://github.com/modelstudioai/cli)
- Agent Skills 精选：[github.com/modelstudioai/skills](https://github.com/modelstudioai/skills)
- OpenWork（开源桌面 Agent）：[github.com/modelstudioai/openwork](https://github.com/modelstudioai/openwork)
- [阿里云百炼 CLI 控制台](https://bailian.console.aliyun.com/cli?source_channel=cli_github&) ｜ [获取 API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)
