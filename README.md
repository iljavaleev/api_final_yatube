# Yatube API

API проект для взаимодействия с социальной сетью Yatube, в которой можно 
публиковать посты в одной из категорий сайта, оформлять подписки на авторов,
создавть комментарии.

В рамках Yatube API доступ к информации ограничен в зависимости от того, 
аутентифицирован ли пользователь и является ли он автором поста.

Аутентификация пользователя происходит по JWT токену. 

Документация доступна по адресу http://localhost:8000/schema/redoc/ и 
http://localhost:8000/schema/swagger-ui/

## Установка проекта

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/iljavaleev/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```
```
source venv/bin/activate
```
Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект локально на http://127.0.0.1:8000/:

```
python3 manage.py runserver
```

## Примеры

Получение информации о посте:
```
url = 'http://127.0.0.1/api/v1/posts/{номер поста}/'
curl -G $url  
```

Ожидаемый ответ API_Yatube:
```
Response 200

{
    "id": 0,
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "author": "string",
    "image": "http://example.com",
    "group": 0
}
```
Создание комментария к посту:
```
url = 'http://127.0.0.1:8000/api/v1/posts/{номер поста}/comments/'
content = '{"text": "string"}'
user_token = "Bearer {user_token}
curl -X POST $url -H 'Content-Type: application/json' -d $content -H "Authorization: $user_token"  
```
Ожидаемый ответ API_Yatube:
```
Response 201

{
    "id": 0,
    "author": "string",
    "post": 0,
    "text": "string",
    "created": "2019-08-24T14:15:22Z"
}
```