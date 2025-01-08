Микросервисы на базе FastAPI
Данный репозиторий содержит два микросервиса, реализованных на основе фреймворка FastAPI:

TODO-сервис: реализует CRUD-операции для списка задач с использованием базы данных SQLite.
Сервис сокращения URL (Short URL): позволяет создавать короткие ссылки для длинных URL-адресов, осуществлять перенаправление по коротким ссылкам и предоставляет информацию о сокращённых URL. Данные также хранятся в SQLite.
Запуск сервисов локально
Для запуска каждого сервиса локально выполните следующие шаги:

Шаг 1: Клонирование репозитория

git clone https://github.com/<ваш_репозиторий>.git
cd <папка_сервисов>

Шаг 2: Установка зависимостей
Перейдите в папку каждого сервиса и установите зависимости:


cd todo-service
pip install -r requirements.txt
Для Short URL-сервиса:

cd short-url-service
pip install -r requirements.txt

Шаг 3: Запуск сервисов

cd todo-service
uvicorn main:app --reload
Для Short URL-сервиса:

cd short-url-service
uvicorn main:app --reload

Теперь оба сервиса будут доступны по следующим адресам:

TODO-сервис: http://localhost:8000/
Short URL-сервис: http://localhost:8001/

Запуск сервисов через Docker
Шаг 1: Сборка образов
Выполните сборку Docker-образов для каждого сервиса:

cd todo-service
docker build -t <имя_образа_todo> .

cd short-url-service
docker build -t <имя_образа_shorturl> .

Шаг 2: Запуск контейнеров
После сборки образов запустите контейнеры:


docker run -d -p 8000:80 -v todo_data:/app/data <имя_образа_todo>
Для Short URL-сервиса:

docker run -d -p 8001:80 -v shorturl_data:/app/data <имя_образа_shorturl>

Теперь оба сервиса будут доступны по тем же адресам, что и при локальном запуске:

TODO-сервис: http://localhost:8000/
Short URL-сервис: http://localhost:8001/
