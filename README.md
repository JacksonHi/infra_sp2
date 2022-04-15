# Проект api_yamdb + Docker

```
API социальной сети с отзывами на фильмы, книги и музыку.
Здесь вы можете зарегистрироваться, чтобы поделиться своим мнением о понравившемся или раздражающем произведении,
а ваши друзья смогут прочитать ваш отзыв и оставить к нему комментарии.
Также вы можете почитать отзывы об интересующем вас произведении и обсудить их в комментариях с другими пользователями.
Для вежливых граммар-наци есть возможность стать модераторами, чтобы поддерживать чистоту и взаимоуважение на платформе.
```

## Разработчики:

```
https://github.com/Drvmnekta
Пользователи и аутентификация
```

```
https://github.com/JacksonHi
Отзывы и комментарии
```

```
https://github.com/avb15214yp
Произведения и категории
```

## Технологии:
- Python 3.9
- Django 2.2.16
- Django REST framework 3.12.4
- djangorestframework-simplejwt 5.0.0
- python-dotenv 0.19.2
- Docker
- Nginx
- Postgres


## Заполнение .env файла
В директории infra_sp2/infra/ создайте .env файл и укажите значения для переменных окружения:

- SECRET_KEY
- SERVERNAMES
- DB_ENGINE
- DB_NAME
- POSTGRES_USER
- POSTGRES_PASSWORD
- DB_HOST
- DB_PORT


## Как запустить проект:

### Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:JacksonHi/infra_sp2.git
```

```
cd api_yamdb/
```

### Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv 
```

```
. venv/bin/activate
```

```
python3 -m pip install --upgrade pip
```

### Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

### Запустить приложение в контейнерах:
из директории infra/

```
docker-compose up -d --build
```

### Выполнить миграции:
из директории infra/

```
docker-compose exec web python manage.py migrate
```

### Создать суперпользователя:
из директории infra/

```
docker-compose exec web python manage.py createsuperuser
```

### Собрать статику:
из директории infra/

```
docker-compose exec web python manage.py collectstatic --no-input
```

## Заполнить базу данных:

```
python3 manage.py shell

>>> from django.contrib.contenttypes.models import ContentType
>>> ContentType.objects.all().delete()
>>> quit()

python manage.py loaddata data.json
```


## Инстркция по пользованию API:

```
http://localhost/redoc/
```

## Админка:

```
http://localhost/admin/
```