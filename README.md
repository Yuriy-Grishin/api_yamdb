## Описание проекта 

Проект хранит отзывы пользователей на фильмы, музыку и книги. 
Пользователи могут оставлять отзывы и ставить оценку в диапазоне от одного до десяти, по результатам которых формируется рейтинг. 

## Алгоритм регистрации пользователей
Регистрация пользователей происходит через направление пользователем POST-запроса на добавление нового пользователя с параметрами email и username на эндпоинт /api/v1/auth/signup/.
Проект отправляет письмо с кодом подтверждения на адрес электронной почты, после чего пользователь отправляет POST-запрос с параметрами username и кодом подтверждения на на эндпоинт /api/v1/auth/token/, в ответе на запрос ему приходит JWT-токен. В результате пользователь получает токен и может работать с API проекта, отправляя этот токен с каждым запросом.
Пользователь может отправить PATCH-запрос на эндпоинт /api/v1/users/me/ для заполнения своего профайла. 

## Пользовательские роли
1. Аноним — может открывать и читать описания произведений, отзывы и комментарии.
2. Аутентифицированный пользователь (user) — может читать всё, дополнительно он может публиковать отзывы и ставить оценку книгам, фильмам, песням, комментировать другие отзывы, редактировать и удалять свои отзывы и комментарии. Эта роль присваивается по умолчанию каждому новому пользователю.
3. Модератор — аналогичные права, что и у Аутентифицированного пользователя, а такэе право удалять любые отзывы и комментарии.
4. Администратор  — полные права на управление всем содержимым проекта. Может создавать и удалять фильмы, музыку, книги. Может назначать роли пользователям.
5. Суперпользователь — обладает правами администратора. Даже если изменить пользовательскую роль суперпользователя это не лишит его прав администратора. 

## Ресурсы API YaMDb
Ресурс AUTH: аутентификация.

Ресурс USERS: пользователи.

Ресурс TITLES: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).

Ресурс CATEGORIES: категории (типы) произведений («Фильмы», «Книги», «Музыка»).

Ресурс GENRES: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.

Ресурс REVIEWS: отзывы на произведения. Отзыв привязан к определённому произведению.

Ресурс COMMENTS: комментарии к отзывам. Комментарий привязан к определённому отзыву.

## Стек технологий
Python;
Django;
Django REST framework;
DRF Simple JWT;

## Запуск проекта 
Сначала клонировать репозиторий и перейти в него в командной строке:
git clone https://github.com/Yuriy-Grishin/api_yamdb

Установите и активируйте виртуальное окружение
python -m venv venv
. venv/bin/activate

Установите зависимости из файла requirements.txt
pip install -r requirements.txt

В папке с файлом manage.py выполните команду:
python3 manage.py runserver
