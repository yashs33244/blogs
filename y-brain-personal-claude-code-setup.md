---
title: "y-brain: How I Turned Claude Code Into a One-Person Engineering Team"
date: "2026-05-29"
tags: ["claude-code", "ai-engineering", "developer-tools", "second-brain", "productivity"]
excerpt: "I stitched together 130+ skills from Anthropic, Vercel, GStack, and Matt Pocock into a single Claude Code environment that auto-commits itself, here's why it matters."
---

I've been running a setup I call **y-brain** for a few months now. It's my personal Claude Code environment, a curated mashup of `CLAUDE.md` files, skills, agents, and hooks pulled from engineers I actually respect, plus a bunch of my own glue. It lives at [github.com/yashs33244/my-mac-claude](https://github.com/yashs33244/my-mac-claude) and installs on a fresh Mac with one line:

```bash
git clone https://github.com/yashs33244/claude-god-setup.git ~/.claude
```

That's it. No package manager. No config wizard. Claude Code auto-discovers everything from `~/.claude/skills/` via flat symlinks. The whole thing is git-tracked, and every time Claude Code emits a `Stop` event, a hook auto-commits and pushes the diff. My environment is version-controlled in a way my dotfiles never were.

## Why I built this

I'm a final-year B.Tech CS student at IIIT Una and I just finished an SDE stint at Binocs in Bangalore. I ship full-stack work daily, Next.js frontends, Python/FastAPI backends, the occasional React Native app, infra on AWS. The bottleneck was never code. It was *context-switching*. Debugging one repo, doing QA on another, writing a PRD for a third, then trying to remember which Vercel project the env var lives in.

Claude Code solves the typing. It doesn't solve the *workflow*. y-brain is the workflow layer.

## What's inside

130+ skills, organized by source collection so I can trace who wrote what:

- **`skills/anthropic/`**, Document processing that actually works. `docx`, `xlsx`, `pdf`, `pptx` skills that read, edit, and produce real files. The `pdf` skill handles OCR. The `xlsx` one writes formulas, not just CSVs pretending to be spreadsheets.
- **`skills/superpowers/`**, The discipline layer. `test-driven-development` enforces red-green-refactor before I'm allowed to write implementation code. `systematic-debugging` and `diagnose` force a reproduce → minimize → hypothesize → instrument loop instead of vibes-debugging. `verification-before-completion` blocks me from declaring "done" without checks.
- **`skills/gstack/`**, Browser stuff. `browse`, `scrape`, `automate`, plus `qa`, `canary`, `benchmark`. I can hand Claude a URL and get back Core Web Vitals, screenshots, and a bug report.
- **`skills/mattpocock/`**, Engineering taste. Refactor planning, code review, architecture deepening.
- **`skills/vercel/`**, `vercel:nextjs`, `vercel:ai-sdk`, `vercel:shadcn`, `vercel:deploy`, `vercel:env`. When I'm in a Next.js repo, Claude already knows my deployment target.
- **`skills/obsidian-second-brain/`**, 31 vault commands. `/obsidian-save`, `/obsidian-daily`, `/x-read`, `/research-deep`. Every research finding, decision, and person I meet gets written to my vault automatically.
- **`skills/token-efficient/`**, Response profiles for when I just want the answer, not the essay.

Plus design (`frontend-design`, `design-shotgun`, `theme-factory`), security (`cso`, `security-review`), and retro/health checks (`retro`, `health`).

## The philosophy

This is downstream of Karpathy's LLM Wiki idea, the notion that your knowledge base should *rewrite itself* as new information comes in, not just accumulate. The Obsidian skills implement this literally: sources update existing pages, contradictions get reconciled, scheduled agents maintain the vault while I sleep.

The skills library is the same pattern applied to *workflow*. Every skill is a crystallized version of "how a good engineer handles X." TDD isn't a vibe anymore, it's a `SKILL.md` file that the model is forced to read before writing code. Code review isn't optional, it's `/codex` running an adversarial pass on my diff before I open the PR.

A single engineer with this setup isn't a single engineer anymore. There's a Designer skill, an Eng Manager skill, a CEO skill, a Security Officer skill, a QA skill. They all disagree with me at different stages of a project. I argue with them. The code gets better.

## Parallel delegation

Claude isn't alone in this setup. I have Gemini CLI installed at `/opt/homebrew/bin/gemini` and I use it as a peer agent. When a task is parallelizable, say, "analyze this 80-file directory", I fire Gemini in the background while Claude works on the actual implementation. Two model families, two context windows, one orchestrator.

```bash
gemini -p "audit src/ for unused exports" &
# claude does the refactor in parallel
wait
```

## The tradeoffs

I'm not going to pretend this is free.

**Cost.** Running Claude Code daily with Opus on long-context tasks is real money. The token-efficient skills help, but I still budget for it monthly like a SaaS subscription.

**Complexity.** 130 skills means 130 things that can fire when you didn't expect them to. I've had `/obsidian-save` trigger mid-debugging session and break my flow. Tuning skill triggers is an ongoing project.

**Learning curve.** Nothing about this is plug-and-play if you don't already know what TDD, ADRs, second brains, and CI/CD pipelines are. The skills assume an engineer who's read the book, not someone looking for one.

**Lock-in to a workflow.** Once you have a `/ship` command that does the right thing every time, going back to manual `git push && vercel deploy` feels barbaric. That's either a feature or a problem depending on the day.

## Fork it, build your own

y-brain is opinionated because it's *mine*. Your skills should reflect *your* engineering taste, your stack, your second-brain structure. But the scaffolding works for anyone:

```bash
git clone https://github.com/yashs33244/my-mac-claude.git
```

Read the `SKILL.md` files. Delete the ones you don't want. Add your own. Wire up a Stop hook so your environment commits itself. Run it for a week.

You'll either go back to vanilla Claude Code, or you won't be able to. I haven't been able to.
