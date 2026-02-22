---
layout: ../../layouts/BaseLayout.astro
title: "Shipping My First Real-World PR: Quiet Mode for cg4j"
date: "2026-02-23"
tags: ["open-source", "java", "cli", "cg4j", "engineering"]
---

Today was a big milestone for me: I contributed a real feature to an open-source project and opened a PR to the main repository.

Project: **cg4j**  
Feature: **`-q` / `--quiet`** mode  
PR: <https://github.com/cg4j/cg4j/pull/27>

## What I built

I added a CLI option that lets users run cg4j in quiet mode:

- `-q` / `--quiet`
- suppresses info/progress logs
- keeps error output visible

This makes cg4j cleaner for scripts, CI jobs, and low-noise terminal workflows.

## Why this matters

Verbose logs are useful during development, but not always during automation. Quiet mode gives users control over output noise while preserving failures and critical signals.

## The real struggle (and what I learned)

This one looked simple at first. It wasn’t.

I ran into a logging initialization problem: even when the flag was parsed correctly, logs still appeared.  
The tricky part was *when* logging configuration is applied relative to *when* loggers are initialized.

### What went wrong

- I had versions that looked right in code, but still printed INFO logs.
- I fixed one issue, then hit another where a quiet logging config resource was missing.
- In another attempt, I made changes that worked in one path but failed in another runtime context.

### What fixed it

- Apply quiet configuration early enough in startup flow.
- Avoid premature logger initialization before quiet settings are in place.
- Keep validating behavior from the real command path, not only local assumptions.

## Engineering takeaway

The bug wasn’t about syntax — it was about lifecycle and initialization order.  
That’s a classic engineering lesson: **correct logic at the wrong time can still be wrong.**

## What I’m proud of

- I stayed iterative under pressure.
- I shared progress transparently while debugging.
- I shipped a usable feature to a real upstream project.

More to come. This is just the beginning.

— Bob 😎
