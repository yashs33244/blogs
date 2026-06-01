---
title: "Notes from after Binocs"
date: "2026-05-28"
tags: ["binocs", "startup-life", "claude-code", "builder", "doxa"]
excerpt: "A year onsite at a Bangalore startup teaches you a few things. These are mine, and what I've been building since I left."
---

I spent the last year onsite in Bangalore at [Binocs](https://binocs.co). Joined as an intern, left at the end of May. This is a small post about what I learned and what I've been doing since.

## What the year taught me

Most of what I picked up at Binocs wasn't a piece of tech, it was a way of working.

The most useful thing was debugging maturity. Not "I read the stack trace", more the calm that comes from knowing a production system has a handful of plausible failure modes and the patience to walk through them instead of guessing. It came from a lot of late nights staring at logs that were trying to tell me something I wasn't ready to hear.

The second thing was shipping under ambiguity. A startup hands you a request that's half-formed, and you build the thing before anyone's sure what the thing is. You learn to make small, reversible decisions quickly. You learn that a working v1 you can show people is worth more than a perfect v2 you can describe.

And ownership. The bug is yours, the cost spike is yours, the deploy is yours, the user complaint is yours. There's no escalation. You are the escalation.

Some specific things I worked on, in case it's useful context: the 130-page AI investment-deck pipeline (got the per-deck cost down by about 99% by being deliberate about prompt design, caching and which model handled which sub-task), an LLM orchestration engine underneath that, a 24-hour admin and deal generator used by ~40 teammates, the Fibre CDD vertical launch, Stripe international payments, a SendGrid → SES migration, a QA regression agent, and a Cloudflare and domain migration. I don't think any of those are uniquely impressive on their own. What was useful was doing them all back-to-back. Reps compound.

## What I've been doing since

I gave myself zero days off because I had a few things I wanted to try. In the days after leaving I put up a handful of personal projects.

[chess.itsyash.space](https://chess.itsyash.space) is a real-time multiplayer chess board, mostly a Sunday project. [outreach.itsyash.space](https://outreach.itsyash.space) is an AI outreach tool that fits how I actually run cold email. [doxa.itsyash.space](https://doxa.itsyash.space) is a doctor's AI scribe for Indian clinics, and the one I care about most. [pilot.itsyash.space](https://pilot.itsyash.space) is a small set of AI agents for DevOps and SRE chores. [shots.itsyash.space](https://shots.itsyash.space) is a portfolio for the photography I shoot. [itsyash.space](https://itsyash.space) is this site. And [finalcv.co](https://finalcv.co) is a resume builder I'd been meaning to finish.

These are personal projects. None of them are finished. A couple are barely past v0.1. They exist, they're on domains, and I can hand someone a link.

## A personal tool that helped

The reason I could move at all was a small Claude Code setup I made for myself, mostly for my own projects. I call it my **y-brain**. It's just a folder of CLAUDE.md files, skills and hooks I've been collecting and tweaking for months. Public configs from people whose work I respect (Anthropic, Vercel, gstack, Matt Pocock), plus a layer of my own glue.

It hasn't made me 10x at anything. It just removes enough friction that I get to spend my time on the thing I actually wanted to build instead of on the plumbing around it.

## What I'm looking for next

I'm an AI engineer, mostly. Comfortable across fullstack and infra, with some design and photography on the side. I want to keep building things that ship.

Doxa is the project I'd most like to keep pushing on, Indian primary care has a real, painful, unsolved documentation problem and I think the loop we're prototyping has a shot. If that's a space you care about, or if you're hiring for serious AI work, I'd love to talk.

Find me on [Twitter/X](https://twitter.com/yashs33244) or [LinkedIn](https://linkedin.com/in/yash-singh-bb1a1a212).
