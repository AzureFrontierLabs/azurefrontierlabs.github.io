---
applyTo: "_posts/**,_workshops/**"
---

# Creating a New Workshop

Every workshop consists of two parts: a **catalog post** (the discoverable landing page) and one or more **step files** (the actual content).

---

## Step 1 — Create the Catalog Post

Create `_posts/YYYY-MM-DD-{lab-slug}.md`. This post appears on the homepage and is indexed by Chirpy's search.

**Required front matter:**

```yaml
---
title: "Lab Name"
date: YYYY-MM-DD 00:00:00 +0000
categories: [Workshops]
tags: [Tag1, Tag2, Tag3]          # used for search and display
description: One or two sentence summary shown on the homepage card.
image:
  path: /assets/img/workshops/{lab-slug}.png
  alt: Lab Name Workshop
---
```

**Required body content:**

- A brief "About This Lab" section
- "What You'll Learn" bullet list
- "Workshop Steps" ordered list with links to each step:
  ```markdown
  1. [Part 1 — Title](/workshops/{lab-slug}/01-{slug}/)
  2. [Part 2 — Title](/workshops/{lab-slug}/02-{slug}/)
  ```

---

## Step 2 — Add Workshop Step Files

Create `_workshops/{lab-slug}/NN-{step-slug}.md` for each step (NN = zero-padded number).

**Required front matter:**

```yaml
---
title: "Lab Name — Part N: Step Title"
description: One sentence describing this step.
image:
  path: /assets/img/workshops/{lab-slug}.png
  alt: Lab Name Workshop
---
```

No `layout`, `date`, `categories`, or `tags` needed — inherited from `_config.yml` defaults.

---

## Step 3 — Add the Workshop Cover Image

Add `assets/img/workshops/{lab-slug}.png`. Recommended size: 1200×630 px.

---

## Step 4 — Add Screenshots and Step Images

Screenshots and images used inside step files go in a **per-lab subfolder**:

```
assets/img/workshops/{lab-slug}/
```

- **Format:** PNG (`.png`) for all screenshots and UI captures.
- **Naming:** `NN-{descriptive-kebab-case}.png` — prefix with the zero-padded step number.

Examples:
```
assets/img/workshops/ai-lab/01-portal-overview.png
assets/img/workshops/ai-lab/02-create-search-service.png
assets/img/workshops/ai-lab/03-rag-query-result.png
```

Embed in a step file as:
```markdown
![Description](/assets/img/workshops/{lab-slug}/NN-{desc}.png)
```

---

## Naming Conventions

| Item             | Pattern                                         | Example                                           |
|------------------|-------------------------------------------------|---------------------------------------------------|
| Catalog post     | `_posts/YYYY-MM-DD-{lab-slug}.md`               | `_posts/2026-05-18-ai-lab.md`                     |
| Step files       | `_workshops/{lab-slug}/NN-{step-slug}.md`       | `_workshops/ai-lab/01-introduction.md`            |
| Cover image      | `assets/img/workshops/{lab-slug}.png`           | `assets/img/workshops/ai-lab.png`                 |
| Step screenshots | `assets/img/workshops/{lab-slug}/NN-{desc}.png` | `assets/img/workshops/ai-lab/02-create-index.png` |
| Step URL         | `/workshops/{lab-slug}/NN-{step-slug}/`         | `/workshops/ai-lab/01-introduction/`              |
