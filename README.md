Аналог Quotes to Scrape на django
http://quotes.toscrape.com/

1. Cтворимо віртуальне оточення poetry та проект Django
> poetry add Django
> poetry run django-admin startproject quotes_scrape

2. Створюємо суперкористувача
> docker run --name hw-djangoapp-postgres -p 5432:5432 -e POSTGRES_PASSWORD=751953 -d postgres
ca44654bf96660344301c3e400b007952f97f974cae4a441c32d19b81bde5bcf
settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': '751953',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
> poetry add psycopg2
> python manage.py migrate
> python manage.py createsuperuser
Console:
    Username (leave blank to use 'dell061019'):
    Email address: anatolii.perfilov@gmail.com
    Password: 123456
    Password (again): 123456
    Bypass password validation and create user anyway? [y/N]: y

3. Запуск застосунку
> poetry run python manage.py runserver
localhost:8000
http://127.0.0.1:8000/admin

4. Створення застосунку qtsapp
> poetry run python manage.py startapp qtsapp
settings.py
INSTALLED_APPS -> qtsapp
qtsapp/models.py
> poetry run python manage.py makemigrations
> poetry run python manage.py migrate
qtsapp/admin.py

5. Додавання головної сторінки
quotes_scrape/qtsapp/templates/qtsapp/index.html
qtsapp/views.py
quotes_scrape/urls.py

6. Створення base.html та style.css
quotes_scrape/qtsapp/templates/qtsapp/base.html
settings.py
STATIC_URL -> "static/"
quotes_scrape/qtsapp/static/qtsapp/style.css

7. Додавання автора
quotes_scrape/qtsapp/templates/qtsapp/author.html
quotes_scrape/qtsapp/forms.py
quotes_scrape/qtsapp/views.py
quotes_scrape/qtsapp/urls.py

8. Додавання цитат
quotes_scrape/qtsapp/templates/qtsapp/quote.html
quotes_scrape/qtsapp/forms.py
quotes_scrape/qtsapp/views.py -> def quote()


9. Сторінка відображення цитати
quotes_scrape/qtsapp/views.py -> def detail()
quotes_scrape/qtsapp/urls.py
quotes_scrape/qtsapp/templates/qtsapp/detail.html

10. Відображення списку цитат
quotes_scrape/qtsapp/views.py -> def main()
quotes_scrape/qtsapp/templates/qtsapp/index.html

11. Відображення сторінки авторів
quotes_scrape/qtsapp/views.py -> def about_author()
quotes_scrape/qtsapp/urls.py
quotes_scrape/qtsapp/templates/qtsapp/about_author.html

12. Додавання користувачів
> poetry run python manage.py startapp users
settings.py INSTALLED_APPS -> users
quotes_scrape/urls.py -> path('admin/', admin.site.urls),
quotes_scrape/users/forms.py
quotes_scrape/users/views.py -> signupuser
quotes_scrape/users/templates/users/signup.html
quotes_scrape/users/urls.py

13. Аутентифікація
quotes_scrape/users/forms.py -> LoginForm
quotes_scrape/users/templates/users/login.html
quotes_scrape/users/views.py -> loginuser
quotes_scrape/users/urls.py

14. Вихід користувача
quotes_scrape/users/views.py -> logout
quotes_scrape/users/urls.py

15. Змінюємо головну сторінку
quotes_scrape/qtsapp/templates/qtsapp/index.html

Код для завантаження даних з MongoDB в Postgres
> poetry add pymongo mongoengine
quotes_scrape/utils/config.ini
quotes_scrape/mongo_postgres.py

The end

