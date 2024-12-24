## Описание
Этот проект включает два микросервиса, реализованные с использованием FastAPI:
1. TODO-сервис (управление задачами).
2. Сервис сокращения URL (Short URL).

## Локальный запуск

### Установка зависимостей

1. Убедитесь, что у вас установлен Python версии 3.9 или выше.
2. Клонируйте репозиторий:
   ```bash
   git clone https://github.com/SetAblaze/fastapi_hw.git
   cd fastapi_hw
   ```
3. Установите зависимости для каждого сервиса:
   ```bash
   cd todo_app
   pip install -r requirements.txt
   cd ../shorturl_app
   pip install -r requirements.txt
   ```

### Запуск сервисов

#### TODO-сервис
1. Перейдите в директорию `todo_app`:
   ```bash
   cd todo_app
   ```
2. Запустите сервер:
   ```bash
   uvicorn main:app --reload --host 127.0.0.1 --port 8000
   ```

#### Сервис сокращения URL
1. Перейдите в директорию `shorturl_app`:
   ```bash
   cd shorturl_app
   ```
2. Запустите сервер:
   ```bash
   uvicorn main:app --reload --host 127.0.0.1 --port 8001
   ```

Оба сервиса будут доступны по следующим адресам:
- TODO-сервис: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- Сервис сокращения URL: [http://127.0.0.1:8001/docs](http://127.0.0.1:8001/docs)

---

## Запуск через Docker

### Предварительные требования
1. Убедитесь, что у вас установлен Docker.
2. Создайте именованные тома для сохранения данных:
   ```bash
   docker volume create todo_data
   docker volume create shorturl_data
   ```

### Сборка образов

#### TODO-сервис
1. Перейдите в директорию `todo_app`:
   ```bash
   cd todo_app
   ```
2. Постройте Docker-образ:
   ```bash
   docker build -t todo-app .
   ```

#### Сервис сокращения URL
1. Перейдите в директорию `shorturl_app`:
   ```bash
   cd shorturl_app
   ```
2. Постройте Docker-образ:
   ```bash
   docker build -t shorturl-app .
   ```

### Запуск контейнеров

#### TODO-сервис
```bash
docker run -d -p 8000:80 -v todo_data:/app/data todo-app
```

#### Сервис сокращения URL
```bash
docker run -d -p 8001:80 -v shorturl_data:/app/data shorturl-app
```

### Доступ к сервисам

- TODO-сервис: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- Сервис сокращения URL: [http://127.0.0.1:8001/docs](http://127.0.0.1:8001/docs)
