### Описание 
# api_yamdb: контейниризация Docker'ом 
Учебный проект по контейнеризации API для сервиса о произведениях искусства. 
3 контейнера: для веб-приложения на Django, БД на PostgreSQL, сервер на nginx

 
### Технологии 

- Python 3.9 
- Django 2.2 
- gunicorn
- Docker
- nginx
- postgreSQL
- psycopg2-binary

### Запуск 

- Установите docker 
- в директории /infra создайте .env с 
- Из директории infra/ запустите docker-compose up -d --build 
- После успешной сборки запустите по очереди команды: 
    docker-compose exec web python manage.py migrate
    docker-compose exec web python manage.py createsuperuser
    docker-compose exec web python manage.py collectstatic --no-input 
- Теперь проект доступен по адресу http://localhost/
 

### Примеры запросов к API Yambd 

Регистрация на сервисе:  

``` 

http://127.0.0.1:8000/api/v1/auth/singup/ 

``` 

Получение токена:  

``` 

http://127.0.0.1:8000/api/v1/auth/token/ 

``` 

Получение данных через GET-запросы:  

 

- о категориях 

``` 

1. http://127.0.0.1:8000/api/v1/categories/ 

``` 

- о жанрах 

``` 

1. http://127.0.0.1:8000/api/v1/genres/ 

2. http://127.0.0.1:8000/api/v1/genres/{slug}/ 

``` 

- о произведениях 

``` 

1. http://127.0.0.1:8000/api/v1/titles/ 

2. http://127.0.0.1:8000/api/v1/titles/{titles_id}/ 

``` 

- об отзывах на произведениям 

``` 

1. http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/ 

2. http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/ 

``` 

- о комментариях к отзывам 

``` 

1. http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/ 

2. http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/ 

``` 

Так же через POST, PUT, PATCH и DELETE-запросы к перечисленным  

эндпоинтам возможно редактирование данных. 

 

Полная документация с определением прав доступа ко всем эндпоинтам  

проекта, примерами содержания запросов и ответов доступна при запущеном  

проекте по адресу:  

``` 

http://127.0.0.1:8000/redoc/ 

``` 
