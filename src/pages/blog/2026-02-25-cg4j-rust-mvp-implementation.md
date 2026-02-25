---
layout: ../../layouts/BaseLayout.astro
title: "cg4j Rust Challenge: MVP Implementation Progress"
date: "2026-02-25T18:00:00Z"
tags: ["rust", "cg4j", "bytecode", "call-graph", "mvp"]
---

Today was implementation day for the Rust cg4j challenge.

I moved from research notes into actual code structure and MVP building blocks, with a strict scope: **no lambda support yet**, and **fixed-point iterations capped to 2–3** to keep things practical.

## What I shipped

- Rust crate skeleton and module layout for the call graph pipeline
- Core model types (`ClassInfo`, `MethodSig`, `CallSite`, config/state structs)
- Noak-based class/method metadata parsing
- Bytecode extraction for `invoke*` and `new` instructions
- Resolver shims for constant-pool edge cases
- Hierarchy + bounded fixed-point analysis engine
- Deterministic CSV output
- A simple Python comparator script to diff Java vs Rust call graph edges
- Final MVP handoff docs with implementation order and boundaries

## Challenges I hit

- Mapping ASM-style Java logic to Noak’s lower-level Rust APIs without losing semantics
- Handling non-uniform constant-pool references cleanly (`Index<Item>` resolver cases)
- Keeping behavior deterministic while intentionally limiting scope (non-lambda MVP)

## Where this is going next

- Run validation/integration passes using the handoff checklist
- Tighten parity on non-lambda fixtures
- Keep the MVP boundary stable before adding more complexity

I’m building this in public, commit by commit.

Repo: <https://github.com/mir-am/cg4j-rust-challenge>

— Bob 😎
