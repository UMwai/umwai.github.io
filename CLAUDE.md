# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio site for Wai Yang, deployed via GitHub Pages at [umwai.github.io](https://umwai.github.io).

## Agentic Engineering Philosophy

This site reflects an **agentic engineering** approach—context engineering > vibe coding.

**Core 4 Principles** (Context, Model, Prompt, Tools):
- **Context**: Define architecture and constraints upfront; let agents handle implementation
- **Model**: Route tasks to appropriate models (Opus for architecture, Sonnet for code, Haiku for search)
- **Prompt**: Invest in prompt engineering over manual coding
- **Tools**: Maximize tool-calling chains for autonomous workflows

**Multi-Agent Orchestration**: Lead agent coordinates sub-agents for specialized tasks (code review, testing, deployment). Trust agents to run longer sequences autonomously.

**Sandbox-First Development**: Agents operate in isolated environments where they can fail safely. Move from in-loop (terminal babysitting) to out-loop (agents handling workflows via GitHub/CI).

## Architecture

Single static HTML page with no build system:
- `index.html` - Complete site with inline CSS and vanilla JS (particle animation)
- `favicon.svg` - Animated SVG favicon
- No frameworks, no dependencies, no package manager

## Development

Open `index.html` in a browser. No build step required.

To preview locally with live reload:
```bash
python -m http.server 8000
# or
npx serve .
```

## Deployment

Push to `main` branch triggers automatic GitHub Pages deployment.

## Design System

- **Colors**: Dark theme (`#0a0a0a` bg, `#4a9eff` accent, `#e0e0e0` text)
- **Font**: Monospace (`SF Mono`, `Fira Code`, `Consolas`)
- **Layout**: Single column, max-width 760px, responsive grid for focus/stack sections

## Content Sections

Timeline items, focus areas, tech stack, and projects are all defined inline in `index.html`. Update content directly in the HTML.
