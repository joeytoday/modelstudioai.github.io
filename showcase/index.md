---
layout: doc
title: 用户案例
permalink: /showcase/
description: "社区成员使用阿里云百炼 CLI + Skills 的真实案例。从 SEO 审计到 AI Vlog 生产线，看看大家都在用 AI 做什么。"
keywords: "阿里云百炼案例,AI Agent 案例,百炼CLI,OpenWork,Showcase,社区案例"
---

# 用户案例 Showcase

来自社区成员的真实使用案例。每一个案例都是一次实践分享。

[提交你的案例 →](https://github.com/modelstudioai/modelstudioai.github.io/issues/new)

---

## AI 竞技场：跨厂商模型对比平台

**作者**：[@Unicosmos](https://github.com/Unicosmos) · 2026-06-11

开发了一个跨厂商 AI 模型对比平台。通过阿里云百炼统一 API 同时调用 DeepSeek、Kimi、GLM、MiniMax、Qwen 等厂商的 38 个模型，在文本对话、图片理解、文生图三个场景下对比输出质量、响应速度和成本。

**核心特性**：SSE 流式输出逐 token 实时渲染 · 模型按 8 厂商分组自由勾选 · 同步滚动联动所有结果卡片 · 每模型显示预估费用 · 启动时自动探测 38 模型可用性

**工具**：OpenWork + bailian-model-config / model-arena-pattern Skills + Node.js + DashScope API

![AI竞技场截图](https://github.com/user-attachments/assets/bf3bd1ca-47f2-44ee-b2c0-f6c8b65b724e)

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/13)

---

## AI Vlog 全自动生产线：从活动图片到成片一条命令搞定

**作者**：[@jamiu799](https://github.com/jamiu799) · 2026-06-11

用 Claude Code + 百炼 CLI 搭建了一条活动 Vlog 全自动生产线：从图片直播平台批量爬取活动现场 13 张照片，通过 AI 智能分析筛选并按叙事结构分类，然后调用 `bl video generate --image` 生成 I2V 动态视频、`bl speech synthesize` 生成全程配音、`bl text chat` 撰写旁白文案，最后用 ffmpeg 合成字幕 + BGM，端到端产出一支 59 秒的完整活动 Vlog。

**产出**：59 秒 / 1920×1080 / 3 个 I2V 动态片段 / CosyVoice 配音 / 全程中文字幕 / 轻快电子 BGM

**工具**：百炼 CLI（`bl video generate` / `bl speech synthesize` / `bl text chat`）+ Claude Code + ffmpeg + Node.js 爬虫

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/12)

---

## group-daily（WaytoAGI-EDU）：教育社群故事化群日报

**作者**：[@Elianyang](https://github.com/Elianyang) · 2026-06-11

把 `group-daily` Skill 改造成教育版：将用户主动提供的群聊素材整理成一份故事化群日报，并输出带 WaytoAGI-EDU 视觉体系的 HTML + PNG 长图。强调低风险离线素材模式——公开仓库不包含微信群原始记录。

**工具**：百炼 CLI `bl text chat`（素材 → story.json）+ Python 渲染脚本 + WaytoAGI-EDU 视觉素材

**仓库**：[github.com/Elianyang/group-daily-waytoagi-edu](https://github.com/Elianyang/group-daily-waytoagi-edu)

![WaytoAGI-EDU群日报效果图](https://raw.githubusercontent.com/Elianyang/group-daily-waytoagi-edu/main/assets/examples/waytoagi-edu-daily-style-confirmed.png)

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/11)

---

## MatchA：Agent-to-Agent 智能人才匹配平台

**作者**：[@zjupump](https://github.com/zjupump) · 2026-06-11

使用百炼 CLI 完成了 MatchA（Agent-to-Agent 智能人才匹配平台）的产品原型设计与功能验证。通过构建求职者 Agent 与企业招聘 Agent，实现匿名技能画像匹配、Agent 自动协商、授权访问及智能推荐等功能。

**核心流程**：求职者 Agent 发布匿名求职意图 → 企业 Agent 发布岗位需求 → 双方 Agent 自动匹配 → 企业发起访问请求 → 求职者授权 → Agent 自动协商建立联系

**工具**：百炼 CLI + DeepSeek + Python + A2A 协作框架

![MatchA截图1](https://github.com/user-attachments/assets/97eba8a4-e3dc-4052-979a-91c644a4010c)

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/9)

---

## AI 模拟辩论

**作者**：[@soulroskars](https://github.com/soulroskars) · 2026-06-11

做了一个「辩论场」AI 工作流——输入辩题，自动编排正反方辩手 + 总结员三个角色，用百炼 CLI 的 `bl text chat` 驱动，完成论点准备→立论陈词→攻防交锋→终局总结的完整辩论流程。辩题为「AI 的迅猛发展提升/降低了人类创作者的价值」。

**产出**：正方 3 条核心论点 + 反方 3 条核心论点 + 双方立论 + 2 轮攻防 + 总结员每轮跟评，输出留存为 JSON 记录

**工具**：百炼 CLI `bl text chat --messages-file` + Node.js 编排脚本

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/6)

---

## 未来提示：反向个人知识库

**作者**：[@ggly](https://github.com/ggly) · 2026-06-11

产品定位是一个反向个人知识库：不帮用户囤知识内容，而是从散落在各处的 AI 对话记录里，识别反复被外包给 AI 的能力缺口、概念盲区、流程缺口和判断盲区，然后生成可直接复制到任意 AI 工具中继续追问的高质量提示词。让人类主动学习，AI 引导。

**工具**：百炼 CLI（`bl text chat` / `bl knowledge retrieve` / `bl search web`）+ Vite + React + TypeScript + Tailwind CSS

![未来提示截图1](https://github.com/user-attachments/assets/1f6b7fea-5e0b-4024-89dd-9daa831de872)

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/5)

---

## 文风提炼：给自己的文字做一次全面体检

**作者**：[@Danheng0502](https://github.com/Danheng0502) · 2026-06-11

把 11 篇不同类型的文章从头到尾读了一遍，然后提炼出一份约 2000 字的文风参考指南（11 个章节）。发现了自己都没意识到的"技能点"：书信体+非人类视角+第二人称拟人（猫视角下的"银色太阳""推推游戏"），以及用不必要的精确数字承载无法言说的分量（"想起你足足三十七次""四百零七片落叶"）。

**最大收获**：对自己文字的判断常常和读者不一样。只凭记忆写文风总结大概率会偏，必须回到原文逐篇读、逐句看。

**工具**：OpenWork / 百炼 CLI + 文档提取脚本

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/3)

---

## SEO Audit Full：对百炼控制台做一次完整 SEO 审计

**作者**：[@JeffLi1993](https://github.com/JeffLi1993) · 2026-06-11

使用 `seo-audit-full` Skill 对百炼控制台页面做了一次完整 SEO Audit。产出结果是一份完整 SEO 审查报告，包含页面基础信息检查、Title / Description 分析、页面内容结构分析、H 标签与语义结构检查、页面可访问性问题、技术 SEO 问题和可执行的优化建议。

**工具**：OpenWork + Skill `bysocket/seo-audit-full`（`npx skills add https://modelscope.cn/skills/bysocket/seo-audit-full`）

![SEO Audit截图](https://github.com/user-attachments/assets/97b93856-7118-49a7-b32b-da05990c01b5)

> [查看原始 Issue →](https://github.com/modelstudioai/modelstudioai.github.io/issues/1)

---

## 如何贡献你的案例

在 [Issues](https://github.com/modelstudioai/modelstudioai.github.io/issues/new) 中提交你的案例，包含以下内容即可：

1. **我做了什么** — 简述你用了哪个 Skill / 命令，完成了什么任务
2. **使用的工具** — OpenWork / 百炼 CLI / 具体 Skill 名称
3. **效果展示** — 截图或描述你的产出结果
4. **踩坑记录**（可选） — 遇到了什么问题，怎么解决的

我们会在 2-3 天内审核并收录到本页面。

---

> 案例合集持续生长中。每场 Workshop 和社区活动后，我们会邀请参与者分享自己的实践。
