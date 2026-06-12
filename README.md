# 🔐 **DCT — Auth Bridge**

### *Vercel-hosted OAuth callback page for the Daily Coding Tracker extension.*

<div align="center">
<img src="https://img.shields.io/badge/Deploy-Vercel-000000?style=for-the-badge">
<img src="https://img.shields.io/badge/Auth-Supabase-3ecf8e?style=for-the-badge">
<img src="https://img.shields.io/badge/UI-HTML_CSS-00cfff?style=for-the-badge">
<img src="https://img.shields.io/badge/Extension-Manifest_V3-f7df1e?style=for-the-badge">
</div>

---

# 📌 **Overview**

**DCT Auth Bridge** is a minimal Vercel deployment that acts as the OAuth redirect target for the [Daily Coding Tracker](https://github.com/ItzPnav/coding-tracker-extension) Chrome extension.

It uses:

* **Supabase OAuth** — handles Google login and issues session tokens via URL hash
* **Vercel** — provides a whitelistable HTTPS URL that Supabase can safely redirect to
* **Chrome Messaging API** — passes the token back to the extension after redirect
* **Vanilla HTML/CSS/JS** — zero dependencies, instant load

> This repo exists solely for deployment. The main extension lives at [ItzPnav/coding-tracker-extension](https://github.com/ItzPnav/coding-tracker-extension).

---

# 🧠 **Architecture**

```
[ User clicks Login in DCT Extension ]
              ↓
[ Google OAuth screen ]
              ↓
[ Supabase processes auth → redirects to Vercel ]
              ↓
┌──────────────────────────────────────────────┐
│          AUTH BRIDGE (this repo)             │
│  1. Parse access_token from URL hash         │
│  2. Send token via chrome.runtime.sendMessage│
│  3. Show success UI + auto-close in 5s       │
└──────────────────────────────────────────────┘
              ↓
[ DCT Extension receives token → user is logged in ]
```

---

# 🚀 **Features**

### ✦ Token Extraction
Parses the `access_token` and `refresh_token` directly from the URL hash that Supabase appends after a successful OAuth flow.

### 📡 Extension Handoff
Sends the token back to the DCT extension using both `chrome.runtime.sendMessage` and `window.postMessage` for maximum compatibility.

### ⏱ Auto-Close
On successful login, displays a 5-second countdown and closes the tab automatically. A manual "close this tab" button is also shown.

### 🎨 Branded UI
Dark terminal aesthetic matching DCT's neon blue design language — Orbitron + Share Tech Mono, animated terminal lines, scanline overlay.

---

# ⚙️ **Tech Stack**

| Layer | Technology |
|-------|------------|
| Hosting | Vercel |
| Auth Provider | Supabase (Google OAuth) |
| Frontend | HTML + Vanilla CSS + JS |
| Extension Bridge | Chrome Messaging API |
| Typography | Orbitron, Share Tech Mono (Google Fonts) |

---

# 📦 **Setup**

1. **Clone the repo:**

```bash
git clone https://github.com/ItzPnav/success-page-for-dct.git
cd success-page-for-dct
```

2. **Deploy to Vercel:**

```bash
# Either drag-and-drop the folder in Vercel dashboard
# or use the Vercel CLI:
npx vercel
```

3. **Whitelist your Vercel URL in Supabase:**

```
Supabase Dashboard → Auth → URL Configuration → Redirect URLs
Add: https://your-project.vercel.app
```

4. **Set the redirect URL in your DCT extension's auth call:**

```bash
# In your extension's login logic, set redirect_to:
https://your-project.vercel.app
```

---

# 🛡️ **Production Tips**

* Never use the Supabase API URL (`*.supabase.co`) as a redirect target — whitelist your Vercel URL only.
* The Vercel URL is stable and permanent — once whitelisted, it won't break.
* Test the full OAuth flow in Opera GX specifically, as it has stricter redirect handling than Chrome.

---

# 🔒 **Security Notes**

* No user data is stored or logged — the page only reads the token from the URL hash and passes it to the extension.
* Token is never sent to any third-party server.
* Page has no backend — it's fully static.

---

# 📁 **Folder Structure**

```
success-page-for-dct/
│
└── index.html        # Auth bridge — the entire deployment
```

---

# 🚀 Made with passion by **pnav**

> *Bridges the gap between Supabase OAuth and the DCT Chrome extension — cleanly.*
