# yamdb_final
# IP 178.154.247.251
![example workflow](https://github.com/chaandrey/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Описание. 


Проект позволяет зарегистрированным пользователям создавать посты, редактировать их и удалят.
Также существует возможность комментировать чужые посты и подписываться на обновления других авторов.
Анонимные пользователи имеют возможность читать посты и их комментарии.


Установка.


Для того чтобы развернуть проект, следуйте инструкции:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone [https://github.com/chaandrey/api_final_yatube]
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```



Примеры.

Для того чтобы получить доступ к полному функционалу , пользователь должен зарегестрироваться и получить JWT токен:

```
POST /api/v1/jwt/create/
```
BODY:
```
{
  "username": "username",
  "password": "password"
}
```

Зарегистрированный пользователь может создавать новые посты:

```
POST /api/v1/posts/
```
BODY:
```
{
  "text": "Post text"
}
```
Редактировать / удалять уже существующие посты ( автор поста должен быть тот же пользователь , кто редактирует/удаляет):

```
DELETE /api/v1/posts/1/
```
BODY:
```
{
  "id": "Post id"
}
```


Добавлять комментарии:

```
POST /api/v1/posts/1/comments/
```
BODY:
```
{
  "test": "New Comment"
}
```

Подписаться на другого пользователя
```
POST /api/v1/follow/
```
BODY:
```
{
  "following": "author"
}
```



Анонимный пользователь имеет только read only права.


Запрос всех постов :

```
GET /api/v1/posts/
```


Запрос поста по его id.

```
GET /api/v1/posts/1
```


Запрос комментариев

```
GET /api/v1/posts/1/comments/
```
