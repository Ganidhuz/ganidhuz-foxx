<p align="center">
  <img src="baymax.png" width="120" alt="Baymax" />
</p>

# 🦊 Ganidhuz-FoxX

> Browse X/Twitter with a real logged-in Firefox session — no API key, no bot blocks.

Built because Chromium kept getting flagged by X. 😉

FoxX uses Playwright + Firefox with your actual session cookies to view profiles, fetch tweets, search feeds, and more.

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

## 🔐 Logging In

FoxX doesn't ask for your password. It uses your real Firefox session — so you only need to log in once.

**The simple way:**
1. Open Firefox and log into X/Twitter normally
2. Run the cookie export script:
   ```bash
   bash scripts/export-x-cookies.sh
   ```
3. FoxX picks up your session automatically from there

**On a headless server?** No monitor, no problem. You can connect to your server's filesystem remotely (e.g. via Finder > Connect to Server on macOS, or any SFTP client), open the Firefox profile directory, and the export script still works the same way.

**Using a password manager?** If you store your X credentials in a vault (Bitwarden, 1Password, etc.), just have your agent retrieve them, log in once through Firefox, and export. You won't need to do it again unless your session expires.

---

## 📋 What Can It Do?

Just tell your agent what you want — FoxX handles the rest.

- 🧑 **"Show me @elonmusk's profile"** — pulls it up like a real browser, no login wall
- 🔍 **"Search X for AI agents news"** — live results, not cached garbage
- 🐦 **"Fetch this tweet"** — grabs the full text, even from long posts
- 📸 **"Screenshot this X thread"** — saves it locally for you to review
- 📰 **"Latest post from @steipete"** — grabs their most recent tweet, no scraper needed

---

## 🤝 Contributing

Got ideas? Found a bug? X blocking a new feature?

PRs and issues are very welcome! This is a community tool and it gets better when more people chip in. Even small improvements — better selectors, new step actions, docs fixes — make a real difference.

[Open an issue](https://github.com/Ganidhuz/ganidhuz-foxx/issues) or just submit a PR. Let's build it together. 🙌

---

## 📄 License

MIT

---

<p align="center">
  <sub>Built by Ganidhu and Baymax</sub>
</p>
