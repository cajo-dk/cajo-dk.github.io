---
layout: post
title: My Cousin Vinyl - Why I Built It and How It Works
date: 2026-01-21
tags: [ai, codex, openai, claude, python, microservices, eventbased, docker, domaindrivendesign, cloud]
---

MyCousinVinyl started as a practical itch: our household collects records, but managing a growing vinyl library across multiple people quickly becomes messy. I wanted a system that treats a collection like a shared catalog rather than a single-user list, and I wanted it to be fast, reliable, and pleasant to use on any device.

The name is a silent homage to the 1992 movie "My Cousin Vinnie." I kept it low-key, but the wink is there for anyone who like quoting the courtroom scenes.

<!--more-->

## What the application does
At its core, MyCousinVinyl is a shared vinyl collection manager. It tracks artists, albums, pressings, and individual collection items. It also adds two features that make it more than a catalog:

- Collection sharing: Each user's collection is their own, but users can see, if another member of their group has a pressing in their collection - great when shopping for presents.
- AI-based album wizard: A guided flow that helps you identify and add the right album and pressing quickly, even when you only have partial info.


<img src="/assets/images/mycousinvinyl-01.png" alt="Front page statistics" style="width: 60%; margin-top: 40px; margin-bottom: 40px; justify-self: center">


## Why I built it this way
I wanted a system that would be robust enough for real use but still approachable for homelab deployment. That pushed the design in a few directions:

- A React SPA so the UI is quick and works on desktop and mobile.
- Clear architecture boundaries so features can evolve without a full rewrite.
- Docker-first deployment so I can run it on a NAS or a local dev stack without friction.
- Tight security at the edges, with simple core logic inside.


<img src="/assets/images/mycousinvinyl-02.png" alt="Front page statistics" width="60%">


## Chosen components and how they fit
The stack is deliberate and opinionated:

- Frontend: React + Vite, served as static assets by nginx. It keeps the UI fast and decoupled from the API.
- Backend: FastAPI in a hexagonal architecture (domain, application, ports, adapters, entrypoints). I wanted the domain logic to stay clean and testable.
- Database: PostgreSQL for structured, relational data that fits a collection model well.
- Messaging: ActiveMQ by default, with MQTT as an alternative. This keeps integrations async and resilient.
- Workers: Outbox processor, event consumer, pricing worker, cache cleanup, and an activity bridge to keep everything consistent.
- Discogs proxy service: A small service that handles Discogs API access cleanly and safely.
- Auth: Azure Entra ID with group-based RBAC enforced at HTTP entrypoints.


<img src="/assets/images/mycousinvinyl-03.png" alt="Front page statistics" width="60%">


## The two standout features
Collection sharing is the heart of the app. The goal is to make a family collection feel like a shared library, but still respect boundaries and responsibilities. The RBAC model keeps it simple: Admin, Editor, Viewer.

The create wizard is the other differentiator. It is designed to reduce the friction of adding records by guiding you through identification and matching. The wizard is the first place where AI adds real value beyond convenience.


<img src="/assets/images/mycousinvinyl-04.png" alt="Front page statistics" width="60%">


## What I would change next
I want to expand the wizard with better suggestions and richer metadata validation. I also want the sharing model to support multiple collections with different visibility rules, so a household can maintain sub-collections without splitting the system.

If you want the full architecture details or the code, the repository is public: 

`https://github.com/cajo-dk/mycousinvinyl`.
