---
layout: page
title: CLI
permalink: /cli/
---

# Aliyun Model Studio CLI

**The official command-line interface for Aliyun Model Studio (DashScope) AI Platform**

Chat with Qwen, generate images & videos, understand images, call agents, manage memory, search the web — all from your terminal. Built for AI Agents: every command works as a structured tool call.

---

## Install

```bash
npm install -g bailian-cli
npx skills add modelstudioai/cli --all -g
```

> Requires Node.js >= 22.12

---

## Core Capabilities

| Capability | Command | Description |
|-----------|---------|-------------|
| Text Chat | `bl text chat` | Qwen3.7-max conversations |
| Multimodal | `bl omni` | Text + image + audio + video |
| Image Gen | `bl image generate` | Qwen-Image 2.0 |
| Image Edit | `bl image edit` | AI-powered image editing |
| Video Gen | `bl video generate` | HappyHorse-1.0 series |
| Video Edit | `bl video edit` | Natural-language video editing |
| Speech TTS | `bl speech synthesize` | CosyVoice streaming TTS |
| Speech ASR | `bl speech recognize` | FunAudio-ASR (30 languages) |
| Vision | `bl vision` | Qwen-VL understanding |
| Knowledge | `bl knowledge retrieve` | Multimodal RAG |
| Memory | `bl memory` | Cross-session memory |
| Apps | `bl app call` | Invoke published agents |
| MCP | `bl mcp` | Orchestrate MCP servers |
| Web Search | `bl text chat --enable-search` | Real-time internet retrieval |
| Advisor | `bl advisor recommend` | Model recommendation |

---

## Authentication

```bash
# API Key (most commands)
bl auth login --api-key sk-xxxxx

# Console login (app list, usage)
bl auth login --console
```

👉 [Get your API Key](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

---

## Links

- [GitHub Repository](https://github.com/modelstudioai/cli)
- [CLI Official Site](https://bailian.console.aliyun.com/cli?source_channel=cli_github&)
- [API Documentation](https://help.aliyun.com/zh/model-studio/)
- [Changelog](https://github.com/modelstudioai/cli/blob/main/CHANGELOG.md)

---

*Built with ❤️ by Model Studio AI*
