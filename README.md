# 📚 Discloud Docs

<div align="center">
  <img src="https://i.imgur.com/za9JTHz.png" alt="Discloud Logo" width="150">
</div>

<p align="center">
  <a href="https://github.com/discloud/docs">
    <img src="https://img.shields.io/badge/GitHub-Repository-blue?style=flat-square&amp;logo=github" alt="GitHub">
  </a>
  <a href="https://docs.discloud.com/en">
    <img src="https://img.shields.io/badge/Documentation-Discloud-blue?style=flat-square&amp;logo=read-the-docs" alt="Documentation">
  </a>
</p>

## 🚀 Introduction

This repository holds the official **Discloud** documentation.

### 📚 Languages

- 🇧🇷 **Português** – [Leia a versão traduzida](README.pt.md)

## 🗂️ Documentation branches

The documentation is divided into 2 branches so that each language maintains its own complete tree:

- `portuguese` – contains the complete Portuguese documentation tree (`https://docs.discloud.com`).
- `english` – contains the complete English documentation tree (`https://docs.discloud.com/en`).

## 📘 Slug & Routing Guidelines

Routes (slugs/permalinks) must remain in English and mirror the English documentation to keep relative links, bookmarks, and automation stable across languages. The slug is the path portion after the domain (e.g., `/getting-started/install`).

### 📝 Managing slugs in Markdown

Because most contributors work directly in Markdown, the slug is driven by how you organize `SUMMARY.md`:

1. Create a section title that represents the group or landing page name.
2. If you need an anchor link on that section, append an explicit HTML anchor to match the slug you intend to publish.
3. List each Markdown file in English; the entry’s melody determines the published route.

Example snippet from `SUMMARY.md`:

```markdown
## How to Host Using <a href="#how-to-host-using" id="how-to-host-using"></a>

- [Control Panel](how-to-host-using/dashboard.md)
```

The link above resolves to `https://docs.discloud.com/how-to-host-using/dashboard`, so the Markdown file’s location, its English name, and the optional anchor must stay synchronized with the English slug.

### 🧭 Best practices for slugs

- Keep every slug in English and never include diacritics, spaces, or trailing slashes.
- Use kebab-case (`how-to-host-using`) for readability and URL hygiene.
- Do not translate or vary slugs between languages, only the page content changes.
- Evaluate SEO and existing links before renaming a route.

---

<p align="center">Made with ❤️ by the Discloud Team</p>
