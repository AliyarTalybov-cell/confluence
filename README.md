# Confluence в Docker

Локальный тестовый запуск Confluence 8.5.19 и PostgreSQL 15. Нужны Docker и Docker Compose.

## Запуск

```sh
git clone https://github.com/AliyarTalybov-cell/confluence.git
cd confluence
cp .env.example .env
```

Откройте `.env` и задайте пароль `POSTGRES_PASSWORD`. Затем загрузите образы и запустите контейнеры:

```sh
docker compose pull
docker compose up -d
```

Откройте http://localhost:8090. При первоначальной настройке выберите PostgreSQL и укажите:

| Параметр | Значение |
| --- | --- |
| Сервер | `postgres` |
| Порт | `5432` |
| База | `confluence` |
| Пользователь | `confluence` |
| Пароль | значение `POSTGRES_PASSWORD` из `.env` |

## Управление

```sh
docker compose ps
docker compose logs -f confluence
docker compose stop
docker compose start
```

Данные Confluence и PostgreSQL сохраняются в Docker-томах и не входят в репозиторий. Перед переносом сделайте резервные копии базы и тома Confluence. В конфигурации порт Confluence доступен только на локальном компьютере.

Используется сторонний образ haxqer с Java-агентом. Для работы требуется подходящая лицензия Atlassian. Инструкция адаптирована из [haxqer/confluence на Docker Hub](https://hub.docker.com/r/haxqer/confluence) под PostgreSQL и конфигурацию этого репозитория. Другие версии образа доступны в [списке тегов](https://hub.docker.com/r/haxqer/confluence/tags).
