# Agent Setup: @vereb/ai-ui

You are configuring and installing the `@vereb/ai-ui` component library in this workspace.

## 1. Core Directives
- **Zero Bloat / 100% Astro**: Pure `.astro` components, Vanilla JavaScript, and native CSS custom properties.
- **Anti-Tailwind**: Strictly no Tailwind CSS. Do not add Tailwind classes.
- **AI Agent Native**: Optimized for AI streaming states, reasoning traces, sequential tool steps, and LLM telemetry.

## 2. Installation

### Option A: Install from npm
```bash
npm install @vereb/ai-ui
```

### Option B: Direct Component Copy (Zero Dependency)
Clone or copy components directly into `src/components/ai-ui/`:
```bash
git clone https://github.com/michaelvereb/ai-ui.git ./tmp-ai-ui
mkdir -p ./src/components/ai-ui ./src/components/animations
cp -r ./tmp-ai-ui/src/components/ai-ui/* ./src/components/ai-ui/
cp -r ./tmp-ai-ui/src/components/animations/* ./src/components/animations/
cp ./tmp-ai-ui/src/styles/theme.css ./src/styles/theme.css
rm -rf ./tmp-ai-ui
```

## 3. Global Styles & Theme Setup
Import `theme.css` in your base Astro layout or root page:
```astro
---
import '../styles/theme.css';
---
```

## 4. Key Components Quick Reference

```astro
---
import Reasoning from './components/ai-ui/Reasoning.astro';
import ThinkingBar from './components/ai-ui/ThinkingBar.astro';
import Steps from './components/ai-ui/Steps.astro';
import Tool from './components/ai-ui/Tool.astro';
import PromptInput from './components/ai-ui/PromptInput.astro';
import ModelSelector from './components/ai-ui/ModelSelector.astro';
import Toaster from './components/ai-ui/Toaster.astro';
import ThemeCustomizer from './components/ai-ui/ThemeCustomizer.astro';
---

<!-- Active LLM Thinking Bar -->
<ThinkingBar phases={['Analyzing codebase...', 'Synthesizing output...']} />

<!-- Collapsible Reasoning Trace -->
<Reasoning steps={[{ text: 'Verifying edge DNS', detail: 'HSTS max-age=31536000' }]} />

<!-- Diagnostic Step Flow -->
<Steps steps={[{ id: 'step-1', title: 'Edge Security', status: 'completed' }]} />

<!-- Tool Call & Output Inspector -->
<Tool name="probe_api" status="completed" input={{ domain: 'example.com' }} output={{ status: 200 }} />

<!-- Interactive Theme Customizer Drawer -->
<ThemeCustomizer />
```

## 5. Live Showcase & Discovery
- **Live Preview & Theme Customizer**: https://www.michaelvereb.com/ai-ui
- **GitHub Repository**: https://github.com/michaelvereb/ai-ui
- **LLM Index**: https://www.michaelvereb.com/llms.txt
