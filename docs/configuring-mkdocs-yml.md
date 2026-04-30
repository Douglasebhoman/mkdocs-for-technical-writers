# Configuring mkdocs.yml

This page is part of a complete guide to building and deploying documentation sites with MkDocs. If you have not yet created your project, start at [Creating a Project](creating-a-project.md).

When you ran `mkdocs new`, MkDocs created a `mkdocs.yml` with one line in it. That line is `site_name: My Docs`. This page explains what to add to it and why, from the minimum needed to get a site running to the optional settings that make a real difference for technical writing projects.

---

## Minimum configuration

The only required field is `site_name`. With just this one line, MkDocs can build and serve your site:

```yaml
site_name: My Documentation
```

Run `mkdocs serve` after saving and open `http://127.0.0.1:8000` in your browser.

> **What you should see:** A basic site with your site name in the header, a single Home page pulled from `docs/index.md`, and a default navigation sidebar. This is functional but unstyled. The Material theme, navigation structure, and other settings come next.

---

## Site name, URL, and author

These fields identify your site and are used by MkDocs when building links, metadata, and the site header.

```yaml
site_name: My Documentation
site_url: https://yourusername.github.io/your-repo/
site_author: Your Name
site_description: A short description of what this documentation covers.
```

**What each field does:**

- `site_name`: the name displayed in the browser tab and the site header.
- `site_url`: the base URL of your live site. This is important for GitHub Pages because MkDocs uses it to generate correct internal links and asset paths.
- `site_author`: metadata that credits the documentation author. Used by search engines and some themes.
- `site_description`: a short summary used in search engine results and social media previews.

---

## Material theme

To enable the Material theme, add a `theme` block to your `mkdocs.yml`:

```yaml
theme:
  name: material
  palette:
    scheme: default
    primary: indigo
    accent: blue
```

**What each setting does:**

- `name: material`: activates the Material theme.
- `palette`: controls the colour scheme. `scheme` can be `default` (light) or `slate` (dark).
- `primary` and `accent`: set the primary and accent colours. Material supports a full range of named colours. See the [Material theme colour documentation](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/) for the complete list.

> **Note:** YAML is whitespace-sensitive. Indentation must be consistent and use spaces, never tabs. A single misplaced space can cause MkDocs to throw a configuration error. If you copy examples from this guide, paste them carefully and check the indentation before saving.

---

## Navigation

The `nav` block defines the structure and order of your documentation. Without it, MkDocs generates navigation automatically from your file structure. Defining it explicitly gives you full control.

```yaml
nav:
  - Home: index.md
  - Getting Started: getting-started.md
  - API Reference: api.md
  - About: about.md
```

To create nested sections, use indentation:

```yaml
nav:
  - Home: index.md
  - Guides:
      - Installation: guides/installation.md
      - Configuration: guides/configuration.md
  - API Reference: api.md
```

> **Note:** Every file listed in `nav` must exist in your `docs/` folder. MkDocs will throw a warning during build if a listed file is missing.

---

## Useful optional settings

These settings are not required but make a meaningful difference for technical writing projects.

**Repository link**
Adds a link to your GitHub repository in the site header. Useful for open-source documentation:

```yaml
repo_name: yourusername/your-repo
repo_url: https://github.com/yourusername/your-repo
```

**Copyright notice**
Adds a copyright statement to the site footer:

```yaml
copyright: '© 2026 Your Name'
```

**Custom CSS**
Lets you override the theme's default styles with your own brand colours and typography:

```yaml
extra_css:
  - stylesheets/brand.css
```

**Markdown extensions**
Enables additional Markdown features beyond the standard syntax:

```yaml
markdown_extensions:
  - admonition
  - pymdownx.details
  - pymdownx.superfences
  - pymdownx.highlight:
      anchor_linenums: true
```

What each extension gives you:

- `admonition`: enables Note, Warning, Tip, and other callout boxes in your Markdown.
- `pymdownx.details`: makes admonitions collapsible so readers can expand and hide content.
- `pymdownx.superfences`: enables code blocks inside admonitions and tabbed sections.
- `pymdownx.highlight`: adds syntax highlighting to code blocks with line number anchors.

---

## Complete example

The only required field is `site_name`. Every other field in this example is optional. Replace every placeholder value with your own details and remove any section you do not need.

```yaml
site_name: My Documentation
site_url: https://yourusername.github.io/your-repo/
site_author: Your Name
site_description: A practical guide to building documentation with MkDocs.

repo_name: yourusername/your-repo
repo_url: https://github.com/yourusername/your-repo

theme:
  name: material
  palette:
    scheme: default
    primary: indigo
    accent: blue

nav:
  - Home: index.md
  - Getting Started: getting-started.md
  - API Reference: api.md
  - About: about.md

copyright: '© 2026 Your Name'

extra_css:
  - stylesheets/brand.css

markdown_extensions:
  - admonition
  - pymdownx.details
  - pymdownx.superfences
  - pymdownx.highlight:
      anchor_linenums: true
```

---

Once your `mkdocs.yml` is configured, move to [Writing Content](writing-content.md).