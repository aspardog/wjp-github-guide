# GitHub Guide — WJP

Site built with [Quarto](https://quarto.org) and published on GitHub Pages.

## Structure

```
.
├── _quarto.yml              # Site configuration (navbar, sidebar, theme)
├── index.qmd                # Landing page
├── about.qmd                # About page
├── guia/                    # Guide section (hierarchical)
│   ├── index.qmd            # Guide index
│   ├── 01-conceptos.qmd     # Basic concepts
│   ├── 02-setup.qmd         # Initial setup
│   └── 03-clonar.qmd        # Cloning repositories
├── blog/                    # Blog section (chronological)
│   ├── index.qmd            # Listing
│   └── posts/
│       └── bienvenida/
│           └── index.qmd
├── styles.css               # Custom CSS
├── styles-dark.css          # Dark mode overrides
├── .github/workflows/
│   └── publish.yml          # CI/CD for publishing
├── .gitignore
└── README.md
```

## Local setup

### 1. Install Quarto

```bash
# macOS
brew install --cask quarto

# Linux (DEB)
# Download from https://quarto.org/docs/get-started/

# Windows
winget install Quarto.Quarto
```

Verify:

```bash
quarto --version    # should be 1.4+ ideally 1.5+
```

### 2. Clone and preview

```bash
git clone git@github.com:aspardog/wjp-github-guide.git
cd wjp-github-guide
quarto preview
```

Opens at `http://localhost:NNNN` and auto-reloads when saving changes to any `.qmd`.

### 3. Manual render (not needed for deploy)

```bash
quarto render
# Generates the entire site in _site/
```

## Publishing

Deployment is **automatic**: each push to `main` triggers the workflow `.github/workflows/publish.yml`, which renders the site and publishes the result to the `gh-pages` branch.

### Enable GitHub Pages

The first time, you need to tell GitHub to serve from `gh-pages`:

1. In the repo: **Settings → Pages**.
2. **Source**: Deploy from a branch.
3. **Branch**: `gh-pages`, folder `/ (root)`.
4. Save.

The site URL will be `https://aspardog.github.io/wjp-github-guide/`.

## Contributing

- **Errata, typos, broken links**: Direct PR, no prior issue needed.
- **New content**: Open an issue first to discuss scope.
- **Team policy/convention changes**: Require consensus, not just code review.

## Stack

| Component | Purpose |
|-----------|---------|
| Quarto | Static site generator |
| GitHub Actions | CI: render + publish |
| GitHub Pages | Static hosting |
| Cosmo (Bootswatch) | Base theme |

## License

Content under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Code under MIT.
