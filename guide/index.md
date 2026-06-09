---
layout: page
title: Guide
permalink: /guide/
---

# Getting Started with Model Studio AI

A complete walkthrough from zero to your first AI Agent workflow.

---

## Prerequisites

- **Node.js** >= 22.12 ([download](https://nodejs.org))
- **API Key** — [Get yours free](https://bailian.console.aliyun.com/cn-beijing/?source_channel=key_github&tab=app#/api-key)

---

## Step 1: Install the CLI

```bash
npm install -g bailian-cli
```

Install the Agent Skills:

```bash
npx skills add modelstudioai/cli --all -g
```

---

## Step 2: Authenticate

```bash
# Recommended: API Key authentication
bl auth login --api-key sk-xxxxx

# Or: Browser-based console login (for app list / usage commands)
bl auth login --console
```

---

## Step 3: Explore Capabilities

### Text Chat

```bash
bl text chat --message "Explain quantum computing in simple terms"
```

### Multimodal (Omni)

```bash
bl omni --message "Describe this image" --image ./photo.jpg
```

### Image Generation

```bash
bl image generate --prompt "A cyberpunk cityscape at sunset" --out-dir ./output/
```

### Video Generation

```bash
bl video generate --image ./scene.png --prompt "Add cinematic camera movement" --download output.mp4
```

### Speech Synthesis

```bash
bl speech synthesize --text "Hello, welcome to Model Studio" --voice cosyvoice-v1 --output hello.mp3
```

### Web Search

```bash
bl text chat --message "What are the latest AI developments this week?" --enable-search
```

---

## Step 4: Install Agent Skills

Skills are reusable workflow units that extend your AI Agent's capabilities:

```bash
# Browse and install curated skills
npx skills add modelstudioai/skills

# Install a specific community skill
npx skills add JohnKeating1997/spark-video
```

---

## Step 5: Build Your Own

Combine CLI commands and skills to create complete AI Agent workflows. See [Showcase](../showcase/) for community examples.

---

## Next Steps

- [CLI Reference](../cli/) — All commands and options
- [Skills Collection](../skills/) — Browse curated skills
- [FAQ](../faq/) — Common questions answered

---

*Built with ❤️ by Model Studio AI*
