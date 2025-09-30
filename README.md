## CI/CD (GitHub Actions + GHCR + Telegram)

**О проекте**

Сайт барбершопа для записи на услуги.

**Триггеры**
- Push в любую ветку (`src/**`, `pom.xml`, `Dockerfile`, `.github/workflows/**`)
- Pull Request (та же фильтрация; без публикации образа)
- Теги `v*` (релизные сборки)
- Расписание: ежедневно 00:00 UTC
- Ручной запуск: `workflow_dispatch`

**Артефакты и результаты**
- JAR-артефакт в ранe `build-test`
- Контейнерные образы в GHCR: `ghcr.io/<owner>/<repo>:<tag>`
    - `latest` (только дефолтная ветка)
    - `<branch>`
    - `<branch>-<short_sha>`
    - `X.Y.Z` по git-тегу `vX.Y.Z`
- Telegram-уведомления о статусе (успех/ошибка)

**Секреты**
- `TELEGRAM_TOKEN`, `TELEGRAM_CHAT_ID` — для уведомлений

**Подтянуть собранный образ и запустить**
```bash
docker pull ghcr.io/user30102020/devops-42-practice:0.1.0
docker run -p 8080:8080 ghcr.io/user30102020/devops-42-practice:0.1.0
