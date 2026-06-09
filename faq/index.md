---
layout: page
title: FAQ
permalink: /faq/
---

# Frequently Asked Questions

---

## General

**Q: What is Model Studio AI?**

Model Studio AI is the open-source ecosystem for Aliyun Model Studio (Bailian). It provides CLI tools, desktop applications, and curated Agent Skills to help developers build AI-powered workflows.

**Q: Is it free to use?**

The CLI tool is free and open-source. API calls are billed through your Alibaba Cloud account. Many models offer free-tier quotas — check with `bl usage free --model <model-name>`.

**Q: What models are available?**

Aliyun Model Studio is a model aggregation platform (MaaS). One API Key gives you access to Qwen, DeepSeek, Kimi, GLM, MiniMax, and more. See the [model list](https://help.aliyun.com/zh/model-studio/getting-started/models).

---

## Installation

**Q: What's the minimum Node.js version?**

Node.js >= 22.12 is required for the CLI.

**Q: How do I get an API Key?**

Visit the [API Key management page](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key) and create a new key.

**Q: Can I use it on Windows?**

Yes. The CLI works on macOS, Linux, and Windows. OpenWork desktop app supports all three platforms.

---

## Troubleshooting

**Q: `bl: command not found`**

Run `npm install -g bailian-cli` to install globally. Make sure your npm global bin directory is in your PATH.

**Q: Authentication failed**

1. Check your API Key is valid: [Console](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)
2. Re-authenticate: `bl auth login --api-key sk-xxxxx`
3. Verify: `bl auth status`

**Q: Skills not loading**

Open a new agent session after installing skills. The agent reads `SKILL.md` on session start.

---

## Community

**Q: How can I contribute?**

- Submit Skills as PRs to [modelstudioai/skills](https://github.com/modelstudioai/skills)
- Report bugs and request features via GitHub Issues
- Join our DingTalk group: Dev@ModelStudioAI (182405011072)

---

*Built with ❤️ by Model Studio AI*
