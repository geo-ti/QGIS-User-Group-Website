# QGIS User Group Website

Hugo static site using the `hugo-bulma-blocks-theme`.

## Tech Stack

- **Hugo** (min v0.139.0) - Static site generator
- **Theme**: `hugo-bulma-blocks-theme` (Bulma CSS framework)
- **Navigation**: Custom web component from `qgis-uni-navigation`

## Directory Structure

```
├── config.toml              # Main configuration
├── content/                 # Markdown content
│   ├── _index.md           # Home page
│   ├── events.md
│   ├── who-we-are.md
│   ├── rules.md
│   └── blog/
│       └── _index.md       # Single blog page with Tips, Resources, Articles
├── static/
│   ├── config/navigation.json  # Secondary navigation config
│   └── img/                    # Images
├── layouts/partials/       # Custom layout overrides
└── themes/hugo-bulma-blocks-theme/
```

## Adding Content

### New Page

1. Create `content/page-name.md`:
```yaml
---
type: "page"
title: "Page Title"
subtitle: "Subtitle"
draft: false
heroSize: "is-medium"
HeroImage: "/img/hegobg1.webp"
HasBanner: true
sidebar: true
---

{{< content-start >}}

Your content here...

{{< content-end >}}
```

2. Add to navigation (see below)

### Blog Page

The blog is a single page at `/blog/` with three sections:
- **Tips** - Weekly QGIS tips
- **Resources** - Styles, palettes, projects, models, PyQGIS, actions, plugins
- **Articles** - In-depth tutorials

Edit `content/blog/_index.md` directly to add content to any section.

## Navigation

**Must update BOTH files** when adding menu items:

### 1. config.toml
```toml
[[menu.main]]
  name = "Page Name"
  url = "/page-name/"
  weight = 25  # Lower = earlier in menu
```

### 2. static/config/navigation.json
```json
{
  "type": "second-menu",
  "settings": {
    "name": "Page Name",
    "href": "/page-name/"
  }
}
```

## Theme Shortcodes

Wrap content in these shortcodes for consistent styling:

```markdown
{{< content-start >}}
Content here
{{< content-end >}}

{{< columns-start >}}
{{< column-start class="is-one-third" >}}
Column 1
{{< column-end >}}
{{< column-start class="is-two-thirds" >}}
Column 2
{{< column-end >}}
{{< columns-end >}}

{{< rich-box-start >}}
{{< rich-content-start themeClass="coloring-1" >}}
Styled box content
{{< rich-content-end >}}
{{< rich-box-end >}}
```

## Commands

```bash
hugo server          # Dev server at localhost:1313
hugo                 # Build to /public
```

## Brand Colors

Defined in `config.toml` under `[params]`:
- Primary green: `#589632`
- Links: `#3A9800`
