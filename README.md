# Altercha - Premium Tea Collection

Multilingual Hugo website for premium tea collection with support for English, Russian, and Portuguese.

## Features

- 🌍 **Multilingual**: EN, RU, PT with automatic language detection
- 📱 **Responsive**: Mobile-first design with hamburger menu
- 🎨 **Modern UI**: Clean, minimalist design with smooth animations
- 🖼️ **Image Processing**: Automatic image optimization with Hugo
- 🏷️ **Taxonomies**: Categories and tags for tea organization
- ♿ **Accessible**: ARIA labels, keyboard navigation, semantic HTML

## Project Structure

```
altercha.com/
├── archetypes/          # Content templates
├── assets/
│   └── scss/           # Styles (main.scss)
├── content/
│   ├── en/             # English content
│   ├── ru/             # Russian content
│   └── pt/             # Portuguese content
├── i18n/               # Translation strings
│   ├── en.toml
│   ├── ru.toml
│   └── pt.toml
├── layouts/
│   ├── _default/       # Default templates
│   ├── partials/       # Reusable components
│   └── teas/           # Tea-specific templates
├── static/             # Static files
└── hugo.toml           # Hugo configuration

```

## Local Development

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) v0.128.0 or higher
- Git

### Setup

1. Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/altercha.com.git
cd altercha.com
```

2. Run the development server:
```bash
hugo server -D
```

3. Open http://localhost:1313 in your browser

### Adding New Tea

1. Create a new tea directory:
```bash
mkdir -p content/en/teas/tea-name
mkdir -p content/ru/teas/tea-name
mkdir -p content/pt/teas/tea-name
```

2. Add `index.md` in each language folder:
```markdown
---
title: "Tea Name"
date: 2024-01-01
categories: ["white-tea"]
tags: ["yunnan", "premium"]
recommended: true
---

Tea description...
```

3. Add image `cover.jpg` (800x800px or larger) to each folder

4. The tea will automatically appear on the site!

## Categories

Available tea categories (with translations):
- `white-tea` - White Tea / Белый чай / Chá Branco
- `green-tea` - Green Tea / Зеленый чай / Chá Verde
- `black-tea` - Black Tea / Красный чай / Chá Preto
- `oolong-tea` - Oolong / Улун / Oolong
- `sheng-puerh` - Sheng Pu-erh / Шен пуэр / Sheng Pu-erh
- `shu-puerh` - Shu Pu-erh / Шу пуэр / Shu Pu-erh
- `herbal-tea` - Herbal Tea / Травяной чай / Chá Herbal

## Deployment

The site automatically deploys to GitHub Pages when you push to the `main` branch.

### GitHub Pages Setup

1. Go to your repository settings
2. Navigate to **Pages** section
3. Under **Build and deployment**:
   - Source: **GitHub Actions**
4. Push to `main` branch - the site will deploy automatically!

### Custom Domain

To use a custom domain (altercha.com):

1. Add a `CNAME` file to `/static/` with your domain:
```
altercha.com
```

2. Configure DNS records at your domain provider:
```
Type    Name    Value
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
CNAME   www     YOUR_USERNAME.github.io
```

3. In repository settings → Pages → Custom domain, enter `altercha.com`

## Technologies

- **Hugo** - Static site generator
- **SCSS** - Styling
- **GitHub Actions** - CI/CD
- **GitHub Pages** - Hosting

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## License

All rights reserved.
