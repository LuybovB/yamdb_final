![workflow](https://github.com/LuybovB/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
[![workflow](https://github.com/LuybovB/yamdb_final/actions/workflows/yamdb_workflow/badge.svg)]


# Проект «YaMDb»

## Описание проекта:
Проект YaMDb собирает отзывы пользователей на произведения, которые, в свою очередь, делятся на категории: «Книги», «Фильмы», «Музыка» и тд.
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

## Техническое описание проекта YaMDb
Принципы REST API.
Формат передачи данных - JSON.
Framework - Django, Django REST Framework.
JWT - Simple JWT.
DataBase - SQLite3.
Пакет datetime.
Модуль Requests.
Docker, docker-compose.
Gunicorn.
Nginx.
Наполнение базы тестовыми данными из CSV файлов.
Передача данных осуществляется по протоколу HTTP.  
Аутентификация осуществляется по JWT-токену.


### Процесс регистрации новых пользователей:
1. Пользователь отправляет запрос с параметрами *email* и *username* на **/api/v1/auth/signup/**.  
2. Сервис YaMDB отправляет письмо с кодом подтверждения (confirmation_code) на указанный email-адрес.
3. Пользователь отправляет запрос с параметрами *username* и *confirmation_code* на эндпоинт **/api/v1/auth/token/**, в ответе на запрос ему приходит *token* (JWT-токен).
После регистрации и получения токена пользователь может отправить PATCH-запрос на **/users/me/** и заполнить поля в своём профайле (описание полей — в документации). 



## Процесс установки локально:

 Клонируем репозиторий:

 ```$ git clone https://github.com/alklim912/yamdb_final.git```
 
 *Настраиваем nginx сервер на локальный:
 -в файле /infra/nginx/default.conf в параметре server_name ставим 127.0.0.1

 Запускаем docker-compose:
 
 ```$ cd infra```
 ```$ docker-compose up```
 ```$ source venv/bin/activate```
 
 Выполняем миграции, создаем админа, переносим статику в контейнере приложения:

 ```$ docker-compose exec web python manage.py migrate```
 ```$ docker-compose exec web python manage.py createsuperuser```
 ```$ docker-compose exec web python manage.py collectstatic --no-input```

