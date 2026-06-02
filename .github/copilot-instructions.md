# Azure Frontier Labs — Website Copilot Instructions

## Project Overview

This repository is the public website for **Azure Frontier Labs**, hosted at [azurefrontierlabs.github.io](https://azurefrontierlabs.github.io) and serving as the workshops catalog for [azurefrontierlabs.com](https://azurefrontierlabs.com).

**Azure Frontier Labs** is a cloud automation platform that manages the full lifecycle of isolated lab environments on Azure — from creation to teardown. It is a place where developers can safely experiment with Azure and Microsoft services through guided, step-by-step hands-on workshops.

The platform provisions various types of labs on demand:

| Lab | Technology Stack |
|-----|-----------------|
| **AI Lab** | Microsoft Foundry + Azure AI Search |
| **Analytics Lab** | Microsoft Fabric |
| **Big Data Lab** | Azure Databricks |

Each lab is dynamically spun up with pre-configured services tailored to its scenario, giving individuals and teams reproducible cloud workspaces for guided learning.

## Tech Stack

- **Static site generator**: [Jekyll](https://jekyllrb.com/)
- **Theme**: [jekyll-theme-chirpy](https://chirpy.cotes.page/) — a minimal, responsive, feature-rich Jekyll theme for technical writing
- **Hosting**: GitHub Pages (`azurefrontierlabs.github.io`)

## Repository Structure

| Path | Purpose |
|------|---------|
| `_posts/` | Workshop and blog post content (Markdown) |
| `_tabs/` | Top-level navigation pages (About, Archives, Categories, Tags) |
| `_data/` | Site data files (contact info, share config) |
| `_plugins/` | Custom Jekyll plugins |
| `assets/` | Static assets (JS, CSS, images) |
| `_config.yml` | Jekyll + Chirpy theme configuration |
| `tools/` | Development scripts (`run.sh` for local server, `test.sh` for production build) |

## Conventions

- All workshop posts live in `_posts/` and follow Jekyll naming convention: `YYYY-MM-DD-title.md`
- Posts use Chirpy front matter fields: `title`, `date`, `categories`, `tags`, `description`, `image`
- Run the local dev server with `./tools/run.sh` (Jekyll with live reload)
- Build for production with `./tools/test.sh`
- The theme documentation is at <https://chirpy.cotes.page/>
