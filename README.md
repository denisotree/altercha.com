# AlterChá

Multilingual tea catalog built with Hugo. Supports EN, RU, PT.

## Development

```bash
hugo server -D
```

Open http://localhost:1313

## Deploy

Push to `main` branch → auto-deploy to GitHub Pages via Actions.

**Setup:** Settings → Pages → Source: GitHub Actions

## Add Tea

```bash
mkdir -p content/{en,ru,pt}/teas/tea-name
```

Add `index.md` + `cover.jpg` to each folder.

## Tech

Hugo · SCSS · GitHub Actions · GitHub Pages
