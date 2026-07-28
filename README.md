# Alyona Larkova — Engineering Portfolio

[![Postman API checks](https://github.com/alyonalar/engineering-portfolio/actions/workflows/postman.yml/badge.svg)](https://github.com/alyonalar/engineering-portfolio/actions/workflows/postman.yml)

Здесь собраны мои Python-проекты и примеры работы с качеством: backend-сервисы, Telegram-боты, обработка документов, API-тестирование, тестовая документация и анализ логов.

Мне интересна разработка систем, в которых важно не только реализовать основной сценарий, но и продумать состояние данных, повторные запросы, ошибки внешних сервисов и восстановление после сбоев. Опыт тестирования помогает замечать такие случаи ещё на этапе проектирования.

## Проекты

| Проект | Основной фокус | Что можно посмотреть |
| --- | --- | --- |
| [Telegram Support Knowledge System](https://github.com/alyonalar/telegram-support-knowledge-system) | Telegram-поддержка и база знаний | pgvector-поиск, роли, конкурентные операции, резервное копирование |
| [Anti-Leak Education Platform](https://github.com/alyonalar/anti-leak-education-platform) | Персонализированная выдача документов | фоновые задачи, DOCX-маркеры, OCR и атрибуция утечек |
| [Document Intelligence Platform](https://github.com/alyonalar/document-intelligence-platform) | Локальный анализ документов | извлечение данных, поиск, сравнение, QA и экспорт |

Документация Python-проектов написана на английском. QA-материалы и резюме представлены на русском.

## Python backend

### [Telegram Support Knowledge System](https://github.com/alyonalar/telegram-support-knowledge-system)

Telegram-бот для поддержки учебного сообщества. Ищет ответы в базе знаний конкретного чата, передаёт неизвестные вопросы администраторам и сохраняет подтверждённые ответы для дальнейшего использования.

**Стек:** Python 3.12, FastAPI, aiogram, PostgreSQL, pgvector, SQLAlchemy, Alembic, Redis, Celery, Docker Compose, pytest.

В проекте реализованы разграничение доступа между чатами, семантический поиск, версионирование базы знаний, обработка конкурентных действий администраторов, сбор обратной связи и резервное копирование.

### [Anti-Leak Education Platform](https://github.com/alyonalar/anti-leak-education-platform)

Сервис для персонализированной выдачи учебных материалов через Telegram и последующего анализа возможных утечек. Для каждого получателя создаётся индивидуальная копия DOCX с водяным знаком и текстовыми маркерами.

**Стек:** FastAPI, Celery, Redis, PostgreSQL, SQLAlchemy, Alembic, aiogram, Google Drive API, python-docx, Tesseract OCR, Docker Compose, pytest.

Проект включает идемпотентную выдачу материалов, фоновые задачи с повторными попытками, хранение карт изменений и атрибуцию по DOCX, PDF, тексту или изображениям. Результат анализа содержит найденные признаки и уровень уверенности, а не только итоговое совпадение.

### [Document Intelligence Platform](https://github.com/alyonalar/document-intelligence-platform)

Локальная платформа для загрузки, чтения, поиска, сравнения и извлечения структурированных данных из документов. Поддерживает TXT, Markdown, DOCX, PDF и сканы; основные сценарии доступны без подключения внешнего AI-сервиса.

**Стек:** FastAPI, SQLModel, SQLite, Alembic, Jinja2, ChromaDB, Tesseract OCR, Docker, pytest, Ruff.

В проекте есть обработка документов, извлечение сущностей и связей, поиск обязательств и рисков, экспорт результатов, очереди задач, повторные попытки и восстановление зависших заданий. Отдельно оформлены архитектурные решения, регрессионные тесты и [баг-репорты](https://github.com/alyonalar/document-intelligence-platform/blob/main/docs/BUG_REPORTS_RU.md).

## QA-практика

### Telegram quiz bot

Кейс построен вокруг собственного Telegram-бота, который принимает `.docx` с вопросами и проводит тестирование. Персональные данные в примерах удалены.

- [Чек-лист](qa/telegram-bot/checklist.md) — функциональные и негативные проверки.
- [Тест-кейсы](qa/telegram-bot/test-cases.md) — основные пользовательские сценарии и тестовые данные.
- [Баг-репорты](qa/telegram-bot/test-findings.md) — обнаруженные проблемы, шаги воспроизведения и ожидаемое поведение.
- [Анализ логов](qa/telegram-bot/log-analysis/analysis.md) — разбор загрузки файла, прохождения квиза и внешнего сетевого сбоя.

### API testing

[Postman-коллекция](qa/api-testing/postman_collection.json) для JSONPlaceholder выполняет связанный сценарий: фильтрует записи пользователя, сохраняет выбранный `post_id`, проверяет чтение, создание, частичное обновление, удаление и запрос отсутствующего ресурса. Коллекцию можно импортировать и запустить без ручной настройки окружения.

[Инструкция по запуску](qa/api-testing/README.md)

## Структура репозитория

```text
qa/
├── api-testing/
│   ├── README.md
│   └── postman_collection.json
└── telegram-bot/
    ├── checklist.md
    ├── test-cases.md
    ├── test-findings.md
    └── log-analysis/
        ├── README.md
        ├── analysis.md
        └── sanitized-log-sample.log
```

## Резюме

- [Резюме и контакты в профиле GitHub](https://github.com/alyonalar/alyonalar#резюме)
