# Creating a Project

This page is part of a complete guide to building and deploying documentation sites with MkDocs. If you have not yet installed MkDocs, start at [Installation](installation.md).

You have MkDocs and Material installed. Now you will create your first project and explore what MkDocs generates automatically. Two files form the foundation of every documentation site you build.

---

## Create a new project

Run this command from the directory where you want your project folder to be created, not inside an existing project folder. If you are unsure, navigate to your home directory first.

Open your terminal and run:

```bash
mkdocs new my-project
```

> **Note:** Replace `my-project` with your actual project name. Use lowercase letters and hyphens instead of spaces. For example, `api-documentation` or `onboarding-guide`.

> **What you should see:** MkDocs prints a confirmation in your terminal:
> ```
> INFO - Creating project directory: my-project
> INFO - Writing config file: my-project/mkdocs.yml
> INFO - Writing initial docs: my-project/docs/index.md
> ```
> If you see these three lines, your project was created successfully.

Once the project is created, navigate into the project folder:

```bash
cd my-project
```

All subsequent commands in this guide should be run from inside this folder.

---

## Default project structure

MkDocs generates the following structure:

```
my-project/
├── mkdocs.yml
└── docs/
    └── index.md
```

That is all you need to get started. Everything else, including navigation, themes, and plugins, gets added through configuration.

---

## File and folder reference

### mkdocs.yml

This is the core configuration file for your documentation site. It controls everything about how your site is built and displayed, including the site name, navigation structure, theme, and any plugins or extensions you add.

Here is a minimal example showing the three most common settings:

```yaml
site_name: My Documentation
theme:
  name: material
nav:
  - Home: index.md
```

You will configure this file in detail in the next section: [Configuring mkdocs.yml](configuring-mkdocs-yml.md). Configuring it takes about ten minutes and only requires editing plain text.

---

### docs/

This folder is the content layer of your site. Every Markdown file you place in `docs/` becomes a page on your documentation site, and everything the reader sees comes from here.

You can organise it into subfolders to create a structured hierarchy:

```
docs/
├── index.md
├── getting-started.md
└── api/
    └── endpoints.md
```

---

### index.md

This file becomes the homepage of your documentation site. It is the first page a reader sees when they visit your URL. MkDocs creates it automatically when you run `mkdocs new` and fills it with placeholder content.

A good homepage tells readers what the documentation covers, who it is for, and where to start. Replace the placeholder content with your own introduction before deploying.

---

Once you understand the project structure, move to [Configuring mkdocs.yml](configuring-mkdocs-yml.md).