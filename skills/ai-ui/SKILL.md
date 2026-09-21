---
name: ai-ui
description: Lightweight, accessible Astro components for AI reasoning traces, streaming chat states, thinking indicators, execution pipelines, tool inspectors, and text animations. Use when an agent needs to install, compose, or customize AI UI interfaces in Astro without React, Radix, or Tailwind.
---

# ai-ui Skill

Expert guide and machine-readable reference for installing, configuring, and composing the `@michaelvereb/ai-ui` component library in Astro projects.

> **Stack Philosophy:** 100% native Astro, Vanilla JavaScript, and native CSS custom properties. Strictly zero React, zero Radix, and zero Tailwind CSS. Strictly zero emojis in code or UI.

---

## When To Use

Activate this skill whenever:
- Building AI interfaces, chatbots, agent reasoning flows, thinking indicators, diagnostic pipelines, or tool call inspectors in Astro.
- Installing or updating `@michaelvereb/ai-ui` in an Astro 4/5 project.
- Composing AI chat components: `<Reasoning />`, `<ThinkingBar />`, `<Steps />`, `<Tool />`, `<ChainOfThought />`, `<PromptInput />`, `<ModelSelector />`, `<Suggestions />`, `<Questions />`, `<FeedbackBar />`, `<Attachments />`, `<Citation />`, `<Message />`, `<Thread />`, `<Loader />`, `<TextShimmer />`, `<Image />`, `<Toaster />`, `<ThemeCustomizer />`, or `<AnimateText />`.
- Customizing theme tokens, surfaces, brand heat colors, or dark mode styling using native CSS custom properties.

---

## 1. Installation

### Method A: Direct GitHub Resolver (Standard & Recommended)

Install `@michaelvereb/ai-ui` directly from GitHub with zero npmjs registry delays:

```bash
npm install github:michaelvereb/ai-ui
# Or with alternative package managers:
# pnpm add github:michaelvereb/ai-ui
# bun add github:michaelvereb/ai-ui
# yarn add github:michaelvereb/ai-ui
```

To update to the latest `main` branch at any time:
```bash
npm update @michaelvereb/ai-ui
# or force-fetch latest main:
pnpm add github:michaelvereb/ai-ui#main
```

### Method B: Direct Component Copy (Zero-Dependency CLI)

If you prefer vendoring components directly into your source tree without adding a package dependency:

```bash
git clone https://github.com/michaelvereb/ai-ui.git ./tmp-ai-ui
mkdir -p ./src/components/ai-ui ./src/components/animations ./src/styles
cp -r ./tmp-ai-ui/src/components/ai-ui/* ./src/components/ai-ui/
cp -r ./tmp-ai-ui/src/components/animations/* ./src/components/animations/
cp ./tmp-ai-ui/src/styles/theme.css ./src/styles/theme.css
rm -rf ./tmp-ai-ui
```

---

## 2. Global Theme & Layout Setup

### Step 1: Import `theme.css` in Your Root Layout

In your universal layout (e.g. `src/layouts/Layout.astro` or `src/layouts/BaseLayout.astro`):

```astro
---
// Package install:
import '@michaelvereb/ai-ui/theme.css';

// OR if vendored via Direct Copy:
// import '../styles/theme.css';

interface Props {
  title?: string;
}

const { title = 'AI Agent Workspace' } = Astro.props;
---

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{title}</title>
  </head>
  <body>
    <slot />
  </body>
</html>
```

### Step 2: Native CSS Design Tokens

`theme.css` establishes semantic variables for colors, surfaces, borders, and typography:

