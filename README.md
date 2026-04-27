<div align="center">

# ☠ STATICVERSE

**A horror-themed cyber portfolio for a 10-year-old Roblox developer.**
Built as a birthday gift. Forsaken aesthetic. Pure HTML. Zero dependencies.

[![Built With](https://img.shields.io/badge/built_with-vanilla_HTML-ff0033?style=for-the-badge)](https://developer.mozilla.org/)
[![Lines of Code](https://img.shields.io/badge/lines-7%2C300+-9b59ff?style=for-the-badge)](#)
[![Dependencies](https://img.shields.io/badge/dependencies-zero-39ff14?style=for-the-badge)](#)
[![Made With](https://img.shields.io/badge/made_with-♥-ffb800?style=for-the-badge)](#)

[**Live Demo →**](https://staticverse-elek.netlify.app) · [**For Static**](https://www.roblox.com/users/7477228506/profile) · [**ES_AR**](https://en.wikipedia.org/wiki/Voseo)

---

```
█▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀█
█  TRANSMISIÓN ENTRANTE · CANAL 22 · EN VIVO  █
█▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄█
```

</div>

## ▼ ¿Qué es esto?

A single-page interactive birthday site for **Static** (a 10-year-old Argentine Roblox creator) — built as a horror-cyberpunk shrine to his work. Two HTML files. No frameworks. No build step. Drop on any static host and it runs.

The brief: take a kid's existing online presence — his 9 Roblox horror games, his YouTube animations, his obsession with the game *Forsaken* — and reflect it back at him as something larger than life. A piece of internet that exists *for him*.

## ▼ Stack

```
HTML5 ─────────── semantic, accessible
CSS3 ───────────── custom properties, grid, animations, blend modes
Vanilla JS ─────── ES6+, no transpilation, no bundler
Google Fonts ───── 6 typefaces (Rubik Glitch, VT323, Press Start 2P, JetBrains Mono, Russo One, Big Shoulders)
SVG ────────────── inline icons + cursor + animated stars
```

**No build pipeline. No package.json. No `node_modules`.** Open `index.html` in a browser → it works.

## ▼ Features

### 🎮 Boot sequence
Terminal-style "DAMNATION.OS" boot screen that types itself out, finds files, glitches, and reveals the page. Pure CSS animations + a few setTimeout chains.

### 🎴 Player card
Forsaken-themed avatar card with the kid's actual Roblox profile picture (base64-embedded `.webp`, red duotone via `mix-blend-mode: multiply`). Hover the avatar — it desaturates back to color, like waking up. Stats blocks (NVL, MUNDOS, ALMAS, CLASE) have animated tooltips and shimmer effects on hover. Direct CTA to his Roblox profile.

### 🎯 9 Roblox games
Real CDN thumbnails pulled from `tr.rbxcdn.com`, real game links, descriptions in Argentine Spanish (voseo: *sos*, *apretá*, *andá*).

### 🧠 Quiz "¿QUIÉN SOS?"
12 character profiles split into 2 factions (6 KILLERS / 6 SURVIVORS), 12 weighted questions, faction-aware UI that switches between blood-red and cyan. Result includes shareable card with WhatsApp / Discord deep-links and Web Share API fallback.

### 📺 Retro YouTube console
A CRT-styled TV that loads his actual YouTube channel videos. Hardcoded 18-video list with thumbs from `i.ytimg.com`, thematic tags (🎵 SPRUNKI, ⛏ MINECRAFT, 🎮 ROBLOX, ⭐ ESPECIAL...), keyboard navigation (↑↓ A B), and a fully-styled gamepad. Glitch transition on video select.

### 📚 100 trucos (interactive)
Searchable, tabbed grid of 100 Roblox Studio lifehacks. Click any card → full-screen modal with extended explanations, Luau code samples (custom syntax highlighter, no Prism.js), and chained "related tricks" that turn the database into a navigable knowledge graph.

### 📕 14-chapter course (`curso.html`)
Standalone companion site — 14 chapters of Roblox Studio mastery (Studio anatomy, Luau scripting, monetization, marketing, 2026 trends), with reading progress bar, animated bar charts, interactive checklists, copy-to-clipboard code blocks, and stat callouts. ~92 KB single file.

### ✨ Comet cursor
Custom 4-spike SVG cursor with a particle trail (object-pooled — 30 reusable elements, never creates/destroys DOM). Color-aware: switches to gold over links, toxic-green over code blocks, cyan over survivors, blood-red over killers. Disabled on touch devices.

### 🎂 Birthday easter egg
Hidden overlay revealed by Konami code (↑↑↓↓←→←→BA), 10 clicks on the skull, or a button. Animated star field, glitch reveal of his real name, personalized message about his 9 games and 159 souls.

## ▼ Architecture decisions

> **Why no framework?**
> Two HTML files, two months of edits, one 10-year-old recipient. React adds a build step, version drift, and deployment complexity for zero user-facing benefit. Vanilla scales fine to ~5K LoC with discipline.

> **Why hardcoded video list instead of YouTube API?**
> Tried it. CORS blocks the RSS feed. Tried 5 public CORS proxies — they rate-limit, get cached as Cloudflare captchas, or just go down. YouTube Data API v3 works but requires an API key (overkill for this scale). Hardcoded array with thumbnails from `i.ytimg.com/vi/{ID}/mqdefault.jpg` (no CORS on images) is the most reliable path. Update the array when new videos drop.

> **Why so much CSS?**
> Most of the "magic" lives in CSS — glitch text via dual `text-shadow` offsets and `clip-path`, CRT scanlines via `repeating-linear-gradient`, vignette via `radial-gradient` mask, grain via inline SVG `feTurbulence`. CSS is the renderer. JS just orchestrates state.

> **Why six font families?**
> Each conveys a register: `Rubik Glitch` for chaos, `VT323` for terminal, `Press Start 2P` for retro game UI, `JetBrains Mono` for code, `Russo One` for impact text, `Big Shoulders Display` for editorial headings. Total ~180 KB woff2, all loaded once with `display:swap`.

## ▼ Mobile

Six breakpoints (1024 / 900 / 768 / 600 / 480 / 380) plus a landscape-orientation rule. iOS-specific:
- `viewport-fit=cover` for notch / Dynamic Island
- `env(safe-area-inset-*)` padding so content respects rounded corners
- `theme-color` for the address bar
- `overscroll-behavior:none` to kill rubber-band bounce
- `-webkit-tap-highlight-color:transparent` to kill the blue tap flash
- Custom cursor + particles disabled on `(hover:none),(pointer:coarse)`
- All interactive elements respect Apple HIG's 44×44px minimum

Tested on iPhone SE 1G (320px) up through iPad Mini.

## ▼ File map

```
.
├── index.html        ← main site (~5,300 lines, ~250 KB)
├── curso.html        ← companion course (~1,900 lines, ~92 KB)
├── netlify.toml      ← cache headers, redirects
└── README.md         ← you are here
```

## ▼ Deploy

```bash
# clone
git clone https://github.com/<you>/staticverse.git

# open
open index.html

# deploy
git push  # → Netlify rebuilds in ~30s
```

**Netlify**: connect this repo, leave build command empty, publish directory `.` — done. Free tier handles this comfortably.

**GitHub Pages**: Settings → Pages → Source: main branch → root → done. Same result, slightly slower CDN.

**Cloudflare Pages**: same flow, marginally faster edge network.

## ▼ Localization note

The entire site is in **Argentine Spanish** (voseo conjugations: *sos*, *apretá*, *andá*, *che*). This is intentional and non-negotiable — the recipient doesn't speak English, and *Spanish-Spain* (*tú*, *coge*) would feel foreign. If you fork this for someone in a different region, swap the strings, not just the language code.

## ▼ Credits

- Built across 9+ iterative sessions with Claude (Anthropic)
- Inspired by *Forsaken* (Roblox horror game) and the cyberpunk-terminal aesthetic of Severance/Mr. Robot
- Roblox CDN, YouTube CDN, Google Fonts — all CORS-friendly, all free
- Argentine Spanish localization care of one Russian-speaking dad in Buenos Aires

## ▼ License

Personal gift. Source is here for reference and learning. If you want to adapt this for your own kid, please **strip the personal content** (name, handles, avatar, game list, video list) and rebuild around theirs — the structure is reusable, the soul isn't.

---

<div align="center">

```
DIBUJADO A MANO EN LA OSCURIDAD ● TRANSMITIENDO DESDE BUENOS AIRES ● EN VIVO
```

**Para Static · 10 años · Abril 2026**

</div>
