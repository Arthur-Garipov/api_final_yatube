# Описание
Яндекс Практикум. Спринт 9. Итоговый проект. API для Yatube.

# Функционал
- Подписка и отписка от авторизованного пользователя;
- Авторизованный пользователь просматривает посты, создавёт новые, удаляет и изменяет их;
- Просмотр сообществ;
- Комментирование, просмотр, удаление и обновление комментариев;
- Фильтрация по полям.
# Установка
_1. Клонировать репозиторий:_
```
git clone https://github.com/Arthur-Garipov/api_final_yatube.git
```
_2. Перейти в папку с проектом:_
```
cd api_final_yatube/
```
_3. Установить виртуальное окружение для проекта:_
```
python -m venv venv
```
_4. Активировать виртуальное окружение для проекта:_

# для OS Lunix и MacOS
```
source venv/bin/activate
```
# для OS Windows
```
source venv/Scripts/activate
```
_5. Установить зависимости:_
```
python -m pip install --upgrade pip
pip install -r requirements.txt
```
_6. Выполнить миграции на уровне проекта:_
```
cd yatube
python3 manage.py makemigrations
python3 manage.py migrate
```
_7. Запустить проект:_
```
python manage.py runserver
```
# Примеры запросов
_1. Получение токена_

Отправить POST-запрос на адрес api/v1/jwt/create/ и передать 2 поля в data:

**username** - имя пользователя.
**password** - пароль пользователя.

_2. Создание поста_

Отправить POST-запрос на адрес api/v1/posts/ и передать обязательное поле text, в заголовке указать **Authorization:Bearer** <токен>.

Пример запроса:
```
{
    "text": "string",
    "image": "string",
    "group": 0
}
```
Пример ответа:
```
{
    "id": 0,
    "author": "Arthur",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}
```
_3. Комментирование поста пользователя_

Отправить POST-запрос на адрес api/v1/posts/{post_id}/comments/ и передать обязательные поля post и text, в заголовке указать Authorization:Bearer <токен>.

Пример запроса:
```
{
    "post": 1,
    "text": "Тест"
}
```
Пример ответа:
```
{
    "id": 0,
    "author": "Arthur",
    "text": "Тест",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
}
```