```css
:root {
  /* Brand Heat Orange */
  --heat: #ED5F45;
  --primary: var(--heat);
  --primary-hover: #e04f35;
  --heat-subtle: rgba(237, 95, 69, 0.08);
  --heat-glow: 0 0 24px rgba(237, 95, 69, 0.2);

  /* Surfaces & Canvas (Crisp Light Mode Default) */
  --bg: #ffffff;
  --bg-subtle: #fafafa;
  --surface: #ffffff;
  --surface-raised: #f4f4f5;
  --surface-hover: #ececef;

  /* Typography */
  --font-sans: 'Geist', -apple-system, BlinkMacSystemFont, 'SF Pro', sans-serif;
  --font-mono: 'Geist Mono', ui-monospace, Menlo, monospace;
  --tracking-ui: -0.02em;

  /* Borders & Radii */
  --border: #e4e4e7;
  --border-muted: #f0f0f2;
  --radius-card: 24px;
  --radius-pill: 9999px;
  --radius-sm: 10px;
}

/* Dark Mode Activation */
html.dark,
html[data-theme="dark"] {
  --bg: #09090b;
  --bg-subtle: #0e0e11;
  --surface: #131316;
  --surface-raised: #18181c;
  --surface-hover: #1e1e24;
  --border: #232328;
  --text: #fcfcfc;
  --text-muted: #a1a1aa;
}
```

---

## 3. Component Catalog & Quick Reference

### Named Imports vs. Subpath Imports

```astro
---
// Option 1: Named Imports (Concise)
import { 
  Reasoning, 
  ThinkingBar, 
  Steps, 
  Tool, 
  PromptInput, 
  Suggestions, 
  Citation, 
  Toaster 
} from '@michaelvereb/ai-ui';

// Option 2: Subpath Imports (0ms tree-shaking overhead)
import Reasoning from '@michaelvereb/ai-ui/Reasoning.astro';
import ThinkingBar from '@michaelvereb/ai-ui/ThinkingBar.astro';
import Steps from '@michaelvereb/ai-ui/Steps.astro';
---
```

---

### Component Specifications

#### 1. `<Reasoning />` — Thought Stream
Collapsible thought process with sequential verification checkmarks down each step.
```astro
---
import { Reasoning } from '@michaelvereb/ai-ui';

const thoughtSteps = [
  { text: 'Parsed user prompt and extracted domain entities', detail: 'Identified target parameter constraints.' },
  { text: 'Inspecting edge DNS, HTTP/2, and TLS 1.3 handshake', detail: 'HSTS max-age=31536000 verified. Edge TTFB: 124ms.' },
  { text: 'Validating RFC 8259 single-pass JSON-LD structured data', detail: 'Zero double-escaped HTML entities.' }
];
---
<Reasoning title="Reasoning Trace" steps={thoughtSteps} defaultOpen={true} />
```

#### 2. `<ThinkingBar />` — Active LLM Reasoning Indicator
Floating animated indicator with text shimmer, active spinner/pulse, and rotating diagnostic descriptions.
```astro
---
import { ThinkingBar } from '@michaelvereb/ai-ui';

const phases = [
  'Auditing edge security headers...',
  'Probing crawler reachability (Claude-User / GPTBot)...',
  'Synthesizing diagnostic recommendations...'
];
---
<ThinkingBar phases={phases} isStreaming={true} autoCycle={true} cycleIntervalMs={3500} />
```

#### 3. `<Steps />` — Multi-Step Execution Pipeline
Technical workflow pipeline with status badges (`completed`, `running`, `pending`, `failed`), timings, and expandable technical drawer.
```astro
---
import { Steps } from '@michaelvereb/ai-ui';

const pipeline = [
  { id: '1', title: 'Fetch Target DOM', status: 'completed', duration: '142ms', details: 'Direct HTML fetch via edge worker.' },
  { id: '2', title: 'Validate Structured Data', status: 'running', duration: '85ms', details: 'RFC 8259 compliance verified.' },
  { id: '3', title: 'Audit Bot Discovery', status: 'pending', details: 'Verify llms.txt and WebMCP declarations.' }
];
---
<Steps title="Agent Diagnostic Pipeline" steps={pipeline} defaultOpen={true} />
```

#### 4. `<Tool />` — Tool Call Payload Inspector
Structured card for inspecting MCP tool calls and function executions with collapsible JSON payloads.
```astro
---
import { Tool } from '@michaelvereb/ai-ui';
---
<Tool 
  name="cloudflare_dns_lookup" 
  status="completed" 
  defaultOpen={false}
  input={{ domain: "www.michaelvereb.com", type: "AAAA" }}
  output={{ address: "100::", proxied: true, ttl: "auto" }} 
/>
```

