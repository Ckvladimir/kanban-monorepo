# Task 6

## Репозитории

- Backend and Frontend: https://gitlab.com/aston_practice_backend_frontend

## Сборка Docker-образов

### Backend

Для сборки backend-образа необходимо перейти в директорию backend-репозитория и выполнить команду:

```bash
cd ../demo_aston_backend
docker build -t aston-backend .
```

Команда `docker build` собирает Docker-образ из `Dockerfile`, расположенного в текущей директории.  
Тег `aston-backend` используется далее в `docker-compose.yml` для запуска backend-контейнера. [web:300][web:301]

### Frontend

Для сборки frontend-образа необходимо перейти в директорию frontend-репозитория и выполнить команду:

```bash
cd ../demo_aston_frontend
docker build -t aston-frontend .
```

Команда собирает Docker-образ frontend-приложения из `Dockerfile` в текущей директории.  
Тег `aston-frontend` используется далее при запуске frontend-контейнера через Docker Compose. [web:300][web:301]

## Запуск контейнеров через Docker Compose

Файл `docker-compose.yml` расположен в директории `task6` основного репозитория.  
Для запуска всех контейнеров нужно перейти в папку `task6` и выполнить команду:

```bash
cd task6
docker compose up
```

Команда `docker compose up` создаёт и запускает контейнеры, описанные в compose-файле.  
В данном случае запускаются три сервиса:

- `postgres` — контейнер с базой данных PostgreSQL;
- `backend` — контейнер backend-приложения Spring Boot;
- `frontend` — контейнер frontend-приложения. [web:250][web:232]

Сервис backend зависит от `postgres`, а frontend зависит от backend, поэтому Compose запускает контейнеры в порядке зависимостей. При этом `depends_on` управляет порядком старта, но сам по себе не гарантирует полную готовность приложения внутри контейнера. [web:232][web:309]

После запуска приложение должно быть доступно по адресам:

- Frontend: http://localhost:8080
- Backend: http://localhost:8081 [web:317]
