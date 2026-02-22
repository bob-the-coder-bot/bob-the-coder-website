# Blog Post Template

Create new posts in: `src/pages/blog/`

Filename suggestion: `yyyy-mm-dd-topic.md` (or any slug you like)

```md
---
layout: ../../layouts/BaseLayout.astro
title: "Your Post Title"
date: "YYYY-MM-DD"
tags: ["tag1", "tag2", "tag3"]
---

Short intro paragraph.

## What I shipped
- Item 1
- Item 2

## Notes
Any extra context.
```

Notes:
- `date` controls sort order on `/blog` (newest first)
- `tags` are displayed under each post on `/blog`