#### 5. `<ChainOfThought />` — Visual Reasoning Graph
Visual step nodes connected by continuous vertical SVG paths.
```astro
---
import { ChainOfThought } from '@michaelvereb/ai-ui';

const nodes = [
  { title: 'Evaluate Search Intent', status: 'completed', detail: 'Classified query as technical audit.' },
  { title: 'Retrieve Knowledge Base', status: 'active', detail: 'Querying Directus collections.' },
  { title: 'Generate Markdown Output', status: 'pending' }
];
---
<ChainOfThought nodes={nodes} />
```

#### 6. `<PromptInput />` — AI Composer Bar
Accessible textarea with model badge, attachment trigger, keyboard shortcuts (`Enter` to submit, `Shift+Enter` for newline).
```astro
---
import { PromptInput } from '@michaelvereb/ai-ui';
---
<PromptInput 
  placeholder="Enter agent prompt or domain to audit..." 
  selectedModel="Claude 3.5 Sonnet"
  submitLabel="Execute" 
  allowAttachments={true} 
/>
```

#### 7. `<ModelSelector />` — Provider Dropdown
Dropdown for selecting LLM models, provider tiers, and parameters.
```astro
---
import { ModelSelector } from '@michaelvereb/ai-ui';
---
<ModelSelector selectedId="claude-3-5-sonnet" />
```

#### 8. `<Suggestions />` — Quick Action Chips
One-click recommendation pills that populate prompt inputs or execute canned audit runs.
```astro
---
import { Suggestions } from '@michaelvereb/ai-ui';
---
<Suggestions suggestions={[
  'Audit domain for AI readiness',
  'Verify RFC 8259 single-pass JSON-LD',
  'Check Claude-User crawler reachability'
]} />
```

#### 9. `<Questions />` — Clarification Questionnaire
Interactive card for multi-choice or single-select user clarification prompts.
```astro
---
import { Questions } from '@michaelvereb/ai-ui';

const options = [
  { id: 'opt-1', label: 'Standard Quick Scan', description: 'Checks DNS, SSL, and security headers.' },
  { id: 'opt-2', label: 'Full 30-Point Site-Ready Audit', description: 'Deep audit of schemas, llms.txt, and bot rules.' }
];
---
<Questions question="Select audit depth level:" options={options} isMultiSelect={false} />
```

#### 10. `<FeedbackBar />` — Rating & Actions
Inline feedback bar with thumbs up/down rating, copy to clipboard, and report triggers.
```astro
---
import { FeedbackBar } from '@michaelvereb/ai-ui';
---
<FeedbackBar />
```

#### 11. `<Attachments />` — File Attachment Chips
Clean chips displaying uploaded files, MIME badges, byte sizes, and dismiss actions.
```astro
---
import { Attachments } from '@michaelvereb/ai-ui';

const files = [
  { id: 'f1', name: 'schema.json', size: '4.2 KB', type: 'json' },
  { id: 'f2', name: 'audit-trace.log', size: '18.9 KB', type: 'log' }
];
---
<Attachments files={files} />
```

#### 12. `<Citation />` — Source Reference Badges
Numbered citation pills with automatic domain favicons and external target links.
```astro
---
import { Citation } from '@michaelvereb/ai-ui';
---
<Citation 
  index={1} 
  title="ai-ui — Astro AI Design System & Chat Interfaces" 
  url="https://www.michaelvereb.com/ai-ui" 
/>
```

#### 13. `<Message />` & `<Thread />` — Chat Stream
Semantic containers for AI dialogue streams with avatars, timestamps, and copy actions.
```astro
---
import { Message, Thread } from '@michaelvereb/ai-ui';
---
<Thread title="Security Audit Session">
  <Message role="user" authorName="Developer">Run 30-point audit on example.com.</Message>
  <Message role="assistant" authorName="Agent" timestamp="Just now">
    Audit completed: Status 200 OK. Zero-trust headers verified.
  </Message>
</Thread>
```

