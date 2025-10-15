# Deployment Guide

## Подготовка к деплою

### 1. Проверка конфигурации

Убедитесь, что в `hugo.toml` правильно указан baseURL:
```toml
baseURL = 'https://altercha.com/'
```

Если используете GitHub Pages без custom domain:
```toml
baseURL = 'https://YOUR_USERNAME.github.io/altercha.com/'
```

### 2. Создание репозитория на GitHub

1. Создайте новый репозиторий на GitHub:
   - Название: `altercha.com` (или любое другое)
   - Visibility: Public (для бесплатного GitHub Pages)

2. Инициализируйте Git и добавьте remote:
```bash
cd /Users/denisotree/code/altercha.com
git init
git add .
git commit -m "Initial commit: Altercha tea website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/altercha.com.git
git push -u origin main
```

### 3. Настройка GitHub Pages

1. Перейдите в **Settings** → **Pages**
2. В разделе **Build and deployment**:
   - Source: выберите **GitHub Actions**
3. Сохраните изменения

### 4. Автоматический деплой

После push в `main` ветку:
- GitHub Actions автоматически запустит workflow
- Hugo соберет сайт
- Сайт задеплоится на GitHub Pages
- Процесс займет ~1-2 минуты

Проверить статус деплоя можно в разделе **Actions** репозитория.

## Custom Domain (altercha.com)

### 1. Настройка DNS

В настройках вашего DNS провайдера добавьте записи:

**A Records (для корневого домена):**
```
Type    Name    Value               TTL
A       @       185.199.108.153     3600
A       @       185.199.109.153     3600
A       @       185.199.110.153     3600
A       @       185.199.111.153     3600
```

**CNAME Record (для www):**
```
Type    Name    Value                           TTL
CNAME   www     YOUR_USERNAME.github.io.        3600
```

### 2. Настройка GitHub Pages

1. В **Settings** → **Pages** → **Custom domain**
2. Введите: `altercha.com`
3. Нажмите **Save**
4. Подождите проверки DNS (~10-30 минут)
5. Включите **Enforce HTTPS** (после успешной проверки)

### 3. Проверка

После настройки DNS (может занять до 24 часов):
- `https://altercha.com` - основной домен
- `https://www.altercha.com` - редирект на основной
- `https://YOUR_USERNAME.github.io/altercha.com/` - также работает

## Обновление сайта

### Добавление нового чая

1. Создайте папки для всех языков:
```bash
mkdir -p content/en/teas/new-tea
mkdir -p content/ru/teas/new-tea
mkdir -p content/pt/teas/new-tea
```

2. Добавьте `index.md` в каждую папку
3. Добавьте изображение `cover.jpg` (800x800px+)
4. Commit и push:
```bash
git add .
git commit -m "Add new tea: Tea Name"
git push
```

Сайт обновится автоматически через 1-2 минуты!

### Изменение дизайна

1. Редактируйте файлы в `assets/scss/main.scss` или `layouts/`
2. Проверьте локально: `hugo server -D`
3. Commit и push:
```bash
git add .
git commit -m "Update design: description"
git push
```

### Добавление переводов

1. Редактируйте файлы в `i18n/`:
   - `en.toml` - английский
   - `ru.toml` - русский
   - `pt.toml` - португальский
2. Commit и push

## Мониторинг

### Проверка деплоя

1. Перейдите в **Actions** в репозитории
2. Найдите последний workflow run
3. Проверьте статус:
   - ✅ Зеленая галочка - успешно
   - ❌ Красный крестик - ошибка (кликните для деталей)

### Логи сборки

В случае ошибки:
1. Откройте failed workflow
2. Кликните на job "build"
3. Разверните шаг "Build with Hugo"
4. Изучите ошибки

## Troubleshooting

### Сайт не обновляется

1. Проверьте статус в **Actions**
2. Очистите кеш браузера (Ctrl+Shift+R / Cmd+Shift+R)
3. Проверьте, что push прошел в ветку `main`

### Ошибка 404

1. Проверьте `baseURL` в `hugo.toml`
2. Убедитесь, что GitHub Pages настроен на GitHub Actions
3. Проверьте, что файл `CNAME` содержит правильный домен

### Изображения не загружаются

1. Проверьте, что изображения в правильных папках
2. Проверьте формат: `.jpg`, `.png`, `.webp`
3. Проверьте размер файлов (рекомендуется < 500KB)

### DNS не резолвится

1. Проверьте DNS записи: `dig altercha.com`
2. Подождите 24-48 часов для полного распространения
3. Используйте DNS checker: https://dnschecker.org

## Performance

### Оптимизация изображений

Перед добавлением изображений:
```bash
# Установите ImageMagick
brew install imagemagick

# Оптимизируйте изображение
convert input.jpg -resize 800x800^ -gravity center -extent 800x800 -quality 85 cover.jpg
```

### Минификация

Hugo автоматически минифицирует:
- HTML
- CSS
- JavaScript (если есть)

Настройки в `.github/workflows/hugo.yml`:
```yaml
hugo --gc --minify
```

## Backup

### Резервное копирование

Весь контент в Git - это уже backup!

Дополнительно можно:
1. Создать private fork
2. Настроить автоматический backup на другой сервис
3. Экспортировать контент: `hugo --destination backup/`

## Monitoring & Analytics

### Добавление Google Analytics

1. Получите Tracking ID
2. Добавьте в `hugo.toml`:
```toml
[params]
  googleAnalytics = "G-XXXXXXXXXX"
```

3. Добавьте в `layouts/partials/head.html`:
```html
{{ template "_internal/google_analytics.html" . }}
```

## Support

Если возникли проблемы:
1. Проверьте [Hugo Documentation](https://gohugo.io/documentation/)
2. Проверьте [GitHub Pages Documentation](https://docs.github.com/pages)
3. Проверьте логи в GitHub Actions
