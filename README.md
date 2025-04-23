# SonarQube Docker Setup

Этот репозиторий содержит конфигурацию для запуска SonarQube с использованием Docker Compose.

## Требования

- Docker
- Docker Compose

## Запуск SonarQube

1. Запустите контейнеры в фоновом режиме:
```bash
docker-compose up -d
```

2. Проверьте статус контейнеров:
```bash
docker-compose ps
```

3. SonarQube будет доступен по адресу: http://localhost:9000

## Учетные данные по умолчанию

- Логин: `admin`
- Пароль: `admin` (при первом входе потребуется изменить)

## Остановка SonarQube

Для остановки контейнеров выполните:
```bash
docker-compose down
```

## Удаление данных

Для полного удаления всех данных (включая тома) выполните:
```bash
docker-compose down -v
```

## Примечания

- Все данные сохраняются в именованных томах Docker
- PostgreSQL база данных настроена для хранения данных SonarQube
- Контейнеры автоматически перезапускаются при сбоях (restart: unless-stopped) # sonarqube-local
