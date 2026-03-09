<p align="center">
  <img src="baymax.png" width="120" alt="Baymax" />
</p>

# 🦊 Ganidhuz-FoxX

> Browse X/Twitter with a real logged-in Firefox session — no API key, no bot blocks.

Built because Chromium kept getting flagged by X. FoxX uses Playwright + Firefox with your actual session cookies to view profiles, fetch tweets, search feeds, and more.

---

## ✨ Features

- **No API key required** — uses your real browser session
- **No bot blocks** — Firefox + cookie injection flies under the radar
- **Headless server support** — runs on VPS/Linux via Xvfb
- **Flexible plan system** — define actions in JSON (navigate, click, screenshot, extract)
- **OpenClaw skill** — plug-and-play with [OpenClaw](https://openclaw.ai)

---

## 🚀 Install

Paste this into OpenClaw or any compatible agent:

```
clawhub install ganidhuz-foxx
```

That's it. The skill handles the rest.

---

## 📋 Usage Examples

### View a profile

```json
{
  "url": "https://x.com/elonmusk",
  "steps": [{ "action": "wait", "ms": 4000 }, { "action": "screenshot", "path": "/tmp/profile.png" }]
}
```

### Search live tweets

```json
{
  "url": "https://x.com/search?q=AI+agents&src=typed_query&f=live",
  "steps": [{ "action": "wait", "ms": 4000 }, { "action": "screenshot", "path": "/tmp/search.png" }]
}
```

### Fetch a tweet

```json
{
  "url": "https://x.com/user/status/123456789",
  "steps": [{ "action": "wait", "ms": 3000 }, { "action": "content", "selector": "article" }]
}
```

---

## 📄 License

MIT

---

<p align="center">
  <sub>Built by Ganidhu and Baymax</sub>
</p>
