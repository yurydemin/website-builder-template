# Backlog: Backend for Contact Forms

## Статус: Не реализовано
## Приоритет: Средний

## Контекст
В текущем шаблоне формы обратной связи отключены (constraints.no_forms: true).
Контактный раздел использует только статичные данные (email, телефон, Telegram).

## Когда активировать
Если проект требует сбора заявок через сайт.

## Варианты реализации

### 1. Сторонний сервис (рекомендуется для простых кейсов)
- **Formspree**: POST на endpoint, email-уведомления
- **Getform**: аналогично
- **Telegram Bot API**: webhook в чат
- **Плюс**: ноль кода, ноль деплоя
- **Минус**: зависимость от внешнего сервиса

### 2. Serverless Function
- **Vercel Functions** или **Netlify Functions**
- Runtime: Node.js / Go / Python
- Логика: приём POST, валидация, отправка email (SendGrid/AWS SES) + Telegram
- **Плюс**: полный контроль, кастомная логика
- **Минус**: привязка к хостингу

### 3. Самописный микросервис
- Отдельный контейнер (Go/Gin, Python/FastAPI, Node/Express)
- БД: PostgreSQL для хранения заявок
- Админка для просмотра
- Rate limiting, reCAPTCHA, антиспам
- **Плюс**: максимальный контроль
- **Минус**: overkill для одной формы

## Архитектура для шаблона (когда будет реализовано)

```yaml
forms:
  enabled: true
  provider: serverless      # third_party | serverless | self_hosted
  third_party:
    service: formspree
    endpoint: https://formspree.io/f/XXXXXX
  serverless:
    platform: vercel
    runtime: nodejs
    notification: email
  self_hosted:
    runtime: go
    database: postgres
    admin_panel: false
```

## Скилл для реализации
`backend-form-handler` — опциональный агент в пайплайне.

## Безопасность
- reCAPTCHA v3 (invisible)
- Honeypot field
- Rate limiting
- CORS на serverless
- Никаких API-ключей в статике (endpoint URL без ключей, ключи в env)
