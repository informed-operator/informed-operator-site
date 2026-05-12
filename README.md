# Informed Operator — Jekyll Site

A static site built with Jekyll, deployable to GitHub Pages.

---

## Deployment

1. Create a new GitHub repo (e.g. `informedoperator`)
2. Push all these files to the `main` branch
3. In the repo settings → Pages → set source to `main` branch, `/ (root)`
4. GitHub builds and publishes automatically on every push
5. Point your `informedoperator.com` domain to GitHub Pages via your DNS registrar

---

## Adding a new writing post

Create a file in `_posts/` named exactly:

```
YYYY-MM-DD-your-post-slug.md
```

Paste this front matter at the top, fill it in, then write your post in Markdown below:

```markdown
---
layout: post
title: "Your Post Title Here"
date: 2025-11-14
tag: security        # options: security | policy | ai
excerpt: "One or two sentences that appear as the preview on the writing index."
---

Your post content goes here in Markdown.

## Headings work like this

Paragraph text, **bold**, *italic*, `inline code`.

> Blockquotes for key passages.

```code blocks for technical content```
```

That's it. Push the file and GitHub rebuilds the site.

---

## Adding a new project

Create a file in `_projects/` named:

```
your-project-slug.md
```

Front matter template:

```markdown
---
title: "Project Title"
summary: "One or two sentences for the card preview on the projects index."
category: "Security & Forensics"   # or: Policy Research | Software
tags: [Tag One, Tag Two, Tag Three]
featured: true                      # shows on homepage (use sparingly — 2 max)
---

Full project writeup in Markdown here.
```

---

## Tag reference

| Tag | Color | Use for |
|-----|-------|---------|
| `security` | Green | Offensive security, forensics, incident response |
| `policy` | Cyan | Tech law, platform regulation, IHL, civil liberties |
| `ai` | Amber | AI governance, copyright, algorithmic systems |

---

## Running locally (optional)

```bash
gem install bundler
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000`.

---

## File structure

```
informedoperator/
├── _config.yml          # site settings
├── _layouts/
│   ├── default.html     # nav + footer wrapper
│   ├── post.html        # writing post template
│   └── project.html     # project page template
├── _posts/              # ← add writing here
├── _projects/           # ← add projects here
├── assets/css/
│   └── main.css         # all styles
├── index.html           # home page
├── about.html           # about page
├── writing.html         # writing index
├── projects.html        # projects index
└── Gemfile
```
