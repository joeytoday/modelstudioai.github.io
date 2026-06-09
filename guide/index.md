---
layout: doc
title: 完整上手教程
permalink: /guide/
---

# 完整上手教程

本教程将带你走通 **百炼 → OpenWork → CLI → Skills** 的完整链路。

> 预计用时：15-20 分钟

---

## 前置准备

### 1. 获取百炼 API Key

前往百炼平台注册并获取 API Key：

[获取 API Key →](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

### 2. 安装 OpenWork

OpenWork 桌面端已内置百炼 CLI：

- [下载 OpenWork](https://github.com/ModelStudioAI/openwork)

也可以选择独立安装百炼 CLI：

- [百炼 CLI 安装指南](/cli/)

---

## 步骤一：配置 API Key

<!-- TODO: 从 hands-on 手册迁移具体配置步骤 -->

打开 OpenWork 后，配置你的百炼 API Key：

```bash
# 示例命令（请根据实际 CLI 替换）
bailian config set api_key YOUR_API_KEY
```

---

## 步骤二：浏览精选 Skills

查看可用的精选 Skills：

- [精选 Skills 列表 →](/skills/)

每个 Skill 支持图文、视频、文字等不同场景。选择一个你感兴趣的 Skill。

---

## 步骤三：加载并运行 Skill

<!-- TODO: 从 hands-on 手册迁移具体操作步骤 -->

```bash
# 示例：从 GitHub 加载一个 Skill
bailian skill load <skill-name>

# 运行 Skill
bailian skill run <skill-name>
```

---

## 步骤四：查看结果

Skill 运行完成后，你将看到 AI 生成的产出。

<!-- TODO: 补充具体产出截图/示例 -->

---

## 下一步

- 尝试其他 [精选 Skills](/skills/)
- 分享你的使用案例 → [提交到 Showcase](/showcase/)
- 遇到问题？查看 [FAQ](/faq/)

---

> 本教程持续迭代中。发现问题或想补充内容？[欢迎提 PR](https://github.com/ModelStudioAI/modelstudioai.github.io/edit/main/guide/index.md)
