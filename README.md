# fastapi_hw
# TODO Service

## Запуск локально
1. Установите зависимости:
pip install -r requirements.txt

3. Запустите сервер:
uvicorn main:app --reload

3. Приложение будет доступно на `http://127.0.0.1:8000/docs`.

## Запуск через Docker
1. Соберите Docker-образ:
docker build -t todo-app .

2. Запустите контейнер:
docker run -d -p 8000:80 -v todo_data:/app/data todo-app
