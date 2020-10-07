# Линый блог
Основные возможности:
- добавление статей через админ-панель Django;
- оформление статей разметкой `Markdown`
- можно делиться статьями по электронной почте;
- комментировать чужие статьи;
- помечать статьи тегами;
- реализована карта сайта для поисковых роботов и RSS-фиды для подписок на обновления;
- настроен полнотекстовый поиск с помощью PostgreSQL.

## Установка
Эти инструкции помогут вам создать копию проекта и запустить ее на локальном компьютере для целей разработки и тестирования.

### Установка PostgreSQL
- Перед установкой обновите индекс пакетов APT: `sudo apt update` и после этого установите необходимые для работы PostgreSQL пакеты:
```
sudo apt install postgresql postgresql-contrib -y 
```
- От имени пользователя `postgres` вызовите утилиту psql `sudo -u postgres psql` 
- Создайте базу данных с именем blog `CREATE DATABASE blog;`
- Создайте пользователя `blog_user` и дайте ему права правления базой данных:
```
CREATE USER blog_user WITH ENCRYPTED PASSWORD 'password'; 
GRANT ALL PRIVILEGES ON DATABASE blog TO blog_user;  
```
- Чтобы выйти из `psql`, выполните команду `\q`
- Если вы всё ещё работаете под пользователем `postgres`, выполните команду `exit` 

### Запуск проекта (на примере Linux)

Перед тем, как начать: если вы не пользуетесь `Python 3`, вам нужно будет установить инструмент `virtualenv` при помощи `pip install virtualenv`. 
Если вы используете `Python 3`, у вас уже должен быть модуль [venv](https://docs.python.org/3/library/venv.html), установленный в стандартной библиотеке.

- Создайте на своем компютере папку проекта blog `mkdir blog` и перейдите в нее `cd blog`
- Склонируйте этот репозиторий в текущую папку `git clone https://github.com/SergePogorelov/blog_on_the_book.git .`
- Создайте виртуальное окружение `python3 -m venv venv`
- Активируйте виртуальное окружение `source venv/bin/activate`
- Установите зависимости `pip install -r requirements.txt`
- Создайте файл `.env` (в директории с файлом `settings.py`)  командой `touch .env` и добавьте в него настройки подключения к базе данных:
```
DATABASE_URL=psql://blog_user:password@127.0.0.1:5432/blog
# поставьте тот пароль, который вы придумали для пользователя 
```
- Накатите миграции `python manage.py migrate`
- Создайте суперпользователя Django `python manage.py createsuperuser --username admin --email 'admin@example.com'`
- Запустите сервер разработки Django `python manage.py runserver`

## В разработке использованы

- [Python](https://www.python.org/)
- [Django](https://www.djangoproject.com/)
- [PostgreSQL](https://www.postgresql.org/)

_По книге [Антонио Меле: Django 2 в примерах](https://dmkpress.com/catalog/computer/programming/python/978-5-97060-746-6/)_
