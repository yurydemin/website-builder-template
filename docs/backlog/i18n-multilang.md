# Backlog: Internationalization (i18n)

## Статус: Не реализовано
## Приоритет: Низкий

## Контекст
Текущий шаблон поддерживает один язык (config.project.language).

## Когда активировать
Если проект требует мультиязычность.

## Стратегии (для обсуждения)

### 1. Subpath (/en/, /ru/)
- Каждый язык — отдельная копия страниц
- SEO-friendly, canonical URLs
- Дублирование контента

### 2. Subdomain (en.example.com)
- Изоляция языков
- Сложнее деплой

### 3. Query parameter (?lang=en)
- Просто, но плохо для SEO

## Архитектура для шаблона (когда будет реализовано)

```yaml
i18n:
  enabled: true
  default: ru
  locales: [ru, en]
  strategy: subpath
```

## Влияние на пайплайн
- Copywriter пишет тексты для каждого языка
- Designer адаптирует layout под RTL (если нужно)
- SEO: hreflang tags, отдельные sitemap.xml или секции
- Структура src/:
  ```
  src/
  ├── ru/
  │   ├── index.html
  │   └── about/
  │       └── index.html
  └── en/
      ├── index.html
      └── about/
          └── index.html
  ```
