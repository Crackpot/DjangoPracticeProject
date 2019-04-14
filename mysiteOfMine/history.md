```bash
(venv)
crackpot@pc [21:19:51] [~/IdeaProjects/DjangoPracticeProject] [master *]
-> % django-admin startproject mysiteOfMine
```
####################################################################################################
```bash
(venv)
crackpot@pc [21:42:28] [~/IdeaProjects/DjangoPracticeProject/mysiteOfMine] [master *]
-> % python manage.py startapp blog
```
####################################################################################################
```bash
(venv)
crackpot@pc [21:54:39] [~/IdeaProjects/DjangoPracticeProject/mysiteOfMine] [master *]
-> % python manage.py makemigrations
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model BlogArticles
```
####################################################################################################
```bash
(venv)
crackpot@pc [21:57:33] [~/IdeaProjects/DjangoPracticeProject/mysiteOfMine] [master *]
-> % python manage.py sqlmigrate blog 0001
BEGIN;
--
-- Create model BlogArticles
--
CREATE TABLE "blog_blogarticles" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "title" varchar(300) NOT NULL, "body" text NOT NULL, "publish" datetime NOT NULL, "author_id" integer NOT NULL REFERENCES "auth_user" ("id"));
CREATE INDEX "blog_blogarticles_author_id_ed798e23" ON "blog_blogarticles" ("author_id");
COMMIT;
```
####################################################################################################
```bash
(venv)
crackpot@pc [22:08:44] [~/IdeaProjects/DjangoPracticeProject/mysiteOfMine] [master *]
-> % python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, blog, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying blog.0001_initial... OK
  Applying sessions.0001_initial... OK
```
####################################################################################################
```bash
(venv)
crackpot@pc [22:23:21] [~/IdeaProjects/DjangoPracticeProject/mysiteOfMine] [master *]
-> % python manage.py createsuperuser
Username (leave blank to use 'crackpot'):
Email address: gaofeitop@163.com
Password: crackpot
Password (again): crackpot
Superuser created successfully.
```
####################################################################################################
```bash
(venv)
crackpot@pc [22:45:35] [~/IdeaProjects/DjangoPracticeProject/mysiteOfMine] [master *]
-> % python manage.py shell
Python 3.5.2 (default, Nov 12 2018, 13:43:14)
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from django.contrib.auth.models import User
>>> from blog.models import BlogArticles
>>> user = User.objects.get(username='crackpot')
>>> user.username
'crackpot'
>>> user.id
1
>>> user.password
'pbkdf2_sha256$36000$ZO9UW2fupnQN$vDn0NqCyQTz+d+NNRiNNxVAP+N/OcpiTypnVa1hJZbI='
>>> user.email
'gaofeitop@163.com'
>>> type(user)
<class 'django.contrib.auth.models.User'>
>>>
>>> blogs = BlogArticles.objects.all()
>>> blogs
<QuerySet [<BlogArticles: You Raise Me Up>]>
>>> for blog in blogs:
...     print(blog.title)
...
You Raise Me Up
>>>
```
####################################################################################################
