# Блог
Основные возможности:
- можно делиться статьями по электронной почте;
- комментировать чужие статьи;
- помечать статьи тегами;
- реализована карта сайта для поисковых роботов и RSS-фиды для подписок на обновления;
- настроен полнотекстовый поиск с помощью PostgreSQL.

## Установка
Эти инструкции помогут вам создать копию проекта и запустить ее на локальном компьютере для целей разработки и тестирования.

### Запуск проекта (на примере Linux)

Перед тем, как начать: если вы не пользуетесь `Python 3`, вам нужно будет установить инструмент `virtualenv` при помощи `pip install virtualenv`. 
Если вы используете `Python 3`, у вас уже должен быть модуль [venv](https://docs.python.org/3/library/venv.html), установленный в стандартной библиотеке.

- Создайте на своем компютере папку проекта blog `mkdir blog` и перейдите в нее `cd blog`
- Склонируйте этот репозиторий в текущую папку `git clone https://github.com/SergePogorelov/blog_on_the_book.git .`
- Создайте виртуальное окружение `python3 -m venv venv`
- Установите зависимости `pip install -r requirements.txt`
- Накатите миграции `python manage.py migrate`
- Создайте суперпользователя Django `python manage.py createsuperuser --username admin --email 'admin@example.com'`
- Запустите сервер разработки Django `python manage.py runserver`

## В разработке использованы

- [Python](https://www.python.org/)
- [Django](https://www.djangoproject.com/)
- [PostgreSQL](https://www.postgresql.org/)

_По книге [Антонио Меле: Django 2 в примерах](https://www.labirint.ru/books/698238/)_
