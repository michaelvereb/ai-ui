# ai-ui

> Lightweight, accessible Astro components for AI reasoning traces, streaming state, and autonomous agent interfaces. 100% native Astro, Vanilla JS, and CSS variables. Zero React, zero Radix, zero Tailwind.

**Live Interactive Showcase & Theme Customizer:**  
[https://www.michaelvereb.com/ai-ui](https://www.michaelvereb.com/ai-ui)

---

## Overview

Traditional UI kits are bloated with React runtimes, large bundle payloads, and complicated configuration trees. **ai-ui** is built specifically for autonomous agents, streaming LLM interfaces, and diagnostic dashboards:

- **100% Astro Native:** Pure `.astro` components with 0ms client-side hydration overhead where possible.
- **Pure CSS Variables:** Themed via native CSS custom properties (`--heat`, `--surface`, `--bg`, `--radius`, `--font-sans`).
- **Zero Heavy Frameworks:** No React, no Tailwind, no Radix UI, no emotion/styled-components.
- **Agent-Install Ready:** Lean component files that coding agents (Claude, Gemini, Antigravity, Cursor) can copy and drop directly into any Astro project.

---

## Quick Start

### 1. Install or Copy

```bash
npm install @vereb/ai-ui
```

*Or copy any single component file directly from `src/components/ai-ui/` into your Astro project.*

### 2. Import Base Theme

Add the design system variables to your layout or page:

```astro
---
import '@vereb/ai-ui/theme.css';
---
```

### 3. Assemble Components

```astro
---
import Reasoning from '@vereb/ai-ui/components/Reasoning.astro';
import ThinkingBar from '@vereb/ai-ui/components/ThinkingBar.astro';
import Steps from '@vereb/ai-ui/components/Steps.astro';
---

<ThinkingBar autoCycle={true} isStreaming={true} />
<Reasoning defaultOpen={true} />
```

---

## Component Catalog

Every component is modular, accessible, and self-contained.

| Component | Description | Quick Snippet |
|---|---|---|
| **Reasoning** | Collapsible thought stream with sequential verification checkmarks | `<Reasoning defaultOpen={true} />` |
| **ThinkingBar** | Rotating diagnostic phase indicator with text shimmer | `<ThinkingBar autoCycle={true} isStreaming={true} />` |
| **Steps** | Multi-step execution pipeline with copyable technical details | `<Steps steps={stepsData} title="Diagnostic Pipeline" />` |
| **Tool** | Structured tool call card with JSON input & output inspector | `<Tool name="probe_bridge" input={input} output={output} />` |
| **ChainOfThought** | Visual reasoning nodes connected by continuous flow lines | `<ChainOfThought nodes={thoughtNodes} />` |
| **PromptInput** | AI prompt bar with model tag, file upload trigger, and submit | `<PromptInput placeholder="Enter prompt..." />` |
| **ModelSelector** | Dropdown for choosing orchestrator models and provider tiers | `<ModelSelector selectedId="claude-3-5-sonnet" />` |
| **Suggestions** | Interactive recommendation chips for standard queries | `<Suggestions suggestions={list} />` |
| **Questions** | Selectable clarification cards with single/multi select options | `<Questions question="Select depth:" options={opts} />` |
| **FeedbackBar** | Inline rating bar with thumbs up/down and report actions | `<FeedbackBar />` |
| **Attachments** | Uploaded file chips with size badges and delete triggers | `<Attachments files={files} />` |
| **Citation** | Numbered reference badge with live domain favicons | `<Citation index={1} title="RFC 8259" url="..." />` |
| **Message** | Message container with author metadata, avatars, and copy | `<Message role="assistant">Diagnostic passed.</Message>` |
| **Thread** | Conversation container grouping user and agent message streams | `<Thread title="Audit Session">...</Thread>` |
| **Loader** | Agent execution states (spinner, dots, pulse, progress bar) | `<Loader variant="spinner" size="md" />` |
| **TextShimmer** | Animated gradient sweep signaling active LLM reasoning | `<TextShimmer text="Reasoning..." />` |
| **Image** | Framed visual container with aspect ratios and caption metadata | `<Image src="..." alt="..." caption="..." />` |
| **Toaster** | Centered notification pill with auto-dismiss | `<Toaster />` |
| **ThemeCustomizer** | Live slide-out drawer for mode, base color, fonts & radius | `<ThemeCustomizer />` |
| **AnimateText** | 20 text streaming & reveal animations via native WAAPI | `<AnimateText effect="soft-blur-in" text="..." />` |

---

## Working with AI Agents

ai-ui is designed for autonomous coding agents (Claude Code, Antigravity, Cursor, Codex):

- **Machine-Readable Index:** Fetch [https://www.michaelvereb.com/ai-ui/llms.txt](https://www.michaelvereb.com/ai-ui/llms.txt) for raw documentation and API specs.
- **Agent Instructions:** Refer to [AGENTS.md](./AGENTS.md) for prompts on composing and styling components.
- **Antigravity Skill:** Load `.agents/skills/ai-ui/SKILL.md` to equip your AI agent with component generation tools.

---

## Styling & Theming

Components use native CSS custom properties defined in `:root`:

```css
:root {
  --heat: #ED5F45;             /* Primary brand accent */
  --primary: var(--heat);
  --bg: #ffffff;               /* Canvas background */
  --surface: #ffffff;          /* Card surfaces */
  --border: #e4e4e7;           /* Hairline borders */
  --radius: 0.75rem;           /* Border radius */
  --font-sans: -apple-system, BlinkMacSystemFont, 'SF Pro', sans-serif;
  --tracking-ui: -0.02em;
}

.dark,
[data-theme="dark"] {
  --bg: #09090b;
  --surface: #131316;
  --border: #232328;
  --text: #fcfcfc;
}
```

---

## License

MIT (c) 2026 [Michael Vereb](https://www.michaelvereb.com)
