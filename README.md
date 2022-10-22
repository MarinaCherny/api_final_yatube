## Проект «API для Yatube» :sunglasses:

Функциональ данного проекта позволяет пользователям публиковать свои посты и управлять подписками через программный интерфейс взаимодействия.

### Реализованы возможности

- Получение, создание, обновление, удаление публикаций.
- Получение, создание, обновление, удаление комментариев к публикациям.
- Просмотр сообществ и детальной информации о них.
- Отслеживание подписок на авторов, а так же возможность подписки на интересующего автора поста.
- Получение, обновление и проверка JWT авторизации.

### Технологии

- [Python](https://www.python.org/) - язык программирования.
- [Django REST Framework](https://www.django-rest-framework.org/) - мощный и гибкий набор инструментов для создания веб-API.
- [Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/) - плагин аутентификации JSON Web Token для Django REST Framework.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

`git clone https://github.com/MarinaCherny/api_final_yatube.git`

`cd api_final_yatube`


Создать и активировать виртуальное окружение:

+ `python3 -m venv venv`
+ `source env/bin/activate`
+ `python -m pip install --upgrade pip`

Установить зависимости из файла requirements.txt:
`pip install -r requirements.txt`

Выполнить миграции:
`python manage.py migrate`


Запустить проект:
`python manage.py runserver`
#### После запуска проекта, документация будет доступна по адресу:
`http://localhost:port/redoc/`

#### Примеры запросов:
:monocle_face:

POST-запрос с токеном, добавление новой публикации в коллекцию публикаций.

`POST http://localhost:port/api/v1/posts/`

```
{
  "text": "И внял я неба содраганье",
  "group": 1
}
```

Ответ:

```
{
    "id": 9,
    "author": "user1",
    "text": "И внял я неба содраганье",
    "pub_date": "2022-01-22T02:37:44.494905Z",
    "image": null,
    "group": 1
}
```


GET-запрос, получение информации о сообществе по id=2.

`GET http://localhost:port/api/v1/groups/2/`

Ответ:

```
{
    "id": 2,
    "title": "group2",
    "slug": "group2",
    "description": "group2"
}
```

POST-запрос, подписка авторизованного пользователя `user=user1` от имени которого сделан запрос на автора интересующей публикации `following=admin`.

`POST http://localhost:port/api/v1/follow/`

```
{
  "following": "admin"
}
```

Ответ:

```
{
    "id": 6,
    "user": "user1",
    "following": "admin"
}
```
:wave:
