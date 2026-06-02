# Azure Frontier Labs — Website

The public workshops catalog for **Azure Frontier Labs**, hosted at [azurefrontierlabs.github.io](https://azurefrontierlabs.github.io).

Built with [Jekyll](https://jekyllrb.com/) and the [Chirpy](https://chirpy.cotes.page/) theme, deployed via GitHub Pages.

---

## Running Locally

1. Install dependencies:

   ```shell
   bundle install
   ```

2. Start the development server with live reload:

   ```shell
   ./tools/run.sh
   ```

   The site will be available at `http://127.0.0.1:4000`.

3. Build for production:

   ```shell
   ./tools/test.sh
   ```

---

## Repository Structure

```
_posts/               # Catalog posts — one per workshop (homepage cards)
_workshops/           # Workshop step content
  {lab-slug}/
    01-{step}.md
    02-{step}.md
    ...
assets/
  img/
    workshops/        # Workshop cover images ({lab-slug}.png)
_tabs/                # Top-level navigation pages (About, Archives, etc.)
_data/                # Site data (contact, share config)
_config.yml           # Jekyll + Chirpy configuration
tools/
  run.sh              # Local dev server
  test.sh             # Production build
```

---

## Creating a New Workshop

Every workshop has two parts:

- A **catalog post** in `_posts/` — the discoverable landing page shown on the homepage.
- One or more **step files** in `_workshops/` — the actual hands-on content.

### Step 1 — Create the Catalog Post

Create `_posts/YYYY-MM-DD-{lab-slug}.md`. This post is indexed by search and displayed as a card on the homepage.

**Required front matter:**

```yaml
---
title: "Lab Name"
date: YYYY-MM-DD 00:00:00 +0000
categories: [Workshops]
tags: [Tag1, Tag2, Tag3]
description: One or two sentence summary shown on the homepage card.
image:
  path: /assets/img/workshops/{lab-slug}.png
  alt: Lab Name Workshop
---
```

**Required body:**

```markdown
## About This Lab

Brief description of what the lab is about.

## What You'll Learn

- Key learning objective 1
- Key learning objective 2

## Workshop Steps

1. [Part 1 — Title](/workshops/{lab-slug}/01-{slug}/)
2. [Part 2 — Title](/workshops/{lab-slug}/02-{slug}/)
```

### Step 2 — Add Workshop Step Files

Create `_workshops/{lab-slug}/NN-{step-slug}.md` for each step (`NN` = zero-padded number).

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

No `layout`, `date`, `categories`, or `tags` needed — these are inherited from `_config.yml` defaults.

### Step 3 — Add the Workshop Cover Image

Add `assets/img/workshops/{lab-slug}.png`. Recommended size: **1200×630 px**.

### Step 4 — Add Screenshots and Step Images

Screenshots and images used inside step files live in a **per-lab subfolder**:

```
assets/img/workshops/{lab-slug}/
```

**Format:** PNG (`.png`) for all screenshots and UI captures.

**Naming convention:** `NN-{descriptive-kebab-case}.png` — prefix with the zero-padded step number so images sort alongside their step.

Examples:

```
assets/img/workshops/ai-lab/01-portal-overview.png
assets/img/workshops/ai-lab/02-create-search-service.png
assets/img/workshops/ai-lab/02-index-schema.png
assets/img/workshops/ai-lab/03-rag-query-result.png
```

To embed an image in a step file:

```markdown
![Portal overview](/assets/img/workshops/ai-lab/01-portal-overview.png)
```

---

### Naming Conventions

| Item             | Pattern                                         | Example                                           |
| ---------------- | ----------------------------------------------- | ------------------------------------------------- |
| Catalog post     | `_posts/YYYY-MM-DD-{lab-slug}.md`               | `_posts/2026-05-18-ai-lab.md`                     |
| Step files       | `_workshops/{lab-slug}/NN-{step-slug}.md`       | `_workshops/ai-lab/01-introduction.md`            |
| Cover image      | `assets/img/workshops/{lab-slug}.png`           | `assets/img/workshops/ai-lab.png`                 |
| Step screenshots | `assets/img/workshops/{lab-slug}/NN-{desc}.png` | `assets/img/workshops/ai-lab/02-create-index.png` |
| Step URL         | `/workshops/{lab-slug}/NN-{step-slug}/`         | `/workshops/ai-lab/01-introduction/`              |

### Example Folder Structure

```
_posts/
  2026-05-18-my-new-lab.md              ← catalog post

_workshops/
  my-new-lab/
    01-introduction.md
    02-setup.md
    03-build-something.md

assets/
  img/
    workshops/
      my-new-lab.png                    ← 1200×630 px cover image
      my-new-lab/                       ← step screenshots
        01-overview.png
        02-create-resource.png
        02-resource-settings.png
        03-final-result.png
```

---

## License

This work is published under [MIT][mit] License.

[mit]: https://github.com/cotes2020/chirpy-starter/blob/master/LICENSE
