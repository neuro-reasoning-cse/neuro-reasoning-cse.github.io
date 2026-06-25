# Neuro-Reasoning Lab Website

The website for the Neuro-Reasoning Lab at CSE, UNSW, built with [Hugo](https://gohugo.io/) using the [FixIt](https://github.com/hugo-fixit/FixIt) theme.

## Local Development

We use GitHub Codespaces to update the website content.

**Step 1:**

In the top-right corner of the repository, click the green **"<> Code"** button and create a Codespace (an online VS Code editor).

**Step 2:**

```bash
# Pull the theme files (required every time you open a new Codespace)
git submodule update --init --recursive
```

**Step 3:**

```bash
# Start the development server
hugo server
```

A local preview of the website will then open in your browser.

After making changes, push them to the GitHub repo (the same way you normally use Git), and the live website will update automatically.

**Note:** Every time you create a new Codespace, you must repeat **Step 2** to pull the FixIt theme.


## Quickstart

Below are descriptions of some key files. The others follow the same logic.

**Layouts**

There are three main templates under `/layouts/`: `home.html`, `list.html`, and `single.html`.

- `home.html` controls the main page: [https://neuro-reasoning-cse.github.io/](https://neuro-reasoning-cse.github.io/)

- `list.html` controls a parent (listing) page. For example, `layouts/members/faculty/list.html` controls the layout of [https://neuro-reasoning-cse.github.io/members/faculty/](https://neuro-reasoning-cse.github.io/members/faculty/).

- `single.html` controls a child (individual) page. For example, `layouts/members/single.html` controls the layout of every personal page, such as [https://neuro-reasoning-cse.github.io/members/faculty/ruoyu/](https://neuro-reasoning-cse.github.io/members/faculty/ruoyu/). Because there is no dedicated layout for students or faculty, those pages fall back to the closest available layout.

**Content**

- **Members** (`/content/members/`): Add a `yourname.md` file to the relevant folder to add a person to the page. Templates are located in `/templates/`. Use `student-alumni_template.md` for students and alumni. Use `faculty_template.md` for faculty members.

- **News** (`/content/news/`): Edit `/content/news/_index.md` to add news. Each entry should follow the structure below, listed under the `news` parameter:

```yaml
  - date:    "01/2000"
    content: "Happy new year."
```

- **Projects** (`/content/projects/`): Edit `/content/projects/_index.md` to add projects. Each entry should follow the structure below, listed under the `news` parameter:

```yaml
  - title: "Project B"
    items:
      - "project 1"
      - "project 2"
  - title: "Project A"
    items:
      - "project 1"
      - "project 2"
```

- **Research** (`/content/research/`): To add a research theme block, create a new folder under `/content/research/`. Then add an `_index.md` inside this theme folder, using `research-theme_template.md` as the template.

  To add a subarea, create a new folder under `/content/research/<theme>/`. Then add an `index.md` inside the subarea folder, using `research-subarea_template.md` as the template.

  So the final structure looks like `/content/research/<theme>/<subarea1>/`.

  For the cover image of each subarea, I use free icons from https://www.flaticon.com/ and draw.io for editing.


**Static**

- **Static files** (`/static/`): This folder stores all images, please put all images in here. To use one in your content, reference it by its path relative to `/static/`. For example, an image at `/static/images/front-image.png` is referenced as `images/front-image.png`.

## Overview

Hugo lets us manage the website easily. We only need to focus on three folders (`/content`, `/layouts`, and `/static`) and one file (`hugo.toml`).

Hugo uses HTML template files (in `/layouts`) to build the front-end pages, and automatically fills in the content (from `/content`) at the corresponding placeholders. Content is written as structured Markdown files, so there is no need to learn a new programming language.

**`/layouts` and `/content` both use a tree structure to organise pages, so their folder structures mirror each other.** Each node (page) has a corresponding layout (`xxx.html`) and content file (`xxx.md`). If a page has no layout of its own, Hugo searches upward and uses the closest available layout.

`/static` stores all the image assets used across the website, such as photos, icons, and avatars. These files are served as-is, and you reference them by their path relative to `/static/` (for example, an image at `/static/images/front-image.png` is written as `images/front-image.png`).

In practice, we usually only edit `/content` to update the website, since most layouts are already finished and will automatically adapt to newly added content.

`hugo.toml` controls the more general, site-wide settings.

<!-- such as the menu, the site title, and the site icon -->


## End

The live site is available at: https://neuro-reasoning-cse.github.io/