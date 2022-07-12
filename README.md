[![Django-app workflow](https://github.com/AlanSosnovsky/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/AlanSosnovsky/yamdb_final/actions/workflows/yamdb_workflow.yml)

# yamdb_final
yamdb_final
# api_yamdb

### О проекте

Данный проект является учебным.
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории (Category): «Книги», «Фильмы», «Музыка».
Сами произведения в YaMDb не хранятся.
Произведению может быть присвоен жанр (Genre).
Пользователи YaMDb оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число).

### Как запустить проект.

Предполагается, что установлен docker и docker-compose.
Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/AlanSosnovsky/yamdb_final.git
```

```
cd yamdb_final/infra/
```

Cоздать и заполнить файл .env:

```
SECRET_KEY=<секретный ключ Django>
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=password #укажите свой
DB_HOST=db
DB_PORT=5432
```

Cоздать и активировать контейнеры:

```
docker-compose up -d --build
```

Выполните по очереди команды:

```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input 
```

Теперь проект доступен по адресу _http://localhost/_ 

### Как делать запросы:

К проекту по адресу .../redoc/ подключена документация redoc, содержащая сведения по доступным эндпоинтам и примеры запросов.


### Импорт внешних данных в проект:

При необходимости импортировать внешние данные, в проекте реализована команда csv_sql для  заполнения таблиц БД из .csv файлов. Синтаксис команды:

```
python manage.py csv_sql <файл .csv> <название модели>
```



### Под руководством команды Яндекс-Практикума над проектом работали:

- Васильев Кирилл - Разработчик
- Ежов Михаил - Разработчик
- Сосновский Александр - Разработчик
- Тихонов Станислав - Разработчик / Тимлид

### В docker-compose упаковал, написал workflow:

- Сосновский Александр
