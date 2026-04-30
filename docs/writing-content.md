# Writing Content

MkDocs uses Markdown as its content format. This page covers everything you need to write, structure, and enrich your documentation — from creating a new page to adding images, code blocks, and callout boxes.

---

## Creating a new page

Every page in your MkDocs site is a Markdown file inside the `docs/` folder. To create a new page:

**Step 1 — Create the Markdown file**

Create a new file inside your `docs/` folder. On Windows:

```
docs/getting-started.md
```

You can create it directly in VS Code by right-clicking the `docs/` folder in the file explorer and selecting **New File**.

**Step 2 — Add content to the file**

Open the file and add your content in Markdown:

```markdown
# Getting Started

This page explains how to set up the project.
```

**Step 3 — Register the page in mkdocs.yml**

MkDocs does not automatically show pages in navigation — you must define them explicitly in the `nav` block:

```yaml
nav:
  - Home: index.md
  - Getting Started: getting-started.md
```

**Step 4 — Preview the page**

Run `mkdocs serve` and open `http://127.0.0.1:8000` in your browser. Your new page will appear in the navigation.

> **Note:** MkDocs follows an explicit navigation model — a file must exist in `docs/` AND be listed in `nav` before it appears in the site. This gives you full control over structure and prevents unfinished pages from appearing in navigation accidentally.

---

## Markdown syntax

MkDocs supports standard Markdown through Python Markdown, along with optional extensions that add advanced features.

**Core Markdown — supported out of the box:**

```markdown
# Heading 1
## Heading 2

**Bold**
*Italic*

- Bullet list item
- Another item

1. Numbered list
2. Second item

[Link text](https://example.com)

![Image alt text](assets/image.png)

`inline code`
```

**Extended Markdown — enabled via extensions:**

With the right extensions configured in `mkdocs.yml`, you also get:

- Tables
- Footnotes
- Admonitions (Note, Warning, Tip boxes)
- Syntax-highlighted code blocks
- Tabbed content sections

Extensions are covered in the sections below and in the [Configuring mkdocs.yml](configuring-mkdocs-yml.md) page.

---

## Admonitions

Admonitions are callout boxes — Note, Warning, Tip, and others — that draw the reader's attention to important information.

**Step 1 — Enable the extension in mkdocs.yml:**

```yaml
markdown_extensions:
  - admonition
  - pymdownx.details
```

> **Note:** If you skip this step, the admonition syntax will render as plain text instead of a styled box.

**Step 2 — Use the admonition syntax in your Markdown:**

The basic format is:

```markdown
!!! type "Optional Title"
    Content goes here. Must be indented with four spaces.
```

**Common admonition types:**

Note:

```markdown
!!! note
    This is a general note for the reader.
```

Warning:

```markdown
!!! warning
    This action cannot be undone.
```

Tip:

```markdown
!!! tip
    You can speed this up by using a keyboard shortcut.
```

With a custom title:

```markdown
!!! warning "Be Careful"
    This step will permanently delete your data.
```

> **Important:** Content inside an admonition must be indented with exactly four spaces. Without the indentation, the content will not render inside the box.

---

## Code blocks with syntax highlighting

MkDocs supports fenced code blocks with language-specific syntax highlighting.

**Basic syntax:**

Open a code block with three backticks followed by the language name:

````markdown
```python
def greet():
    print("Hello, world!")
```
````

MkDocs applies syntax highlighting automatically based on the language you specify. Common language identifiers include `python`, `javascript`, `bash`, `yaml`, `html`, and `markdown`.

**Enable syntax highlighting in mkdocs.yml:**

```yaml
markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.superfences
```

**With line numbers:**

````markdown
```python linenums="1"
def add(a, b):
    return a + b
```
````

**With tabbed language examples (Material theme feature):**

````markdown
=== "Python"
    ```python
    print("Hello")
    ```

=== "JavaScript"
    ```javascript
    console.log("Hello")
    ```
````

---

## Images

To add an image to a page, place the file inside your `docs/` folder and reference it using standard Markdown image syntax.

**Step 1 — Place the image inside docs/:**

```
docs/
└── assets/
    └── diagram.png
```

Keeping images in an `assets/` subfolder inside `docs/` is a common convention that keeps your content organised.

**Step 2 — Reference the image in your Markdown:**

```markdown
![Architecture diagram](assets/diagram.png)
```

- The text in square brackets is the alt text — a description used by screen readers and displayed if the image fails to load. Always write descriptive alt text.
- The path in parentheses is relative to the current Markdown file.

**Step 3 — Preview the image:**

Run `mkdocs serve` and open your local site to confirm the image renders correctly.

**Resizing images:**

Standard Markdown does not support image resizing. Use an HTML `img` tag instead:

```html
<img src="assets/diagram.png" alt="Architecture diagram" width="600">
```

**Common mistakes:**

- **Wrong file path** — the image will not render. Check that the path is relative to the Markdown file, not the project root.
- **Image outside docs/** — MkDocs only includes files inside `docs/` in the build. Images stored elsewhere will not appear in the live site.
- **Case sensitivity** — file names are case-sensitive on Linux and macOS. `Diagram.png` and `diagram.png` are different files.

---

Once your content is written and previewing correctly, move to [Previewing Locally](previewing-locally.md).