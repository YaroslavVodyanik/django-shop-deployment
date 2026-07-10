# Django Shop Deployment

Учебный Django-проект, подготовленный для запуска в Docker. В приложении есть интернет-магазин, блог, авторизация, админ-панель, загрузка изображений, REST API и базовая Docker-настройка для публикации.

## Почему проект важен для портфолио

Проект показывает классический Django backend: модели, страницы, админ-панель, авторизацию, загрузку изображений, REST API и запуск через Docker Compose. Настройки вынесены в переменные окружения, поэтому проект выглядит аккуратно для GitHub и безопаснее для публичного репозитория.

## Стек

- Python 3.11
- Django 4.2
- Django REST Framework
- django-filter
- django-debug-toolbar
- Pillow
- Poetry
- Docker / Docker Compose
- SQLite

## Возможности

- каталог товаров;
- карточки товаров с изображениями;
- заказы;
- авторизация и регистрация пользователей;
- блог;
- sitemap;
- Django admin;
- REST API;
- запуск через Docker Compose.

## Что можно проверить

- страницу магазина;
- блог;
- авторизацию и регистрацию;
- Django admin;
- REST API;
- запуск через `.env` и Docker Compose.

## Быстрый запуск

1. Создайте `.env` из шаблона:

```powershell
copy .env.template .env
```

Linux/macOS:

```bash
cp .env.template .env
```

2. Запустите приложение:

```bash
docker compose up --build -d
```

3. Откройте приложение:

```text
http://localhost:8000
```

Полезные страницы:

- `http://localhost:8000/shop/`
- `http://localhost:8000/blog/`
- `http://localhost:8000/myauth/login/`
- `http://localhost:8000/admin/`

## Переменные окружения

Пример `.env`:

```env
DJANGO_SECRET_KEY=change-me
DJANGO_DEBUG=1
DJANGO_ALLOWED_HOSTS=localhost,127.0.0.1
DJANGO_DB_PATH=/data/db.sqlite3
APP_PORT=8000
```

Для учебного запуска `DJANGO_DEBUG=1` оставлен специально: так Django отдаёт статические и медиафайлы без отдельной настройки nginx.

## Команды разработки

Установить зависимости локально через Poetry:

```bash
poetry install
```

Запустить миграции:

```bash
python mysite/manage.py migrate
```

Создать администратора:

```bash
python mysite/manage.py createsuperuser
```

Запустить локально без Docker:

```bash
python mysite/manage.py runserver
```

## Docker

Проект использует Poetry внутри Docker-образа. Виртуальное окружение Poetry отключено:

```env
POETRY_VIRTUALENVS_CREATE=false
```

Остановить контейнеры:

```bash
docker compose down
```

Остановить и удалить volume с базой и медиа:

```bash
docker compose down -v
```

## Структура

```text
mysite/
  blogapp/     блог
  myauth/      авторизация
  shopapp/     магазин, товары, заказы, API
  mysite/      настройки проекта
Dockerfile
docker-compose.yml
pyproject.toml
```
