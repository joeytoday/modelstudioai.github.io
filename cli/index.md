---
layout: doc
title: 阿里云百炼 CLI
permalink: /cli/
---

# 阿里云百炼 CLI

阿里云百炼 CLI 是 Model Studio AI 的命令行工具，直接调用阿里云百炼模型完成各种 AI 任务。

[阿里云百炼 CLI 控制台 →](https://bailian.console.aliyun.com/cli?source_channel=cli_github&)

---

## 安装方式

### 方式一：通过 OpenWork（推荐）

OpenWork 桌面端已内置阿里云百炼 CLI，无需单独安装：

- [下载 OpenWork →](https://github.com/ModelStudioAI/openwork)

### 方式二：独立安装

<!-- TODO: 从 CLI repo README 迁移安装命令 -->

```bash
# 安装命令示例
npm install -g @modelstudioai/cli
```

---

## 配置

### 获取 API Key

[获取阿里云百炼 API Key →](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

### 配置 Key

<!-- TODO: 从 CLI repo 迁移配置说明 -->

```bash
bailian config set api_key YOUR_API_KEY
```

---

## 常用命令

<!-- TODO: 从 CLI repo 迁移命令参考 -->

| 命令 | 说明 |
|------|------|
| `bailian config` | 配置管理 |
| `bailian skill load` | 加载 Skill |
| `bailian skill run` | 运行 Skill |
| `bailian skill list` | 查看已加载的 Skills |

---

## 更多资源

- [CLI 源码 →](https://github.com/ModelStudioAI/cli)
- [完整上手教程 →](/guide/)
- [精选 Skills →](/skills/)
