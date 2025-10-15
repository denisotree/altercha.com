# Quick Deploy Guide - Altercha

## 🚀 Быстрый деплой на GitHub Pages

### Шаг 1: Создайте репозиторий на GitHub

1. Перейдите на https://github.com/new
2. Repository name: `altercha.com`
3. Visibility: **Public**
4. Нажмите **Create repository**

### Шаг 2: Загрузите код

```bash
cd /Users/denisotree/code/altercha.com

# Инициализируйте Git (если еще не сделано)
git init

# Добавьте все файлы
git add .

# Сделайте первый коммит
git commit -m "Initial commit: Altercha tea website"

# Переименуйте ветку в main
git branch -M main

# Добавьте remote (замените YOUR_USERNAME на ваш GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/altercha.com.git

# Загрузите код
git push -u origin main
```

### Шаг 3: Настройте GitHub Pages

1. Откройте репозиторий на GitHub
2. Перейдите в **Settings** (⚙️)
3. В левом меню выберите **Pages**
4. В разделе **Build and deployment**:
   - **Source**: выберите **GitHub Actions**
5. Готово! 🎉

### Шаг 4: Дождитесь деплоя

1. Перейдите во вкладку **Actions** в репозитории
2. Вы увидите запущенный workflow "Deploy Hugo site to Pages"
3. Подождите ~1-2 минуты пока он завершится (зеленая галочка ✅)
4. Ваш сайт доступен по адресу: `https://YOUR_USERNAME.github.io/altercha.com/`

## 🌐 Настройка custom domain (altercha.com)

### Шаг 1: Настройте DNS

В панели управления вашего DNS провайдера добавьте:

**A Records:**
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**CNAME Record:**
```
www → YOUR_USERNAME.github.io
```

### Шаг 2: Добавьте домен в GitHub

1. В **Settings** → **Pages** → **Custom domain**
2. Введите: `altercha.com`
3. Нажмите **Save**
4. Подождите проверки DNS (~10-30 минут)
5. Включите **Enforce HTTPS**

### Шаг 3: Готово!

Сайт будет доступен по адресу: `https://altercha.com`

## 📝 Обновление сайта

После любых изменений:

```bash
git add .
git commit -m "Описание изменений"
git push
```

Сайт обновится автоматически через 1-2 минуты!

## ✅ Что уже настроено

- ✅ GitHub Actions workflow (`.github/workflows/hugo.yml`)
- ✅ Hugo конфигурация (`hugo.toml`)
- ✅ CNAME файл для custom domain (`static/CNAME`)
- ✅ .gitignore для исключения временных файлов
- ✅ Robots.txt для SEO
- ✅ Автоматическая минификация HTML/CSS
- ✅ Оптимизация изображений
- ✅ Мультиязычность (EN, RU, PT)

## 🔧 Проверка перед деплоем

```bash
# Проверьте что сайт работает локально
hugo server -D

# Откройте http://localhost:1313
# Проверьте все страницы и языки
```

## 📞 Нужна помощь?

Смотрите подробную инструкцию в `DEPLOYMENT.md`