#### 14. `<Loader />` — Status Indicators
Lightweight SVG and CSS animated loaders: `spinner`, `dots`, `pulse`, or `progress`.
```astro
---
import { Loader } from '@michaelvereb/ai-ui';
---
<Loader variant="spinner" size="md" />
<Loader variant="progress" progress={72} />
```

#### 15. `<TextShimmer />` — Gradient Shimmer Text
GPU-accelerated gradient sweep across text signaling active generation.
```astro
---
import { TextShimmer } from '@michaelvereb/ai-ui';
---
<TextShimmer text="Synthesizing remediation plan..." duration="2.5s" />
```

#### 16. `<Toaster />` — Global Toast Notifications
Non-intrusive alert pill mounted at screen bottom, triggered from client JavaScript.
```astro
---
import { Toaster } from '@michaelvereb/ai-ui';
---
<!-- Place once in layout or page -->
<Toaster />

<!-- Trigger from anywhere in client scripts -->
<script>
  window.dispatchEvent(new CustomEvent('ai-toast', {
    detail: { message: 'Copied agent prompt to clipboard!', type: 'success' }
  }));
</script>
```

#### 17. `<ThemeCustomizer />` — Live Design Drawer
Figma-style interactive side panel letting users tune base colors, fonts, and radii with instant CSS clipboard export.
```astro
---
import { ThemeCustomizer } from '@michaelvereb/ai-ui';
---
<ThemeCustomizer />
```

#### 18. `<AnimateText />` — 20 Kinetic WAAPI Text Effects
GPU-accelerated text reveal and entrance animations (e.g. `soft-blur-in`, `typewriter`, `spring-scale-in`, `line-by-line-slide`).
```astro
---
import { AnimateText } from '@michaelvereb/ai-ui';
---
<AnimateText effect="soft-blur-in" text="Audit verified with 100% pass rate." />
```

---

## 4. Common Agent Composition Workflows

### Pattern 1: Streaming Agent Reasoning Session

```astro
---
import { 
  Thread, 
  Message, 
  ThinkingBar, 
  Reasoning, 
  Tool, 
  Citation, 
  PromptInput 
} from '@michaelvereb/ai-ui';
---

<div class="ai-agent-container">
  <Thread title="Site-Ready Audit">
    <Message role="user">Check bot reachability for michaelvereb.com.</Message>
    
    <Reasoning steps={[
      { text: 'Probing Claude-User endpoint', detail: 'HTTP 200 OK returned with raw semantic HTML.' },
      { text: 'Inspecting robots.txt and WAF rules', detail: 'Zero challenge or 403 blocks.' }
    ]} />

    <Tool 
      name="probe_crawler" 
      status="completed" 
      input={{ url: "https://www.michaelvereb.com" }} 
      output={{ status: 200, reached: true }} 
    />

    <Message role="assistant">
      Your domain is 100% reachable and citable by autonomous agents.
    </Message>

    <Citation index={1} title="ai-ui Documentation" url="https://www.michaelvereb.com/ai-ui" />
  </Thread>

  <PromptInput placeholder="Ask a follow-up question..." submitLabel="Send" />
</div>
```

---

## 5. Architectural Safeguards & Purity Rules

1. **Anti-Tailwind:** Never introduce Tailwind CSS classes. Style custom containers using scoped CSS with native CSS variables (`var(--heat)`, `var(--surface)`, `var(--bg)`).
2. **Zero-React:** Never convert components into React/JSX. Keep them in pure `.astro` files with Vanilla JS micro-interactions.
3. **No Emojis:** Strictly no emojis in code, labels, or UI elements. Use clean SVG line icons.
4. **Universal Live Discovery:**
   - Interactive Demo: `https://www.michaelvereb.com/ai-ui`
   - Agent Setup Prompt: `https://www.michaelvereb.com/ai-ui/prompt.md`
   - GitHub Repository: `https://github.com/michaelvereb/ai-ui`
