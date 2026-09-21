# AGENTS.md — ai-ui Component Integration Guidelines

> Machine-readable operating manual for AI coding assistants (Claude Code, Antigravity, Cursor, OpenAI Codex) installing or modifying components from `@michaelvereb/ai-ui`.

---

## 1. Architectural Directives

- **100% Astro & Vanilla:** All components are written in `.astro` with pure HTML, Vanilla JS, and scoped CSS. Never convert components to React, JSX, or Vue unless explicitly requested by the user.
- **Anti-Tailwind:** Never introduce Tailwind CSS utility classes. Use native CSS custom properties (`var(--heat)`, `var(--surface)`, `var(--bg)`, `var(--radius)`).
- **CSS Class Standard:** All internal component classes use the `.ai-` namespace prefix (e.g. `.ai-thinking-bar`, `.ai-reasoning-wrap`, `.ai-tool-box`).
- **No Emojis:** Use clean SVGs (Lucide-compatible) or plain text. Emojis in code or UI are strictly forbidden.
- **Toast Standard:** Use `window.aiToast('Message')` for user feedback. Never mutate button text labels on copy actions.

---

## 2. Component File Locations

All components reside in `src/components/ai-ui/`:

- `Reasoning.astro` — Thought chain with step-by-step verification
- `ThinkingBar.astro` — Floating thinking indicator with text shimmer
- `Steps.astro` — Sequential execution pipeline with technical details
- `Tool.astro` — Expandable tool call input/output payloads
- `ChainOfThought.astro` — Visual reasoning nodes with connecting lines
- `PromptInput.astro` — Minimalist prompt bar with model indicator
- `ModelSelector.astro` — Dropdown for model switching
- `Suggestions.astro` — Single-click query prompt chips
- `Questions.astro` — Interactive clarification questionnaire card
- `FeedbackBar.astro` — Response rating bar
- `Attachments.astro` — File chips with metadata
- `Citation.astro` — Domain reference badges with favicons
- `Message.astro` — Chat messages with author headers
- `Thread.astro` — Conversation grouping container
- `Loader.astro` — Agent loading indicators (spinner, dots, pulse, progress)
- `TextShimmer.astro` — Smooth text shimmer effect
- `Image.astro` — Framed media figure with captions
- `Toaster.astro` — Floating bottom notification pill
- `ThemeCustomizer.astro` — Live theme drawer
- `AnimateText.astro` (in `src/components/animations/`) — 20 WAAPI text reveal effects

---

## 3. Theme Variables

All styling depends on `src/styles/theme.css`:

```css
:root {
  --heat: #ED5F45;
  --primary: var(--heat);
  --bg: #ffffff;
  --surface: #ffffff;
  --border: #e4e4e7;
  --radius: 0.75rem;
  --font-sans: -apple-system, BlinkMacSystemFont, 'SF Pro', sans-serif;
  --tracking-ui: -0.02em;
}
```

Dark mode is triggered by adding `.dark` or `data-theme="dark"` to `<html>`.

---

## 4. Live Reference & Agent Resources

- Interactive Showcase: [https://www.michaelvereb.com/ai-ui](https://www.michaelvereb.com/ai-ui)
- GitHub Repository: [https://github.com/michaelvereb/ai-ui](https://github.com/michaelvereb/ai-ui)
- Agent Setup Prompt: [https://www.michaelvereb.com/ai-ui/prompt.md](https://www.michaelvereb.com/ai-ui/prompt.md)
- Agent Skill Manifest: [./.agents/skills/ai-ui/SKILL.md](./.agents/skills/ai-ui/SKILL.md)
- Universal MCP Endpoint: [https://www.michaelvereb.com/ai-ui/mcp](https://www.michaelvereb.com/ai-ui/mcp)

