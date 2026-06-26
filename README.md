# Website Builder Template

Универсальный шаблон для создания landing page и корпоративных сайтов через Claude Code с использованием мульти-агентного пайплайна.

## Быстрый старт

```bash
# 1. Клонируйте репозиторий
git clone https://github.com/yurydemin/website-builder-template.git
cd website-builder-template

# 2. Заполните конфигурацию
# Откройте config/PROJECT_CONFIG.yaml и заполните все поля

# 3. Заполните брифы
# docs/brief/company-info.md
# docs/brief/brand-constraints.md
# docs/brief/product-descriptions.md

# 4. Установите скиллы в Claude Code
mkdir -p ~/.claude/skills
cp -r .claude/skills/* ~/.claude/skills/

# 5. Запустите пайплайн
# Следуйте инструкциям в .claude/commands/build-website.md
```

## Что входит в шаблон

- **Пайплайн из 9 шагов**: Research → Brief → Copy + Design → Verify → Build → Test → SEO/GEO → Report
- **6 скиллов Claude Code**: Orchestrator, Copywriter, Designer, Tester, SEO/GEO, Reference Analyzer
- **Библиотека блоков**: 12 типов блоков для landing/corporate сайтов
- **Multi-page архитектура**: Готовая структура src/ с чистыми URL
- **SEO-ready**: sitemap.xml, robots.txt, structured data шаблоны

## Структура проекта

```
.
├── config/
│   └── PROJECT_CONFIG.yaml          # Главный конфиг проекта
├── docs/
│   ├── brief/                         # Исходные материалы
│   │   ├── company-info.md
│   │   ├── brand-constraints.md
│   │   ├── product-descriptions.md
│   │   └── reference-analysis.md
│   └── backlog/                       # Фичи в разработке
│       ├── forms-backend.md
│       └── i18n-multilang.md
├── .claude/
│   ├── skills/                        # Скиллы для Claude Code
│   │   ├── core-orchestrator/
│   │   ├── core-copywriter/
│   │   ├── core-designer/
│   │   ├── core-tester/
│   │   ├── core-seo-geo/
│   │   └── reference-analyzer/
│   └── commands/
│       └── build-website.md           # Пошаговый промпт
├── src/                               # Исходники сайта (деплой-корень)
│   ├── index.html
│   ├── about/
│   ├── cases/
│   ├── contacts/
│   ├── privacy/
│   ├── sitemap.xml
│   ├── robots.txt
│   └── assets/
├── output/                            # Артефакты пайплайна
└── CLAUDE.md                          # Глобальный контекст
```

## Требования

- Claude Code (desktop или terminal)
- Node.js (опционально, если используете Vite для сборки)
- Хостинг: Vercel, Netlify, GitHub Pages или любой статический хостинг
