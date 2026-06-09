---
layout: doc
title: Workshop
permalink: /workshop/
---

# CLI & Skills 动手实验

欢迎参加 Model Studio AI 线下 Workshop。本页是你的全程指引——按步骤操作即可。

---

## Step 1：获取百炼 API Key

点击下方链接，注册/登录百炼平台并创建 API Key：

👉 [获取 API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

拿到 Key 后复制保存，下一步要用。

---

## Step 2：安装 OpenWork

OpenWork 桌面端已内置百炼 CLI，下载安装即可：

👉 [下载 OpenWork](https://github.com/ModelStudioAI/openwork)

<!-- TODO: 补充各系统的具体安装说明或直接链接到 release 页面 -->

> 已安装过 OpenWork？请确认更新到最新版本。

---

## Step 3：配置 API Key

打开 OpenWork，配置你刚才获取的 API Key：

<!-- TODO: 从 hands-on 手册迁移具体配置步骤 -->

```bash
# 配置命令示例
bailian config set api_key YOUR_API_KEY
```

配置成功后你应该看到：

<!-- TODO: 补充成功提示截图或文字 -->

---

## Step 4：选择一个精选 Skill

以下 Skills 已验证可用，选择你感兴趣的一个：

### 图文类

<!-- TODO: 填入实际 Skill -->

| Skill | 一句话说明 | 加载命令 |
|-------|-----------|---------|
| *待补充* | — | `bailian skill load xxx` |

### 视频类

| Skill | 一句话说明 | 加载命令 |
|-------|-----------|---------|
| *待补充* | — | `bailian skill load xxx` |

### 文字类

| Skill | 一句话说明 | 加载命令 |
|-------|-----------|---------|
| *待补充* | — | `bailian skill load xxx` |

---

## Step 5：加载并运行

```bash
# 加载你选的 Skill
bailian skill load <skill-name>

# 运行
bailian skill run <skill-name>
```

<!-- TODO: 从 hands-on 手册迁移具体操作说明和预期产出 -->

运行完成后，你应该看到 AI 生成的产出。

---

## Step 6：查看结果

<!-- TODO: 补充各类 Skill 的产出示例和截图 -->

恭喜！你已经跑通了 **OpenWork → 百炼 CLI → Skill** 的完整链路。

---

## 进阶探索（可选）

已经跑通了？试试这些：

- 换一个不同类型的 Skill 再跑一遍
- 调整 Skill 的参数看看产出有什么变化
- 浏览 [Skills 完整列表](https://github.com/ModelStudioAI/skills) 找找有没有适合你工作场景的

---

## 遇到问题？

| 问题 | 解决方式 |
|------|----------|
| API Key 配置失败 | 检查 Key 是否完整复制，没有多余空格 |
| Skill 加载报错 | 检查网络连接，确认能访问 GitHub |
| CLI 命令找不到 | 确认 OpenWork 已更新到最新版 |

现场有助教可以帮你解决——举手即可。

更多问题参考 [FAQ →](/faq/)

---

## Workshop 之后

- 📖 [完整文档](/guide/) — 随时回来查阅
- 🎯 [精选 Skills](/skills/) — 发现更多场景
- ✨ [分享你的案例](/showcase/) — 告诉我们你怎么用的
- 💬 加入社群 — 持续交流（见现场引导）

---

> 本页面会在每场 Workshop 后更新。[帮我们改进 →](https://github.com/ModelStudioAI/modelstudioai.github.io/edit/main/workshop/index.md)
