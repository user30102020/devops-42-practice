# Spring Boot + GitHub Actions + GHCR + Telegram

## Триггеры
- `push` в `main` → сборка JAR, сборка и публикация образа в GHCR, уведомление в Telegram.
- `tag` вида `v*` → релизные теги образа по семвер.
- `pull_request` → только сборка/тесты без публикации.
- `workflow_dispatch` → ручной запуск.

## Ручная сборка
```bash
mvn -B clean package
docker build -t ghcr.io/<owner>/<repo>:local .
docker run -p 8080:8080 ghcr.io/<owner>/<repo>:local
