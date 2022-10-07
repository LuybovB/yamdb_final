https://github.com/LuybovB/yamdb_final/actions/workflows/yamdb_workflow.yaml/badge.svg
yamdb_final

https - ссылка на развёрнутый проект

API для сервиса YaMDb, основанный на Django REST Framework.

Сервис YaMDb это групповой итоговый проект студентов Яндекс.Практикума, который представляет собой абстрактную систему отзывов о произведениях (фильмах, книгах и музыке).

Полная Redoc-документация API доступна по ссылке.

Для локального развёртывания: docker-compose up - сборка контейнеров и запуск приложения

docker-compose exec web python manage.py makemigrations api - создание миграций

docker-compose exec web python manage.py migrate - выполнить миграции

docker-compose exec web python manage.py createsuperuser - создание суперпользователя

docker-compose exec web python manage.py collectstatic - сборка статики

