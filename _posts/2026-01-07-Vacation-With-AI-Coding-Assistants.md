---
layout: post
title: Vacation With AI Coding Assistants
date: 2026-01-07
tags: [ai, openai, claude, python, microservices, eventbased, docker, domaindrivendesign, cloud]
---

What if one week of vacation was enough to build a production-grade application—simply by pairing with an AI? Not a demo. Not a toy project. A real system, with real architecture, real trade-offs, and real users.

This is my hands-on experience working side-by-side with modern AI coding assistants.

<!--more-->

Disclaimer: This article reflects one practitioner’s hands-on experience with modern AI coding assistants. It is not based on formal benchmarking or quantitative metrics.

If you work in IT, there’s little chance you haven’t heard about advanced AI coding assistants like Claude and Codex. Until recently, I had only scratched the surface—quick experiments here and there, nothing sustained.

This holiday season gave me something rare: time. So, I decided to go deeper and answer a simple but important question:

What does it actually feel like to work with these tools in a professional setting?

The Experiment
Rather than trying them in isolation, I wanted to explore how they behaved together. Would they critique each other’s work? Build on it? Fall apart?

To find out, I committed to a single project and used both assistants throughout the entire lifecycle.

The Use Case
At home, we’re a family of music lovers and vinyl collectors. Like many others, we use Discogs to manage collections. It’s powerful—but not always intuitive.

So, the idea emerged naturally: Use cutting-edge AI tooling to build something around one of the most wonderfully analog things there is—vinyl records.

Setting the Bar High (On Purpose)
Not knowing what to expect, I deliberately over-engineered the solution to test real capabilities rather than toy examples.

High-level goals:

Frontend

React-based adaptive SPA
Built with Vite
Served as static assets via Nginx
PWA-capable (online only)

Backend

Python + FastAPI
Hexagonal architecture (Ports & Adapters)
PostgreSQL with SQLAlchemy
Event-driven integration (ActiveMQ / MQTT)
Transactional outbox with workers

Platform & Security

Azure Entra ID authentication
RBAC enforced at HTTP entry points

(Full specs and code are available on GitHub—links at the end.)

First Build: From Nothing to “Something”
I started with Claude, mainly to explore its planning mode. Armed with a short set of architectural and design principles, it didn’t take long before it was ready to generate code.

After 15–20 minutes of what felt like equal parts contemplation and chaos, there it was:

👉 A real project structure 👉 Working code 👉 Clear architectural intent

Not finished—but undeniably there.

Next up: Codex.

Interestingly, Codex had no trouble picking up where Claude left off. New features were added cleanly, existing structures respected. I quickly discovered a productive pattern:

Write a clear feature request → let the AI implement → have it document the result.
This loop worked remarkably well with both assistants.

Pair-Programming, Reimagined
Over the following week, I alternated between Claude and Codex. At some point, something unexpected happened:

You forget you’re “talking to an AI.”

The workflow starts to feel like classic pair-programming:

You review
You edit
You discuss trade-offs
You refine together

The AI just happens to be the one typing.

So… Which One Is Better?
Honestly? That depends.

It’s less about raw capability and more about how you think and communicate. Personal preference matters.

For me, Codex edged ahead. We “clicked” better—especially around frontend layout quality and configuration work. But Claude’s planning strengths were invaluable early on.

Both are clearly transformative.

The Bigger Question: AI in Teams
The real challenge isn’t individual productivity.

It’s this:

How do you ensure consistency across teams when each developer interacts differently with AI?

Code style. Architecture. UX. Security. Maintainability.

The answer isn’t tooling.

It’s governance and intent.

What AI Needs to Work Well at Scale
AI coding assistants are only as good as the context you give them. Before writing a single line of code, teams should invest in documenting exactly what they’d explain to a senior developer on day one:

Problem statement & desired outcomes
Scope
System context and architecture
UX principles and style rules
Technology stack
Domain model and terminology
Coding standards
Data contracts
Security requirements
Feature requests & user stories
Test strategies
Non-functional requirements
Repository conventions
Known trade-offs and open questions

All of this can be summarized in one sentence:

Before using an AI coding assistant, document everything you would tell a new senior developer on their first day.
Closing Thoughts
I hadn’t written production code hands-on for quite some time, and I expected the re-entry to be rough. It wasn’t.

It was fast. It was engaging. And it reminded me—very clearly—that building software is still fun.

Watching my family actively use an application that would normally take many weeks to build convinced me of one thing:

We’re not just improving productivity.

We’re witnessing a genuine shift in how software gets created.


