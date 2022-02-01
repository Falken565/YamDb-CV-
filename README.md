# YaMDb - учебный проетк по API

Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором.

Проект групповой, выполнялся несколькими студентами (каждый делал свою часть), взаимодействие осуществялось через GitHub (разработка каждой части в отдельной ветви, затем объединение в master)

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:Falken565/YaMDB.git
```

```
cd YamDb-CV-
```

Cоздать файл с переменными окружения .env:

```
# блок отправки сообщений на почту
EMAIL_HOST=<post host>
EMAIL_HOST_USER=<email address>
EMAIL_HOST_PASSWORD=<email password>
EMAIL_PORT=587

# блок базы данных
DB_ENGINE=django.db.backends.postgresql_psycopg2 # указываем бд, с которой работаем
POSTGRES_DB=yamdb_db # имя бд 
POSTGRES_USER=vasya666 # логин для подключения к бд (укажите свой)
POSTGRES_PASSWORD=123321 # пароль для подключения к бд (укажите свой)
DB_HOST=db # название контейнера
DB_PORT=5432 # порт для подключения к БД

# секретики для settings.py
SECRET_KEY=<super-secret-key>
```

Запуск приложения в контейнерах:

```
docker-compose up -d --build
```

Выполнить миграции:

```
docker-compose exec web python manage.py migrate --noinput
```

Создаем пользователя:

```
docker-compose exec web python manage.py createsuperuser
```

Собираем статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

### Как взаимодействовать с проектом:

Через админку:
логинемся на локальный сервер (http://127.0.0.1/admin) под суперюзером и создаем объекты жанров, категорий и тд 

По API:
заходим на http://127.0.0.1/redoc , где предстваленна документация с примерами запросов по API

