# Создание блога на MkDocs + GitHub Pages

Дата: 2024-01-10

## Задача

Создать самый простой и бесплатный блог для документации.

Требования:
- Просто добавлять файлы md в папку
- Они должны автоматически публиковаться на сайте
- Минимальный функционал

## Варианты решения

### Вариант 1: Jekyll + GitHub Pages

Плюсы:
- Интегрирован в GitHub Pages
- Публикуется бесплатно на github.io

Минусы:
- Сложнее Ruby-экосистема

### Вариант 2: MkDocs-Material

Плюсы:
- Минимальная настройка
- Отличная навигация
- Одна команда для деплоя
- Понятная структура

### Вариант 3: VitePress/Netlify

Плюсы:
- Быстрый
- Красивый UI

Минусы:
- Требует Node.js
- Сложнее для новичков

## Выбор решения

Выбран **MkDocs-Material** — оптимален для документации.

## Процесс установки

### 1. Создание репозитория

1. Создать репозиторий: `твой-никнейм.github.io`
2. Сделать публичным

### 2. Установка MkDocs локально

```bash
pip install mkdocs-material --break-system-packages
```

### 3. Структура файлов

```
mkdocs.yml
.github/workflows/deploy.yml
docs/
├── index.md
├── about.md
└── posts/
    └── *.md
```

### 4. Настройка Git

```bash
cd /home/ubuntu/project/4
git init
git add .
git commit -m "initial commit"
```

### 5. Токен GitHub

Создать токен на https://github.com/settings/tokens:
- Отметить `repo` и `workflow`
- Скопировать токен

### 6. Первый деплой

```bash
git remote add origin https://твой-никнейм:ТОКЕН@github.com/твой-никнейм/твой-никнейм.github.io.git
git push -u origin main
```

### 7. Настройка GitHub Pages

Зайти в Settings → Pages:
- Branch: `gh-pages`
- Папка: `/(root)`

Сайт доступен: https://твой-никнейм.github.io

## Решение проблем

### Ошибка: refspec main не соответствует

Репозиторий создан с неправильным именем. Нужно переименовать в `твой-никнейм.github.io` в Settings → General → Repository name.

### Ошибка: workflow scope

Токену нужны права на `workflow`. Создать новый токен с галочками `repo` И `workflow`.

### Ошибка: Jekyll конфликтует с MkDocs

GitHub Pages по умолчанию запускает Jekyll. Решение:
- Настроить GitHub Pages читать из ветки `gh-pages`
- MkDocs делает `gh-deploy` и пушит в эту ветку

## Структура развёртывания

- **main** → исходники (mkdocs.yml, docs/)
- **gh-pages** → готовый сайт (HTML-файлы)
- MkDocs делает `gh-deploy` → пушит в `gh-pages`
- GitHub Pages читает из `gh-pages`

## Как добавить новую статью

1. Создать файл в `docs/posts/название.md`
2. Написать заголовок и контент на Markdown
3. Добавить ссылку в `docs/index.md`
4. Запушить в git:

```bash
cd /home/ubuntu/project/4
git add .
git commit -m "add: новая статья"
git push origin main
```

Сайт обновится автоматически через 1-2 минуты.

## Локальная проверка

```bash
mkdocs serve
```

Открыть http://localhost:8000

## Команды

Установка:
```bash
pip install mkdocs-material --break-system-packages
```

Локальный сервер:
```bash
mkdocs serve
```

Деплой на GitHub Pages:
```bash
mkdocs gh-deploy --force
```

## Вывод

MkDocs Material — оптимальный выбор:
- Полностью бесплатно
- Автоматический деплой
- Понятная структура
- Красивый дизайн из коробки
- Минимальная настройка
