# Previewing Locally

This page is part of a complete guide to building and deploying documentation sites with MkDocs. If you have not yet configured your site, start at [Configuring mkdocs.yml](configuring-mkdocs-yml.md).

Your site is configured. Before you push it to the world, you need to see it the way your readers will. MkDocs includes a built-in development server that builds your site and serves it in your browser with live reload so every change you save appears instantly without restarting the server.

---

## Start the local preview server

From inside your project folder, run:

```bash
mkdocs serve
```

Then open your browser and navigate to:

```
http://127.0.0.1:8000
```

This is your machine's local address. It only exists on your computer and is not accessible to anyone else.

> **What you should see:** Your documentation site fully rendered in the browser, with your site name in the header, your navigation structure in the sidebar, and your content on the page. Any configuration you have set in `mkdocs.yml`, including theme, colours, and navigation, will be visible here exactly as it will appear on the live site.

---

## Live reload

MkDocs watches your project files while the server is running. Any time you save a change, whether the change is in a Markdown file, a navigation update in `mkdocs.yml`, or a CSS file, the browser refreshes automatically.

You do not need to stop and restart the server to see your changes. Save the file and the browser updates within a second or two.

This makes the iteration process significantly faster. Write, save, and review without leaving your editor.

---

## Stop the server

When you are done previewing, return to your terminal and press:

```
Ctrl + C
```

This shuts down the local server. The site will no longer be accessible at `http://127.0.0.1:8000` until you run `mkdocs serve` again.

> **Note:** On some Windows terminals, pressing Ctrl + C will prompt: "Terminate batch job (Y/N)?" Type Y and press Enter to confirm. On macOS and Linux, Ctrl + C stops the server immediately with no confirmation required. In both cases this is expected behaviour. It does not mean something went wrong.

---

## Pre-deployment checklist

Before moving to deployment, work through the following checks in your local preview:

- **Navigation:** click through every item in the sidebar and confirm each page loads correctly. Check that the order and structure match what you defined in `mkdocs.yml`. If a page is missing or in the wrong order, update the `nav` block in `mkdocs.yml` and save.

- **Internal links:** click every link inside your Markdown content and confirm it points to the correct page. If a link is broken, correct the path in your Markdown file and save. The browser will update automatically.

- **Images and media:** scroll through every page and confirm all images render correctly. If an image is missing, check that the file path is correct and that the file is inside the `docs/` folder. Images stored outside `docs/` will not be included in the build.

- **mkdocs.yml:** review your configuration one final time. Confirm the `site_name`, `site_url`, theme settings, and navigation structure are all correct. If anything is wrong, fix it and save. The server will reload automatically.

- **Custom CSS:** if you have added custom styles, check that they are rendering as expected and not breaking the layout on any page. If a style is not applying, check that the file path in `extra_css` matches the actual location of your stylesheet.

> **Note:** You do not need to run `mkdocs build` before deploying. The deployment step in the next section handles the build automatically.

---

Once every item on this list is confirmed in your local preview, move to [Deploying to GitHub Pages](deploying-to-github-pages.md).