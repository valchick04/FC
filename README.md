# ФК Сибиряк на Django

## Запуск

```bash
python3 -m pip install -r requirements.txt
python3 manage.py migrate
python3 manage.py runserver 127.0.0.1:8000
```

Сайт: http://127.0.0.1:8000/

Админ-панель: http://127.0.0.1:8000/admin/

Тестовый администратор после миграций:

- логин: `admin`
- пароль: `admin123`

## PostgreSQL

По умолчанию проект использует локальную PostgreSQL-базу `fc_sibiryak` на `127.0.0.1:5432`. Если нужно указать другое подключение, задай переменную окружения:

```bash
export DATABASE_URL="postgresql://fc_sibiryak:password@127.0.0.1:5432/fc_sibiryak"
python3 manage.py migrate
```

Перенос данных из текущего SQLite:

```bash
python3 manage.py dumpdata --natural-foreign --natural-primary --exclude contenttypes --exclude auth.permission > sqlite_data.json
export DATABASE_URL="postgresql://fc_sibiryak:password@127.0.0.1:5432/fc_sibiryak"
python3 manage.py migrate
python3 manage.py loaddata sqlite_data.json
```

Также можно вместо `DATABASE_URL` задать `POSTGRES_DB`, `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_HOST` и `POSTGRES_PORT`.

Для временного запуска на старом SQLite:

```bash
USE_SQLITE=1 python3 manage.py runserver 127.0.0.1:8000
```
