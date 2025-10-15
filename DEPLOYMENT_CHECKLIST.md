# Deployment Checklist

## ✅ Перед деплоем

### Конфигурация
- [ ] Проверьте `baseURL` в `hugo.toml`
  - С custom domain: `https://altercha.com/`
  - Без custom domain: `https://YOUR_USERNAME.github.io/altercha.com/`
- [ ] Проверьте `static/CNAME` (если используете custom domain)
- [ ] Проверьте `.gitignore` (должен исключать `/public/` и `/resources/`)

### Контент
- [ ] Все чаи имеют изображения (`cover.jpg`)
- [ ] Все чаи переведены на 3 языка (EN, RU, PT)
- [ ] Front matter заполнен корректно (title, date, categories, tags)
- [ ] Нет draft страниц (или используйте `hugo server -D` для проверки)

### Дизайн
- [ ] Проверьте сайт локально: `hugo server -D`
- [ ] Проверьте все страницы:
  - [ ] Главная (`/`)
  - [ ] Категории (`/categories/white-tea/`)
  - [ ] Теги (`/tags/yunnan/`)
  - [ ] Страницы чая
- [ ] Проверьте все языки (EN, RU, PT)
- [ ] Проверьте мобильную версию (DevTools → Toggle device)
- [ ] Проверьте hamburger menu
- [ ] Проверьте переключатель языков

### Изображения
- [ ] Все изображения оптимизированы (< 500KB)
- [ ] Формат: `.jpg`, `.png` или `.webp`
- [ ] Размер: минимум 800x800px
- [ ] Названия файлов: `cover.jpg` (единообразие)

## 🚀 Деплой на GitHub

### Создание репозитория
- [ ] Создан репозиторий на GitHub
- [ ] Visibility: Public (для бесплатного GitHub Pages)
- [ ] Название: `altercha.com` (или другое)

### Загрузка кода
```bash
# Выполните эти команды:
cd /Users/denisotree/code/altercha.com
git init
git add .
git commit -m "Initial commit: Altercha tea website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/altercha.com.git
git push -u origin main
```

- [ ] Код загружен на GitHub
- [ ] Все файлы на месте (проверьте на GitHub)
- [ ] `.github/workflows/hugo.yml` присутствует

### Настройка GitHub Pages
- [ ] Settings → Pages
- [ ] Source: **GitHub Actions** (не Deploy from branch!)
- [ ] Сохранено

### Проверка деплоя
- [ ] Actions → Workflow запущен
- [ ] Workflow завершился успешно (зеленая галочка ✅)
- [ ] Сайт доступен по URL (указан в Pages settings)

## 🌐 Custom Domain (опционально)

### DNS настройки
- [ ] A Records добавлены:
  ```
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
  ```
- [ ] CNAME Record добавлен: `www → YOUR_USERNAME.github.io`
- [ ] DNS изменения сохранены

### GitHub настройки
- [ ] Settings → Pages → Custom domain
- [ ] Домен введен: `altercha.com`
- [ ] DNS check прошел успешно ✅
- [ ] Enforce HTTPS включен

### Проверка домена
- [ ] `https://altercha.com` открывается
- [ ] `https://www.altercha.com` редиректит на основной
- [ ] HTTPS работает (зеленый замок 🔒)
- [ ] Все языки доступны

## 🧪 Тестирование после деплоя

### Функциональность
- [ ] Главная страница загружается
- [ ] Навигация работает
- [ ] Переключатель языков работает
- [ ] Мобильное меню работает
- [ ] Все изображения загружаются
- [ ] Все ссылки работают
- [ ] Категории отображаются правильно
- [ ] Теги работают

### Производительность
- [ ] Сайт загружается быстро (< 3 секунд)
- [ ] Изображения оптимизированы
- [ ] Нет ошибок в консоли браузера
- [ ] Нет 404 ошибок

### SEO
- [ ] `robots.txt` доступен (`/robots.txt`)
- [ ] `sitemap.xml` доступен (`/sitemap.xml`)
- [ ] Meta tags присутствуют (View Page Source)
- [ ] Alt текст на изображениях

### Мобильная версия
- [ ] Сайт адаптивный
- [ ] Hamburger menu работает
- [ ] Overlay появляется
- [ ] Крестик анимируется
- [ ] Меню закрывается при клике вне
- [ ] Body scroll блокируется

### Браузеры
- [ ] Chrome/Edge
- [ ] Firefox
- [ ] Safari
- [ ] Mobile Safari (iOS)
- [ ] Chrome Mobile (Android)

## 📊 Мониторинг

### После деплоя
- [ ] Проверьте Google Search Console (через неделю)
- [ ] Проверьте Google Analytics (если настроен)
- [ ] Проверьте Lighthouse score
- [ ] Проверьте PageSpeed Insights

### Регулярно
- [ ] Проверяйте GitHub Actions на ошибки
- [ ] Обновляйте контент
- [ ] Следите за issues в репозитории

## 🔧 Troubleshooting

### Если что-то не работает:

**Сайт не открывается:**
1. Проверьте Actions → последний workflow
2. Проверьте Settings → Pages → URL
3. Подождите 5-10 минут после первого деплоя

**404 ошибка:**
1. Проверьте `baseURL` в `hugo.toml`
2. Проверьте Source в Pages settings (должен быть GitHub Actions)
3. Пересоберите: push новый коммит

**Изображения не загружаются:**
1. Проверьте пути к изображениям
2. Проверьте что изображения в Git (не в .gitignore)
3. Проверьте формат файлов

**CSS не применяется:**
1. Очистите кеш браузера (Ctrl+Shift+R)
2. Проверьте что `assets/scss/main.scss` в Git
3. Проверьте консоль браузера на ошибки

**Custom domain не работает:**
1. Проверьте DNS записи: `dig altercha.com`
2. Подождите 24-48 часов для распространения DNS
3. Проверьте `static/CNAME` файл

## ✅ Финальная проверка

Перед тем как считать деплой завершенным:

- [ ] Сайт открывается по основному URL
- [ ] Все 3 языка работают
- [ ] Мобильная версия работает корректно
- [ ] Все изображения загружаются
- [ ] Нет ошибок в консоли
- [ ] HTTPS работает (если custom domain)
- [ ] Robots.txt и sitemap.xml доступны

## 🎉 Готово!

Если все пункты отмечены ✅ - поздравляем, сайт успешно задеплоен!

Теперь при каждом `git push` сайт будет автоматически обновляться.
