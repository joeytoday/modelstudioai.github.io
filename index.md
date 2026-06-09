---
layout: home
title: Home
---

# Model Studio AI

**AI Agent Skills & Tools — powered by Aliyun Model Studio**

One command to orchestrate 10+ foundation models. Build real AI Agents from your terminal.

---

## Quick Start — 3 Steps

### 1. Install

```bash
npm install -g bailian-cli
```

> Requires Node.js >= 22.12

### 2. Authenticate

Get your free API Key: [Aliyun Model Studio Console](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

```bash
bl auth login --api-key sk-xxxxx
```

### 3. Go

```bash
# Chat with Qwen
bl text chat --message "Hello, what can you do?"

# Generate an image
bl image generate --prompt "A cat astronaut on Mars" --out-dir ./images/

# Generate a video
bl video generate --image ./cat.png --prompt "Make it move" --download cat.mp4
```

---

## What's Here

| Section | Description |
|---------|-------------|
| [Guide](./guide/) | Complete getting-started tutorial |
| [CLI](./cli/) | Aliyun Model Studio CLI — full-modal AI from your terminal |
| [OpenWork](./openwork/) | Desktop AI agent workspace |
| [Skills](./skills/) | Curated Agent Skills collection |
| [Workshop](./workshop/) | Upcoming hands-on events |
| [Showcase](./showcase/) | Community projects & demos |
| [Videos](./videos/) | Video tutorials |
| [FAQ](./faq/) | Frequently asked questions |

---

## Links

- [GitHub Org](https://github.com/modelstudioai)
- [CLI Site](https://bailian.console.aliyun.com/cli?source_channel=cli_github&)
- [API Documentation](https://help.aliyun.com/zh/model-studio/)
- [Get API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

---

*Built with ❤️ by Model Studio AI*
