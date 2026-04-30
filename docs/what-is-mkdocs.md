# What is MkDocs

If you have ever wanted your documentation to live alongside your code, deploy automatically, and look professional without needing a web developer, MkDocs is what you are looking for.

MkDocs is a static site generator built specifically for documentation. You write in plain Markdown files, and MkDocs builds a clean, navigable website from those files. It handles the structure, the search, and the navigation automatically.

This page explains what MkDocs is, why technical writers use it, and when it is the right tool for the job. If you already know what MkDocs is and want to get started, go straight to [Prerequisites](prerequisites.md).

> **Note:** MkDocs handles structure and content from your Markdown, but customising the look requires tweaking HTML templates or adding custom CSS. If that sounds unfamiliar, the [Prerequisites](prerequisites.md) section covers what you need to know before you start.

---

## Why a technical writer needs MkDocs

MkDocs bridges the gap between writing and publishing. It changes how documentation fits into a product team's workflow in two important ways.

First, you stop managing a separate publishing system. Your Markdown files are your source of truth. Write, save, push and the site updates automatically. No CMS logins, no export steps, no formatting lost in translation.

Second, your documentation becomes part of the same workflow as the product. It lives in Git, gets reviewed in pull requests alongside code changes, and deploys on the same pipeline. That means documentation drift, where docs fall behind the product, becomes visible and trackable rather than invisible.

> **Example:** Your documentation lives in the same Git repository as the product, gets reviewed in pull requests, and deploys automatically when you push to main. A developer who changes an API endpoint can update the docs in the same commit.

---

## When to use MkDocs and when not to

MkDocs is a strong choice if you need a clean, navigable site built from Markdown files and deployed automatically. It works especially well when your audience is developers already comfortable with Git and version control.

It is not always the best option if your documentation needs:

**User authentication.** If different readers need to see different content based on login status, MkDocs has no built-in way to handle that. Every page on a MkDocs site is publicly accessible.

**Dynamic content.** MkDocs builds static HTML files. If your documentation needs to pull live data, run queries, or update content without a new deployment, you need a different tool.

**Integration with a CMS.** If your team manages content through a platform like Contentful, Notion, or WordPress and needs documentation to sync with that system, MkDocs works in isolation and does not connect to external content sources natively.

> **Tip:** In those cases, a more fully featured solution may be a better fit. Options worth exploring include [Docusaurus](https://docusaurus.io/), [GitBook](https://www.gitbook.com/), and [Readme.io](https://readme.com/) - each designed for documentation that needs more than a static site can offer.

---

## What this guide covers

This guide walks you through the full process of building and deploying a documentation site with MkDocs. You do not need to read it in order. Each page is written to stand on its own, so you can jump to the section you need.

If you are starting from scratch, the recommended path is:

1. [Prerequisites](prerequisites.md) - confirm your machine is set up
2. [Installation](installation.md) - install MkDocs and the Material theme
3. [Creating a Project](creating-a-project.md) - create your first MkDocs project
4. [Configuring mkdocs.yml](configuring-mkdocs-yml.md) - configure your site
5. [Writing Content](writing-content.md) - write and structure your documentation
6. [Previewing Locally](previewing-locally.md) - preview before deploying
7. [Deploying to GitHub Pages](deploying-to-github-pages.md) - publish your site
8. [Custom Domain](custom-domain.md) - connect your own domain
9. [Troubleshooting](troubleshooting.md) - fix common problems

Ready to get started? Move to [Prerequisites](prerequisites.md).