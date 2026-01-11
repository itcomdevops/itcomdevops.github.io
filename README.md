# Docs Blog

Простой блог на MkDocs Material для документации.

## Структура

```
├── mkdocs.yml          # Конфигурация
└── docs/
    ├── index.md        # Главная страница
    ├── about.md        # О блоге
    └── posts/          # Заметки
        └── *.md
```

## Добавление поста

Создайте файл в `docs/posts/название.md`:

```markdown
# Заголовок

Дата: 2024-01-10

Содержание...
```

## Запуск локально

```bash
pip install mkdocs-material
mkdocs serve
```

Откройте http://localhost:8000

## Деплой на GitHub Pages

```bash
mkdocs gh-deploy
```

---

## TODO / Планы

- [ ] Реализовать автоматическое обновление списка постов в `docs/posts/index.md`
- [ ] Настроить CI/CD для автоматического деплоя при push
