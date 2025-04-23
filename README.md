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

## Настройка интеграции с GitHub Actions

1. В SonarQube создайте новый проект:
   - Перейдите в Administration -> Projects -> Management
   - Создайте новый проект
   - Получите токен доступа (Administration -> Security -> Users -> Tokens)

2. В GitHub репозитории:
   - Перейдите в Settings -> Secrets and variables -> Actions
   - Создайте новый секрет с именем `SONAR_TOKEN` и значением токена из SonarQube

3. В файле `.github/workflows/sonarqube.yml`:
   - Замените `your-project-key` на ключ вашего проекта в SonarQube
   - Убедитесь, что `SONAR_HOST_URL` указывает на правильный адрес вашего SonarQube

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
- Контейнеры автоматически перезапускаются при сбоях (restart: unless-stopped)
- Для работы с GitHub Actions убедитесь, что SonarQube доступен из интернета

sonar \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.token=sqp_8e3ae896cd5cc896b590ede2bd6789935362ca82