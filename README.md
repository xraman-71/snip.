# ✂️ Snip — Modern Link Shortener

> A clean, minimal, 100% frontend link shortener. No server. No database. No account. Just paste, shorten, and share.

[![Live Demo](https://img.shields.io/badge/🌐%20Live%20Demo-Visit%20Site-1a1a1a?style=for-the-badge)](https://xraman-71.github.io/spin./)

![HTML](https://img.shields.io/badge/HTML-5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![No Backend](https://img.shields.io/badge/Backend-None-success?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-black?style=flat-square)

---

## ✨ Features

| Feature | Details |
|---|---|
| 🌍 **Works for Anyone** | Short links work on any device, any browser, anywhere — no account needed to open them |
| ⚡ **Instant** | Links generated in milliseconds, entirely client-side |
| 🔒 **Zero Tracking** | No data ever sent to a server — the destination is encoded into the URL itself |
| 🧠 **Self-contained Links** | Uses Base64 encoding — the full destination lives inside the short link |
| 📋 **One-click Copy** | Copy to clipboard instantly |
| 💸 **100% Free** | No ads, no premium tier, no rate limits |
| 🎨 **Premium Design** | Minimal, modern UI with Poppins + JetBrains Mono typography |

---

## 🏗️ How It Works

Snip uses **Base64 encoding** to embed the destination URL directly inside the short link — no server or database required.

```
User pastes:   https://www.youtube.com/watch?v=dQw4w9WgXcQ
               ↓ btoa(encodeURIComponent(url))
Short link:    https://yoursite.com/?r=aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1kUXc0dzlXZ1hj
               ↓ open in any browser
Redirects to:  https://www.youtube.com/watch?v=dQw4w9WgXcQ  ✅
```

When someone opens a short link, the page:
1. Detects the `?r=` query parameter
2. Decodes it using `atob()` + `decodeURIComponent()`
3. Validates it starts with `https://`
4. Redirects the user immediately via `window.location.replace()`

No localStorage. No cookies. No server. The link **is** the data.

---

## 📁 File Structure

```
snip/
├── index.html      # Main app + redirect handler (everything lives here)
├── privacy.html    # Privacy policy page
├── terms.html      # Terms of service page
└── README.md       # You're reading it
```

All three pages share the same design system, color tokens, and typography — zero dependencies, no build step, no npm.

---

## 🎨 Design System

```css
--primary:      #1a1a1a;
--bg:           #FFFFFF;
--bg-soft:      #F5F5F0;
--border-light: #DDDDD8;
--text-muted:   #7a7a72;
--font-body:    'Poppins', sans-serif;
--font-mono:    'JetBrains Mono', monospace;
```

Responsive side padding scales from `32px` on mobile to `128px` on wide screens using `clamp()` — giving the layout a rich, editorial feel at any viewport width.

---

## 🖥️ Run Locally

No build step. No npm. Just open the file:

```bash
# Clone the repo
git clone https://github.com/YOUR-USERNAME/snip.git
cd snip

# Open directly in browser
open index.html

# Or use a local dev server (optional, for accurate URL generation)
npx serve .
# → http://localhost:3000
```

> **Tip:** When running via `open index.html` (file:// protocol), generated short links will use the local file path. For proper `http://` short links, use a local server like `npx serve` or VS Code Live Server.

---

## ⚠️ Limitations

Since Snip is 100% frontend with no server:

- **Short links are longer than typical shorteners** — the destination URL is Base64-encoded, so the short link contains the full URL (encoded). It's a compacted, shareable format — not a 6-character code like `bit.ly/abc123`.
- **No analytics** — there's no way to track clicks without a server.
- **No custom slugs** — links are auto-generated from the encoded URL.
- **No editing/deleting** — once shared, a link can't be revoked (there's no server to update).

If you need those features, a backend is required.

---

## 🔐 Privacy

- No personal data is collected
- No cookies are set
- No analytics or telemetry
- The only browser storage used is `localStorage` for the link counter (purely cosmetic)
- The destination URL is encoded in the link itself — it never touches a server

See [privacy.html](./privacy.html) for the full policy.

---

## 📄 License

MIT — do whatever you want with it.

---

## 🙌 Credits

Built with:
- [Poppins](https://fonts.google.com/specimen/Poppins) — body font
- [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) — monospace font
- Vanilla HTML, CSS, and JavaScript — zero dependencies

---

<p align="center">Made with care. No servers were harmed.</p>
