# Deploying to GitHub Pages

This page is part of a complete guide to building and deploying documentation sites with MkDocs. If you have not yet previewed your site locally, start at [Previewing Locally](previewing-locally.md).

Everything you have built locally is about to become publicly accessible. This page covers every step, from creating the repository to seeing your documentation live at a real URL. Follow each step in order and do not skip ahead.

---

## Before you deploy

Make sure the following are in place before continuing:

- Your documentation content is complete and all pages, links, and images have been verified in local preview.
- Git is installed on your machine. Run `git --version` to confirm.
- You have a GitHub account. Create one at [github.com](https://github.com) if you do not already have one.
- Your `mkdocs.yml` has `site_url` set to your GitHub Pages URL:

```yaml
site_url: https://yourusername.github.io/your-repo-name/
```

Confirm the URL matches the pattern `https://yourusername.github.io/your-repo-name/` exactly. A wrong URL will cause broken links on the live site.

> **Note:** If you do not know your repository name yet, complete the next section first and come back to update this setting before running the deploy command.

---

## Create a GitHub repository

1. Log in to your GitHub account at [github.com](https://github.com).
2. Click the **+** icon in the top-right corner and select **New repository**.
3. Give the repository a name that matches your project. For example, `mkdocs-for-technical-writers`.
4. Add an optional description.
5. Set visibility to **Public**. GitHub Pages is available on public repositories on the free plan.
6. Do not initialise the repository with a README, `.gitignore`, or licence. Initialising with these files creates a commit history that conflicts with your local project when you try to push.
7. Click **Create repository**.

GitHub will show you a page with setup instructions. Keep this tab open. You will need the repository URL in the next step.

---

## Connect your local project to the repository

Run all commands from the root directory of your project — the folder that contains your `mkdocs.yml` file. If you are in the wrong directory, the deployment will fail.

Navigate to your project folder in your terminal:

```bash
cd path/to/your/project
```

Before pushing, create a `.gitignore` file in your project root to exclude the `site/` folder from version control. The `site/` folder is generated fresh every time you deploy and does not need to be tracked in Git:

```
site/
```

Then run the following commands in order:

**Initialise Git** (skip this if your project is already a Git repository):

```bash
git init
```

**Stage all files:**

```bash
git add .
```

**Create your first commit:**

```bash
git commit -m "Initial commit"
```

**Link your local repository to GitHub:**

```bash
git remote add origin https://github.com/yourusername/your-repo-name.git
```

Replace the URL with the repository URL from the GitHub tab you kept open.

**Push to GitHub:**

```bash
git push -u origin main
```

> **What you should see:** GitHub confirms the push with a summary of the files uploaded. If you see an error about the branch name, run `git branch` to see your current branch name, then try `git push -u origin master` if your branch is named `master` instead of `main`.

---

## Deploy with mkdocs gh-deploy

MkDocs includes a built-in deployment command that builds your site and pushes it to the `gh-pages` branch of your repository automatically. You do not need to run `mkdocs build` first. The deploy command handles the build step.

Run:

```bash
mkdocs gh-deploy
```

> **What you should see:** MkDocs builds your site, pushes the static files to the `gh-pages` branch, and prints a confirmation message including your live site URL:
> ```
> INFO - Your documentation should shortly be available at:
> https://yourusername.github.io/your-repo-name/
> ```

If this command fails, see the [Troubleshooting](troubleshooting.md) page for the most common deployment errors.

---

## Enable GitHub Pages in repository settings

After running `mkdocs gh-deploy`, the `gh-pages` branch exists in your repository. Now tell GitHub to serve it as your Pages site:

1. Go to your repository on GitHub.
2. Click **Settings** in the top navigation menu.
3. In the left sidebar, click **Pages**.
4. Under **Source**, select **Deploy from a branch**. If you see GitHub Actions as the default source option, select Branch instead and proceed with the steps below.
5. Under **Branch**, select `gh-pages` and leave the folder set to `/ (root)`.
6. Click **Save**.

> **Note:** If you do not see these options, check that your repository is set to Public. GitHub Pages is not available on private repositories on the free plan. If you have already run `mkdocs gh-deploy` and the `gh-pages` branch exists, GitHub Pages may already be configured automatically. Check the Pages settings before making changes.

---

## Your live site URL

Once GitHub Pages is enabled, your site will be available at:

```
https://yourusername.github.io/your-repo-name/
```

It typically goes live within a few minutes of enabling Pages. In some cases it can take up to 10 minutes.

You will see a confirmation banner in the GitHub Pages settings once the site is live. To monitor deployment status, go to the **Actions** tab in your repository and look for the `pages-build-deployment` workflow. GitHub runs this workflow each time the `gh-pages` branch is updated.

---

## Updating your site

Every time you make changes to your documentation, redeploy by running:

```bash
mkdocs gh-deploy
```

This rebuilds the site and pushes the updated files to `gh-pages`. The live site will update within a minute or two.

---

Once your site is live, move to [Custom Domain](custom-domain.md) to connect it to your own domain name. If you do not need a custom domain, you can skip directly to [Troubleshooting](troubleshooting.md) or consider your site complete.