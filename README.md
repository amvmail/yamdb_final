# yamdb_final
yamdb_final
https://github.com/amvmail/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg
It`s commit on git status

### Установка проекта

После commit в репозиторий git, ветка main на этот сервер в результате deploy
разворачиваются 3 conteiner - nginx, infra-web, postgres из 3-х image с такими же названиями
Запуск проекта при deploy осуществляется автоматически 
Посмотреть работающие контайнеры 

```
docker container ps
```
Примерный вывод начальной части этой команды:
docker container ps
CONTAINER ID   IMAGE                     
e0920462cd75   nginx:1.21.3-alpine       
e5e72f976891   amvmail/infra-web:latest  
4c251c716c48   postgres:13.0-alpine      

При изменении файлов проекта в репозитории git происходит повторный deploy
и рестарт этого проекта на сервере

Остановка контайнера (в качестве имени контейнера применяется его ID):
```
docker container stop e5e72f976891 
```

Посмотреть все контайнеры на сервере (после останова контейнера у него изменится статус): 

```
docker container ps -a
```

Запуск контайнера (в качестве имени контейнера применяется его ID):
```
docker container start e5e72f976891


### Запросы к API

Регистрация пользователей:

```
POST-запрос на добавление нового пользователя с параметрами `email` и `username`
http://127.0.0.1:8000//api/v1/users/
```

```
POST-запрос для получения сообщения с кодом подтверждения (`confirmation_code`) с параметрами `email` и `username`
http://127.0.0.1:8000/api/v1/auth/signup/
```

```
POST-запрос с параметрами `username` и `confirmation_code`, для получения токена
http://127.0.0.1:8000/api/v1/auth/token/
```

Используемые запросы:

```
Работа с категориями. Запросы: Get, Post и Del
http://127.0.0.1:8000/api/v1/categories/
```

```
Работа с жанрами. Запросы: Get, Post и Del
http://127.0.0.1:8000/api/v1/genres/
```

```
Работа с произведениями. Запросы: Get, Post, Patch и Del
http://127.0.0.1:8000/api/v1/titles/
```

```
Работа с отзывами. Запросы: Get, Post, Patch и Del
http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/
```

```
Работа с комментариями. Запросы: Get, Post, Patch и Del
http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/{review_id}/comments/
```

```
Получение и изменение своих данных. Запросы: Get, Patch
http://127.0.0.1:8000/api/v1/users/me/
```