---
layout: doc
title: Workshop
permalink: /workshop/
---

# CLI & Skills 动手实验

欢迎参加 Model Studio AI 线下 Workshop！本页是你的全程操作指引——按步骤执行即可完成一个完整 AI 作品。

> **预计用时：90 分钟** | 现场 tokens 管够，放心使用。

---

## Step 1：获取百炼 API Key

点击下方链接，注册/登录阿里云百炼平台并创建 API Key：

👉 [获取 API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

操作步骤：

1. 点击链接，使用阿里云账号登录（支持支付宝/钉钉扫码）
2. 进入「API-KEY 管理」页面
3. 点击「创建新的 API Key」
4. 复制生成的 Key（格式为 `sk-xxxxxxxxxxxxxxxx`），保存好备用

> 没有阿里云账号？注册是免费的，新用户默认有免费调用额度。

---

## Step 2：安装 OpenWork

OpenWork 桌面端已内置百炼 CLI，下载安装即可使用全部能力。

### 下载地址

| 系统 | 下载链接 | 说明 |
|------|----------|------|
| **macOS (Apple Silicon)** | [GitHub Releases](https://github.com/modelstudioai/openwork/releases) | .dmg 文件，双击安装拖入 Applications |
| **macOS (Intel)** | [GitHub Releases](https://github.com/modelstudioai/openwork/releases) | 同上，选 x64 版本 |
| **Windows** | [GitHub Releases](https://github.com/modelstudioai/openwork/releases) | .exe 安装程序，按提示完成 |
| **Linux** | [GitHub Releases](https://github.com/modelstudioai/openwork/releases) | .AppImage 或 .deb，按发行版选择 |

### 安装后确认

打开 OpenWork，你应该看到主界面的对话窗口。左下角显示版本号即为安装成功。

### 备选方案：独立安装百炼 CLI

如果你更习惯纯终端操作，也可以不装 OpenWork，直接安装 CLI：

```bash
npm install -g bailian-cli
```

> 需要 Node.js >= 22.12。安装后终端输入 `bl --version` 确认。

---

## Step 3：配置 API Key

### 方式一：OpenWork 内配置（推荐）

1. 打开 OpenWork
2. 在对话框中输入以下内容，让 Agent 帮你配置：

```
请帮我配置百炼 API Key：sk-你的Key粘贴在这里
```

Agent 会自动执行 `bl auth login --api-key sk-xxxxx` 并确认成功。

### 方式二：终端命令行配置

```bash
# 登录认证（推荐，Key 会持久化到 ~/.bailian/config.json）
bl auth login --api-key sk-xxxxx

# 或者设置环境变量（临时生效）
export DASHSCOPE_API_KEY=sk-xxxxx
```

### 配置成功的预期提示

```
✓ API Key 已保存
✓ 区域: cn-beijing
✓ 账号验证通过
```

如果看到 `✓` 绿色提示，说明配置完成。

### 验证配置

```bash
# 发一条消息测试
bl text chat --message "你好"
```

如果收到千问的回复，恭喜你，环境就绪！

---

## Step 4：选择一个精选 Skill

以下 Skills 已验证可用，覆盖图文、视频、文字三类场景。选择你感兴趣的一个：

### 🎨 图文类

| Skill | 一句话说明 | 加载命令 |
|-------|-----------|---------|
| **canvas-design** | 用 AI 生成视觉海报，支持自定义主题和风格 | `npx skills add anthropics/skills` 选 canvas-design |
| **frontend-design** | 生成高质量产品推广页面（HTML） | `npx skills add anthropics/skills` 选 frontend-design |
| **baoyu-xhs-images** | 生成小红书风格信息图，10 种视觉风格 | `npx skills add baoyu/xhs-images` |

### 🎬 视频类

| Skill | 一句话说明 | 加载命令 |
|-------|-----------|---------|
| **spark-video** | 一句话生成短片：剧本 → 分镜 → 渲染 → 合成 | `npx skills add modelstudioai/skills` 选 spark-video |
| **shanyin-screenwriting-master** | 真人实拍风格影视短片生成 | `npx skills add Shanyin-ai/shanyin-screenwriting-master` |

### 📝 文字类

| Skill | 一句话说明 | 加载命令 |
|-------|-----------|---------|
| **marketing-writer** | 生成营销文案，支持多平台多风格 | `npx skills add gushuaialan1/marketing-writer` |
| **doc-coauthoring** | 结构化技术文档协作撰写 | `npx skills add anthropics/skills` 选 doc-coauthoring |
| **internal-comms** | 周报、日报、团队通讯类文档 | `npx skills add anthropics/skills` 选 internal-comms |

> 不确定选哪个？推荐 **spark-video**（视频）或 **canvas-design**（海报），效果最直观。

---

## Step 5：加载并运行 Skill

### 在 OpenWork 中运行（推荐）

直接在对话框中用自然语言告诉 Agent 你想做什么。Agent 会自动调用对应 Skill。

**示例提示词：**

```
用 spark-video 帮我生成一段 30 秒的短视频。
主题：一只猫在太空探险。
风格：皮克斯动画风格，温馨治愈。
```

```
用 canvas-design 帮我设计一张海报。
主题：夏日咖啡节，清凉蓝绿配色，要有手绘感。
```

```
用 marketing-writer 帮我写一段小红书推广文案。
产品：智能台灯，卖点是护眼+无线充电+氛围灯三合一。
```

### 在终端中运行

如果你使用独立 CLI + Qwen Code / Claude Code：

```bash
# 安装 Skill（首次需要）
npx skills add modelstudioai/skills --all -g

# 在 Agent 会话中说出你的需求，Agent 自动读取 SKILL.md 并执行
# 以 spark-video 为例：
# "帮我用 spark-video 生成一段产品广告视频，产品图在 ./product.png"
```

### 常用 bl 命令参考

```bash
# 文字对话
bl text chat --message "帮我写一首关于夏天的诗"

# 图片生成
bl image generate --prompt "赛博朋克风格的猫咖" --out-dir ./output/

# 视频生成（图生视频）
bl video generate --image ./input.png --prompt "让画面动起来" --download output.mp4

# 语音合成
bl speech synthesize --text "你好，欢迎来到 Workshop" --output hello.mp3
```

---

## Step 6：查看结果

### 图文类产出

- **canvas-design** → 在当前目录生成 HTML 文件，浏览器打开即可看到完整海报
- **frontend-design** → 生成完整的产品页 HTML，包含响应式布局和动效
- **baoyu-xhs-images** → 生成 1-10 张卡通信息图 PNG，可直接发小红书

### 视频类产出

- **spark-video** → 在 `projects/<项目名>/<集数>/final/` 目录下生成 MP4 文件
- **shanyin-screenwriting-master** → 同上，输出最终合成视频

### 文字类产出

- **marketing-writer** → 直接在对话中输出文案，可要求导出 Markdown
- **doc-coauthoring** → 分阶段输出结构化文档，最终生成完整 Markdown 或 DOCX
- **internal-comms** → 输出格式化的周报/通讯内容

> 所有通过 `bl` 生成的文件都会保存在你指定的 `--out-dir` 或当前工作目录下。

恭喜！你已经完成了 **获取 Key → 安装 → 配置 → 选 Skill → 运行 → 产出** 的完整链路。

---

## 进阶探索（时间允许的话）

已经跑通了？可以试试这些：

- 换一个不同类型的 Skill 再跑一遍，感受多模态能力组合
- 调整提示词的细节（风格、时长、配色），观察 AI 如何响应
- 组合多个 `bl` 命令形成流水线，比如「文生图 → 图生视频 → 配音」
- 尝试 `bl advisor recommend --message "你的场景描述"` 让 AI 推荐最适合的模型

---

## 遇到问题？

| 问题 | 解决方式 |
|------|----------|
| API Key 配置后提示「无效」 | 检查 Key 是否完整复制（以 `sk-` 开头），没有多余空格或换行。回到 [API Key 页面](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key) 重新创建一个试试 |
| `bl: command not found` | 确认已安装：`npm install -g bailian-cli`，然后重启终端。或直接用 OpenWork（已内置） |
| Skill 加载失败 / 网络超时 | 现场 Wi-Fi 可能拥挤，切换手机热点重试。或让旁边的同学帮你 AirDrop 安装包 |
| 视频生成很慢（等了 5 分钟+） | 正常！视频渲染需要排队，通常 3-8 分钟完成。可以先切到文字/图片类 Skill 玩 |
| `node: command not found` | 需要安装 Node.js >= 22.12。macOS: `brew install node`，Windows: 从 [nodejs.org](https://nodejs.org) 下载安装 |
| 生成的图片/视频质量不满意 | 优化提示词：加入更具体的描述（风格、色调、构图）。试试 `bl advisor recommend` 换个模型 |

> 现场有助教巡场，遇到任何卡住的情况直接举手！

---

## Workshop 之后

- 📖 [完整文档](/guide/) — 随时回来查阅更多用法
- 🎯 [精选 Skills](/skills/) — 发现更多场景和能力
- ✨ [分享你的作品](/showcase/) — 提交到 Showcase，让更多人看到你的创作
- 💬 加入开发者社群 — 钉钉群 Dev@ModelStudioAI（群号 182405011072）持续交流
- 🏆 路演获奖？别忘了把作品 PR 到 [modelstudioai/skills](https://github.com/modelstudioai/skills)，成为社区共建者！

---

> 本页面会在每场 Workshop 后迭代更新。发现问题或有改进建议？[帮我们改进 →](https://github.com/ModelStudioAI/modelstudioai.github.io/edit/main/workshop/index.md)
