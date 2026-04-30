# Installation

This page is part of a complete guide to building and deploying documentation sites with MkDocs. If you have not already confirmed your prerequisites, start at [Prerequisites](prerequisites.md).

This page covers installing MkDocs and the Material theme on your machine. By the end you will have both tools installed and verified, ready to create your first project.

Install MkDocs first, then the Material theme. Both use pip and the order matters — installing MkDocs first ensures the correct version is in place before the Material theme adds its dependencies.

---

## Install MkDocs

Open your terminal and run:

```bash
pip install mkdocs
```

pip downloads and installs MkDocs and its dependencies automatically. This usually takes under a minute.

> **What you should see:** The final lines of output should include something like:
> ```
> Successfully installed mkdocs-1.6.1
> ```
> If you see a line beginning with `Successfully installed`, the installation completed without errors.

---

## Install the Material theme

This guide uses the Material theme, which provides a responsive layout, built-in search, and extensive configuration options.

Install it with:

```bash
pip install mkdocs-material
```

> **What you should see:** The final lines of output should include something like:
> ```
> Successfully installed mkdocs-material-9.x.x
> ```
> The exact version number will differ. Any version beginning with 9 is current.

---

## Verify the installation

Run each command separately and confirm both return output without errors. The first confirms MkDocs is installed. The second confirms the Material theme is installed separately, since it is a different package.

```bash
mkdocs --version
```

```bash
pip show mkdocs-material
```

**What you should see:**

`mkdocs --version` returns something like:

```
mkdocs, version 1.6.1
```

`pip show mkdocs-material` returns package details including the version number and installation location:

```
Name: mkdocs-material
Version: 9.x.x
Summary: Documentation that simply works
Location: /usr/local/lib/python3.x/site-packages
```

If both commands return output without errors, your installation is complete.

---

## Troubleshooting

**`mkdocs` is not recognised as a command**

On Windows, this usually means Python was not added to PATH during installation. Reinstall Python from [python.org](https://www.python.org/downloads/) and check the box that says **"Add Python to PATH"** during setup. Then close and reopen your terminal before trying again.

On macOS and Linux, try closing and reopening your terminal after installation. Some PATH changes only take effect in a new terminal session. If that does not work, run MkDocs directly using:

```bash
python -m mkdocs --version
```

**`pip` is not recognised as a command**

Try running `pip3` instead of `pip`. On macOS and Linux, `pip3` is the correct command when multiple Python versions are installed:

```bash
pip3 install mkdocs
pip3 install mkdocs-material
```

---

Your tools are installed and verified. Move to [Creating a Project](creating-a-project.md) to build your first MkDocs project.