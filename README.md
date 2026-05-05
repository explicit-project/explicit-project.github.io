# EXPLICIT Project Website

This repository contains the source code for the **EXPLICIT project website**, built with [Hugo](https://gohugo.io/) using the [Blowfish theme](https://blowfish.page/).

## Repository Structure

```
.
├── assets/                   # Images, logos, and custom resources
├── content/                  # Website sections (Home, News, Project, Publications, Team, Contact)
│   └── en/                   # Content language (en=english, es=spanish, etc.)
│       ├── _index.md
│       ├── project.md
│       ├── publications.md
│       ├── team.md
│       ├── contact.md
│       └── news/             # News section (one news post)
│           ├── _index.md
│           └── <news-entry>/
│               ├── index.md
│               └── featured.jpg
├── data/                     # Structured data (team.yml, publications.yml)
├── layouts/                  # Custom partials and shortcodes
├── static/                   # Static files served directly
├── themes/                   # Blowfish theme (Git submodule)
├── hugo.toml                 # Hugo configuration file
└── README.md
```

### Website Content

Website sections are stored in `/content`:

- `_index.md` – Home page content
- `news/` – News and updates section (list of posts)
- `project.md` – Project description and details
- `publications.md` – Publications page (renders content from `data/publications.yaml`)
- `team.md` – Team page (renders content from `data/team.yaml`)
- `contact.md` – Contact information

> 💡 Updating these markdown files changes the content and layout of the corresponding pages.

### News Section

The `news` section is organized using **page bundles**, where each news item is stored in its own directory containing the content and associated assets:

```
content/en/news/<news-entry>/
                ├── index.md
                ├── featured.jpg
                ...
```

#### Naming Convention

Each news entry directory should follow a consistent and descriptive naming scheme:

```
YYYY/MM/DD/short-title
```

For example:

```
2025/09/01/project-funded
2026/04/13/conference-presentation
```

This convention ensures chrological ordering, readability, unique and predictable URLs.

> ⚠️ **The directory name is used as the page slug**, so keep it short, lowercase and hyphen-separated.

#### Content Guidelines

- `index.md` – news content and front matter
- `featured.jpg` – (optional) used as the main image for previews and listings
- Additional images or assets can be included in the same directory and referenced relatively

### Data Files

Data-driven content is stored in `/data`:

- [team.yaml](data/team.yaml) – project members grouped by role
- [publications.yaml](data/publications.yaml) – structured list of outputs (journals, conferences, datasets, repositories, etc.)

These are rendered through custom partials and shortcodes.

> ⚠️ **To update the website, simply edit the corresponding YAML files**—no code changes are required.  
> For more details on the structure of each file, see the YAML files themselves.

### Theme Management

This website uses the [**Blowfish** theme](https://blowfish.page/) as a **Git submodule**.

> ⚠️ **Do not modify files inside `themes/blowfish/` directly.**  
> Any local edits will be lost when the theme is updated.

To update the theme to its latest version, run:

```bash
git submodule update --remote --merge
```

If you need to override templates, styles, or partials,
create a file with the same name and path inside the `/layouts` or `/assets` directory of this repository.
Hugo will automatically prioritize your local version over the theme’s version.

## Installation

### Local Development

Clone the repository and initialize submodules:

```bash
git clone https://github.com/explicit-project/website.git
cd website
git submodule update --init --recursive
```

Run a local development server:

```bash
hugo server
````

Then visit http://localhost:1313.

### Development with Docker

If using [VS Code + Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers):

```bash
docker compose up
```

Then open the workspace in VS Code. The development server should start automatically.

### Deployment via GitHub Pages

This site is automatically deployed using GitHub Actions whenever changes are pushed to the main branch. See the workflow configuration [here](.github/workflows/gh-pages.yml).

## Image Credits

Some images used on this website are licensed under **Creative Commons** and are attributed below:

| Image | Author / Source | License |
|--------|------------------|----------|
| Hero image on the homepage | [Unsplash](https://unsplash.com/photos/a-close-up-of-a-computer-circuit-board-tBvF46kmwBw) by Luke Jones | [Unsplash License](https://unsplash.com/license) |
| Funding logos | Provided by the [Spanish Ministry of Science (MICIU) and AEI](https://www.aei.gob.es/va/sobre-aei/imagen-institucional) | — |
