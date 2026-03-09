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

## 📦 Requirements

- Python 3.7+
- Playwright: `pip install playwright && playwright install firefox`
- Firefox with an active X/Twitter login
- *(Headless servers only)* Xvfb: `Xvfb :1 &`

---

## 🚀 Quick Start

### 1. Export your X session cookies

```bash
bash scripts/export-x-cookies.sh
```

> Cookies are saved to `secrets/x-cookies.json` by default.  
> Custom path: `FOXX_COOKIES_OUT=/custom/path.json bash scripts/export-x-cookies.sh`

### 2. Run the environment health check

```bash
bash scripts/check-firefox-env.sh
```

### 3. Run a plan

```bash
DISPLAY=:1 python3 scripts/playwright-firefox-control.py --plan /tmp/foxx-plan.json
```

---

## 📋 Plan Examples

### View a profile

```json
{
  "needs_gui": true,
  "gui_reason": "site_only_action",
  "url": "https://x.com/elonmusk",
  "cookies_path": "secrets/x-cookies.json",
  "steps": [
    { "action": "wait", "ms": 4000 },
    { "action": "screenshot", "path": "/tmp/foxx-profile.png" }
  ],
  "close_delay_ms": 3000
}
```

### Search live tweets

```json
{
  "needs_gui": true,
  "gui_reason": "site_only_action",
  "url": "https://x.com/search?q=AI+agents&src=typed_query&f=live",
  "cookies_path": "secrets/x-cookies.json",
  "steps": [
    { "action": "wait", "ms": 4000 },
    { "action": "screenshot", "path": "/tmp/foxx-search.png" }
  ],
  "close_delay_ms": 3000
}
```

### Fetch a tweet

```json
{
  "needs_gui": true,
  "gui_reason": "site_only_action",
  "url": "https://x.com/user/status/123456789",
  "cookies_path": "secrets/x-cookies.json",
  "steps": [
    { "action": "wait", "ms": 3000 },
    { "action": "content", "selector": "article" },
    { "action": "screenshot", "path": "/tmp/foxx-tweet.png" }
  ],
  "close_delay_ms": 3000
}
```

---

## ⚙️ Plan Options

| Field | Required | Description |
|---|---|---|
| `needs_gui` | ✅ | Must be `true` to launch browser |
| `gui_reason` | ✅ | `login`, `captcha`, `mfa`, `visual_verification`, or `site_only_action` |
| `url` | ✅ | Starting URL |
| `cookies_path` | optional | Path to exported cookies JSON |
| `close_delay_ms` | optional | Wait (ms) before closing (default: `3000`) |
| `storage_state_path` | optional | Save session state to this path after run |

---

## 🎬 Supported Step Actions

| Action | Description |
|---|---|
| `goto` | Navigate to a URL |
| `click` | Click an element by selector |
| `fill` | Fill an input by selector |
| `type` | Type text with a human-like delay |
| `press` | Press a keyboard key |
| `wait` | Wait for N milliseconds |
| `wait_for_selector` | Wait for an element to appear |
| `screenshot` | Capture a screenshot |
| `content` | Extract inner text from an element |

---

## 🔧 Tips

- Always include a `wait` step (min 3000ms) after navigation
- A validation screenshot is auto-taken before the browser closes
- If X redirects to the login page, re-run `export-x-cookies.sh`
- Always close the browser after your task — don't leave it idle

---

## 📄 License

MIT
