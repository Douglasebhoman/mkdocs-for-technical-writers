# Troubleshooting

This page is part of a complete guide to building and deploying documentation sites with MkDocs. If you are working through the guide from the beginning, start at [What is MkDocs](what-is-mkdocs.md).

If something is not working, you are in the right place. Every error listed here has a clear fix. Work through the relevant entry from top to bottom. The most common problems appear first.

If your issue is not listed here, check the [MkDocs documentation](https://www.mkdocs.org/) or the [Material for MkDocs documentation](https://squidfunk.github.io/mkdocs-material/).

---

## MkDocs is not recognised as a command

**What you see:**
```
'mkdocs' is not recognized as an internal or external command
```

**What causes it:**
Python was not added to PATH during installation, or MkDocs was installed in a Python environment your terminal cannot access.

**How to fix it:**

On Windows, reinstall Python from [python.org](https://www.python.org/downloads/) and check the box that says **"Add Python to PATH"** during setup. Then reinstall MkDocs:

```bash
pip install mkdocs
pip install mkdocs-material
```

Close and reopen your terminal after reinstalling. Run `mkdocs --version` to confirm the fix worked.

On macOS and Linux, close and reopen your terminal after installation. If `mkdocs` is still not recognised, run the following to confirm MkDocs is installed:

```bash
python -m mkdocs --version
```

---

## pip is not recognised as a command

**What you see:**
```
'pip' is not recognized as an internal or external command
```

**What causes it:**
On macOS and Linux, the correct command is often `pip3` rather than `pip` when multiple Python versions are installed. On Windows, pip may not have been included during Python setup.

**How to fix it:**

On macOS and Linux, try running `pip3` instead of `pip` for all installation commands:

```bash
pip3 install mkdocs
pip3 install mkdocs-material
```

On Windows, if both `pip` and `pip3` fail, reinstall Python from [python.org](https://www.python.org/downloads/) and ensure pip is included during setup.

---

## mkdocs serve fails with a docs_dir error

**What you see:**
```
ERROR - Config value 'docs_dir': The "docs" directory does not exist.
```

**What causes it:**
You ran `mkdocs serve` from outside your project folder. MkDocs looks for the `docs/` directory relative to where the command is run. If you are in the wrong directory, MkDocs cannot find the docs folder.

**How to fix it:**
Navigate into your project folder first, then run the command:

```bash
cd path/to/your/project
mkdocs serve
```

Confirm you are in the right place by running `dir` (Windows) or `ls` (macOS/Linux) and checking that `mkdocs.yml` is visible in the output.

---

## Images not rendering on the live site

**What you see:**
Images display correctly in local preview but appear as broken links on the live site.

**What causes it:**
The image file is stored outside the `docs/` folder, or the file path in the Markdown is incorrect relative to the page referencing it.

**How to fix it:**

1. Confirm the image file is inside the `docs/` folder. For example, `docs/assets/diagram.png`. Files outside `docs/` are not included in the build.
2. Check the file path in your Markdown. The path must be relative to the current page:

```markdown
![Alt text](assets/diagram.png)
```

3. Check for case sensitivity. On Linux and macOS, `Diagram.png` and `diagram.png` are different files. The filename in your Markdown must match the actual filename exactly.
4. Redeploy after fixing:

```bash
mkdocs gh-deploy
```

---

## Site not updating after mkdocs gh-deploy

**What you see:**
You run `mkdocs gh-deploy` successfully but the live site still shows the old content.

**What causes it:**
Either your browser is showing a cached version of the old site, GitHub Pages is not configured to serve from `gh-pages`, or the deployment pushed to the wrong branch.

**How to fix it:**

Start with step 1. A hard refresh fixes most cases. If the content is still old after refreshing, work through the remaining steps.

1. Hard refresh your browser with `Ctrl + Shift + R` (Windows) or `Cmd + Shift + R` (macOS) to bypass the cache.
2. Confirm the `gh-pages` branch exists in your repository. Go to the Code tab and select branches from the dropdown.
3. Go to **Settings** then **Pages** and confirm the source is set to the `gh-pages` branch.
4. Check the **Actions** tab in your repository and look for the `pages-build-deployment` workflow. Confirm it completed successfully. If it shows a red failure icon, see the GitHub Actions section below.

---

## GitHub Actions workflow failure

**What you see:**
The `mkdocs gh-deploy` command completes successfully, but the live site does not update. The **Actions** tab in your repository shows a red failure icon next to the `pages-build-deployment` workflow.

**What causes it:**
GitHub Actions failed to build or publish the site. Common causes include incorrect workflow permissions, the `gh-pages` branch not being recognised as the Pages source, or a build error in the generated site files.

**How to fix it:**

1. Go to the **Actions** tab in your repository.
2. Click the failed workflow run to open it.
3. Expand the failed step to read the error message. This tells you exactly what went wrong.
4. Fix the specific error. Common fixes include:

**Permissions error:**
Go to **Settings** then **Actions** then **General** and under **Workflow permissions**, select **Read and write permissions**. Then redeploy:

```bash
mkdocs gh-deploy
```

**Pages source not configured:**
Go to **Settings** then **Pages** and confirm the source is set to **Deploy from a branch** with `gh-pages` selected.

**Build error in generated files:**
Run `mkdocs build` locally and check the terminal output for errors. Fix any issues in your content or configuration, then redeploy.

---

## Pages not appearing in navigation

**What you see:**
You created a Markdown file in `docs/` but it does not appear in the sidebar navigation on the site.

**What causes it:**
MkDocs uses explicit navigation. A page must be listed in the `nav` block of `mkdocs.yml` to appear in the sidebar.

**How to fix it:**
Open `mkdocs.yml` and add the missing page to the `nav` block:

```yaml
nav:
  - Home: index.md
  - Your New Page: your-new-page.md
```

Save the file and the local preview will update automatically. Redeploy to update the live site.

---

## YAML configuration error

**What you see:**
```
ERROR - Config value 'theme': Unrecognised theme name: ...
```
or
```
ERROR - mkdocs.yml contains a syntax error
```

**What causes it:**
YAML is whitespace-sensitive. A missing colon, incorrect indentation, or a tab character instead of spaces will cause MkDocs to fail.

**How to fix it:**

1. Check for missing colons after keys:

```yaml
# Wrong
site_name My Documentation

# Correct
site_name: My Documentation
```

2. Check that nested blocks are correctly indented with spaces and never tabs:

```yaml
# Wrong
theme:
name: material

# Correct
theme:
  name: material
```

3. Use a YAML validator such as [yamllint.com](https://www.yamllint.com/) to identify the exact line causing the error.

---

## Admonitions not rendering

**What you see:**
Your `!!! note` or `!!! warning` syntax appears as plain text rather than a styled callout box.

**What causes it:**
Either the `admonition` extension is not enabled in `mkdocs.yml`, or the content inside the admonition block is not indented correctly.

**How to fix it:**

First, confirm the extension is enabled in `mkdocs.yml`:

```yaml
markdown_extensions:
  - admonition
  - pymdownx.details
```

If the extension is enabled but the admonition still renders as plain text, check the indentation. Content inside an admonition block must be indented with exactly four spaces:

```markdown
# Wrong - no indentation
!!! note
This content will not render inside the box.

# Correct - four spaces
!!! note
    This content will render inside the box.
```

---

## Custom domain not working

**What you see:**
Your custom domain returns a 404 error or still redirects to the default GitHub Pages URL.

**What causes it:**
The CNAME file is missing from the `docs/` folder, the domain has not been set in GitHub Pages settings, or DNS records have not propagated yet.

**How to fix it:**

1. Confirm the CNAME file exists inside `docs/` and contains only your domain with no extra characters:

```
yourdomain.com
```

2. Go to **Settings** then **Pages** in your repository and confirm your custom domain is entered in the **Custom domain** field.
3. Confirm your DNS records are configured correctly with your domain registrar. See the [Personal Website Setup Guide](https://douglasebhoman.hashnode.dev/how-to-build-a-personal-website-with-a-custom-domain-and-professional-email) for the correct DNS configuration.
4. Wait. DNS propagation can take up to 48 hours. If everything is configured correctly, the domain will resolve once propagation is complete.

---

## mkdocs gh-deploy fails with a permission error

**What you see:**
```
ERROR - Failed to push to remote repository
```
or a Git authentication error.

**What causes it:**
Your terminal is not authenticated with GitHub, or the remote URL is set incorrectly.

**How to fix it:**

1. Confirm the remote URL is correct:

```bash
git remote -v
```

The output should show your repository URL. If it is wrong, reset it:

```bash
git remote set-url origin https://github.com/yourusername/your-repo-name.git
```

2. If you are using HTTPS, GitHub requires a personal access token instead of your account password. Generate one at **GitHub** then **Settings** then **Developer settings** then **Personal access tokens**. When your terminal prompts for a password, paste your personal access token instead of your GitHub account password.

3. If you are using SSH, confirm your SSH key is added to your GitHub account under **Settings** then **SSH and GPG keys**.

---

If none of the solutions above resolve your issue, check the [MkDocs GitHub Issues](https://github.com/mkdocs/mkdocs/issues) page or the [Material for MkDocs Discussions](https://github.com/squidfunk/mkdocs-material/discussions) for community support.