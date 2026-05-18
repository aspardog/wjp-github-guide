# Guía de GitHub — WJP

Sitio construido con [Quarto](https://quarto.org) y publicado en GitHub Pages.

## Estructura

```
.
├── _quarto.yml              # Configuración del sitio (navbar, sidebar, tema)
├── index.qmd                # Landing
├── about.qmd                # Acerca de
├── guia/                    # Sección de guía (jerárquica)
│   ├── index.qmd            # Índice de la guía
│   ├── 01-conceptos.qmd
│   ├── 02-setup.qmd
│   └── 03-modelo-mental.qmd
├── blog/                    # Sección de blog (cronológica)
│   ├── index.qmd            # Listing
│   └── posts/
│       └── bienvenida/
│           └── index.qmd
├── styles.css               # CSS personalizado
├── styles-dark.css          # Overrides modo oscuro
├── .github/workflows/
│   └── publish.yml          # CI/CD para publicación
├── .gitignore
└── README.md
```

## Setup local

### 1. Instalar Quarto

```bash
# macOS
brew install --cask quarto

# Linux (DEB)
# Descargar desde https://quarto.org/docs/get-started/

# Windows
winget install Quarto.Quarto
```

Verificá:

```bash
quarto --version    # debería ser 1.4+ idealmente 1.5+
```

### 2. Clonar y previsualizar

```bash
git clone git@github.com:TU-USUARIO/wjp-github-guide.git
cd wjp-github-guide
quarto preview
```

Se abre en `http://localhost:NNNN` y recarga automáticamente al guardar cambios en cualquier `.qmd`.

### 3. Render manual (no necesario para deploy)

```bash
quarto render
# Genera todo el sitio en _site/
```

## Publicación

El deploy es **automático**: cada push a `main` dispara el workflow `.github/workflows/publish.yml`, que renderiza el sitio y publica el resultado a la rama `gh-pages`.

### Activar GitHub Pages

La primera vez, hay que indicarle a GitHub que sirva desde `gh-pages`:

1. En el repo: **Settings → Pages**.
2. **Source**: Deploy from a branch.
3. **Branch**: `gh-pages`, carpeta `/ (root)`.
4. Guardar.

La URL del sitio será `https://TU-USUARIO.github.io/wjp-github-guide/`.

Acordate de actualizar `site-url` y `repo-url` en `_quarto.yml` y los links en `index.qmd` y `about.qmd` con tu usuario/organización real.

## Contribuir

- **Erratas, typos, links rotos**: PR directo, sin issue previo.
- **Nuevo contenido**: abrí un issue primero para discutir alcance.
- **Cambios de política/convención del equipo**: requieren consenso, no solo review de código.

## Stack

| Pieza | Para qué |
|---|---|
| Quarto | Generador de sitio estático |
| GitHub Actions | CI: render + publish |
| GitHub Pages | Hosting estático |
| Cosmo (Bootswatch) | Tema base |

## Licencia

Contenido bajo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Código bajo MIT.
