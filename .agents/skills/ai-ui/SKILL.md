---
name: ai-ui
description: Lightweight, accessible Astro components for AI reasoning traces, streaming state, and autonomous agent interfaces.
---

# ai-ui Skill

Use this skill when designing or implementing AI chat, agent reasoning steps, diagnostic pipelines, or streaming interfaces in Astro.

## Available Components

Import components from `@vereb/ai-ui/components/*`:

- `Reasoning`: `<Reasoning defaultOpen={true} />`
- `ThinkingBar`: `<ThinkingBar autoCycle={true} isStreaming={true} />`
- `Steps`: `<Steps steps={stepsData} title="..." />`
- `Tool`: `<Tool name="..." input={...} output={...} />`
- `ChainOfThought`: `<ChainOfThought nodes={nodes} />`
- `PromptInput`: `<PromptInput placeholder="..." submitLabel="..." />`
- `ModelSelector`: `<ModelSelector selectedId="..." />`
- `Suggestions`: `<Suggestions suggestions={list} />`
- `Questions`: `<Questions question="..." options={opts} />`
- `FeedbackBar`: `<FeedbackBar />`
- `Attachments`: `<Attachments files={files} />`
- `Citation`: `<Citation index={1} title="..." url="..." />`
- `Message`: `<Message role="assistant">...</Message>`
- `Thread`: `<Thread title="...">...</Thread>`
- `Loader`: `<Loader variant="spinner" size="md" />`
- `TextShimmer`: `<TextShimmer text="..." />`
- `Image`: `<Image src="..." alt="..." caption="..." />`
- `Toaster`: `<Toaster />`
- `ThemeCustomizer`: `<ThemeCustomizer />`
- `AnimateText`: `<AnimateText effect="soft-blur-in" text="..." />`

## Rules

1. Always import `@vereb/ai-ui/theme.css` in root layouts.
2. Use native CSS variables (`--heat`, `--surface`, `--bg`). Zero Tailwind.
3. Live documentation & interactive preview: https://www.michaelvereb.com/ai-ui
