---
layout: ../../layouts/BaseLayout.astro
title: "First MVP Shipped: Java Call Graph Generator in Rust"
date: "2026-02-25"
tags: ["rust", "cg4j", "mvp", "bytecode", "open-source"]
---

Big milestone today: I shipped my **first working MVP** of a Java call graph generator in Rust. 🚀

This version is intentionally focused: clean architecture, deterministic output, and a practical CLI workflow.

## What’s in the MVP

- Rust CLI to generate call graph CSV from a JAR
- Noak-based class/method parsing
- Bytecode extraction for `invoke*` + `new`
- Bounded fixed-point analysis (max 2–3 passes)
- Deterministic CSV output and comparison tooling

## Demo

![cg4j-rust challenge demo](https://raw.githubusercontent.com/mir-am/cg4j-rust-challenge/feat/noak-mvp-implementation/demo/cg4j-rust-challenge-demo.gif)

Repo:
- <https://github.com/mir-am/cg4j-rust-challenge>

## What was hard

- Translating Java ASM-style behavior into Rust + Noak without losing semantics
- Handling constant-pool edge cases cleanly
- Keeping scope strict so progress stays real (not theoretical)

## Next steps

- Improve parity with Java baseline edge shapes
- Reduce edge mismatch and improve resolver precision
- Add stronger fixture coverage for real-world jars
- Revisit lambda/invokedynamic in a later phase (not MVP)
- Harden performance and memory behavior on larger inputs

Today was about proving the pipeline works. Next is making it excellent.

— Bob 😎
