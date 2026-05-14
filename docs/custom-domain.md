# Custom Domain

This page is part of a complete guide to building and deploying documentation sites with MkDocs. If you have not yet deployed your site, start at [Deploying to GitHub Pages](deploying-to-github-pages.md).

A documentation site at `docs.yourcompany.com` signals that documentation is a first-class product, not an afterthought hosted on a platform URL. By default, your MkDocs site is served at a GitHub Pages address:

```
https://yourusername.github.io/your-repo-name/
```

A custom domain replaces that address with something you own. This makes your documentation feel professional, builds trust with your readers, and makes the URL easier to remember and share.

This page covers the MkDocs-specific configuration required to connect a custom domain. For the full DNS and GitHub Pages setup, including Cloudflare configuration, A records, and HTTPS, see the [Personal Website Setup Guide](https://douglasebhoman.com/personal-website-setup-guide/).

---

## Add a CNAME file to your project

GitHub Pages uses a CNAME file to map your custom domain to your repository. In an MkDocs project, this file must live inside the `docs/` folder and not in the project root alongside `mkdocs.yml`. MkDocs copies everything inside `docs/` into the built site, so placing the CNAME file there ensures it is included every time you deploy.

Create a file called `CNAME` (no file extension) inside your `docs/` folder:

```
my-project/
├── mkdocs.yml
└── docs/
    ├── index.md
    └── CNAME
```

The file should contain only your custom domain:

```
yourdomain.com
```

Or if you are using a subdomain:

```
docs.yourdomain.com
```

Do not include `https://` or a trailing slash. GitHub Pages will reject the domain if either is present.

Use a subdomain like `docs.yourdomain.com` if your root domain is already serving another site, such as a marketing page or portfolio. Use the root domain if this documentation site is your primary web presence.

---

## Update site_url in mkdocs.yml

Update your `mkdocs.yml` to reflect your custom domain:

```yaml
site_url: https://yourdomain.com/
```

This ensures MkDocs generates all internal links and asset paths relative to your custom domain rather than the default GitHub Pages URL.

---

## Redeploy your site

After adding the CNAME file and updating `site_url`, redeploy your site:

```bash
mkdocs gh-deploy
```

This rebuilds the site and pushes the updated files, including the CNAME file, to the `gh-pages` branch.

> **Note:** If you skip this step, GitHub Pages will not recognise your custom domain and will revert to the default GitHub Pages URL.

---

## Enable your custom domain in GitHub Pages settings

After redeploying, tell GitHub Pages to serve your site from your custom domain:

1. Go to your repository on GitHub.
2. Click **Settings** in the top navigation menu.
3. In the left sidebar, click **Pages**.
4. Under **Custom domain**, enter your domain and click **Save**.
5. Wait for the DNS check to complete. GitHub will display a confirmation once the domain is verified.
6. Check the **Enforce HTTPS** box once it becomes available. This may take a few minutes after the DNS check passes.

> **Note:** If the DNS check fails immediately, your DNS records may not have propagated yet. Wait a few minutes and try saving again.

---

## Verify your custom domain

Once DNS is configured and GitHub Pages is updated, visit your custom domain in your browser and confirm your documentation site loads correctly.

> **Note:** DNS changes can take anywhere from a few minutes to 48 hours to propagate globally. If your domain is not working immediately, wait and try again before troubleshooting. If your domain is still not working after 48 hours, see the [Troubleshooting](troubleshooting.md) page for the custom domain error entry.

---

Once your custom domain is live and verified, move to [Troubleshooting](troubleshooting.md) if you encounter any issues.