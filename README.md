# Силант - Система учета техники

Веб-приложение для управления складской техникой, ведения истории технического обслуживания и регистрации рекламаций.

## Установка

1. Клонируйте репозиторий:
```bash
git clone <repository-url>
cd silant
```

2. Создайте виртуальное окружение:
```bash
python -m venv venv
source venv/bin/activate  # для Linux/Mac
venv\Scripts\activate     # для Windows
```

3. Установите зависимости:
```bash
pip install -r requirements.txt
```

4. Создайте файл `.env` на основе `.env.example`:
```bash
cp .env.example .env
```

5. Настройте переменные окружения в `.env`:
```
DJANGO_SECRET_KEY=your-secret-key
DEBUG=True
DATABASE_NAME=silant_db
DATABASE_USER=postgres
DATABASE_PASSWORD=your-password
DATABASE_HOST=localhost
DATABASE_PORT=5432
DJANGO_ALLOWED_HOSTS=localhost,127.0.0.1
```

6. Примените миграции:
```bash
python manage.py migrate
```

7. Создайте суперпользователя:
```bash
python manage.py createsuperuser
```

8. Загрузите тестовые данные (опционально):
```bash
python manage.py loaddata fixtures/initial_data.json
```

9. Запустите сервер:
```bash
python manage.py runserver
```

Приложение будет доступно по адресу: http://localhost:8000

## Тестовые пользователи

После загрузки тестовых данных доступны следующие учетные записи:

- **Менеджер**: `manager` / `password123`
- **Клиент**: `client` / `password123`
- **Сервисная организация**: `service` / `password123`

## API

Документация API доступна по адресам:
- Swagger: http://localhost:8000/swagger/
- ReDoc: http://localhost:8000/redoc/

### Основные эндпоинты

- `GET /api/machines/` - список машин
- `GET /api/maintenance/` - список ТО
- `GET /api/claims/` - список рекламаций
- `GET /api/search/?factory_number=XXX` - поиск машины
``

## Разработка

Для запуска в режиме разработки:

```bash
DEBUG=True python manage.py runserver
```

Для сбора статических файлов:

```bash
python manage.py collectstatic
```
