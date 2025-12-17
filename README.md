# StaticJinjaPlus_port

Этот репозиторий содержит Docker-порт проекта [StaticJinjaPlus](https://github.com/MrDave/StaticJinjaPlus)

Порт позволяет собирать Docker-образы StaticJinjaPlus без копирования исходного кода в репозиторий, с возможностью выбора версии приложения и базового образа.

##  Что находится в репозитории
Репозиторий содержит только файлы для сборки Docker-образов:

```
├── Dockerfile.ubuntu     # Образы Ubuntu
├── Dockerfile.slim       # Образы python-slim
├── README.md
├── LICENSE
├── .gitignore
```

### Поддерживаемые образы и теги:

| Тег | Базовый образ|
|-----|-----|
| 0.1.0 | ubuntu |
| 0.1.1 | ubuntu |
| 0.1.0-slim | python-slim |
| 0.1.1-slim | python-slim |
| develop | ubuntu |
| develop-slim | python-slim |
| latest | ubuntu |
| slim | python-slim |

- Что означают теги
  - 0.1.0, 0.1.1 — конкретные релизы StaticJinjaPlus
  - develop — сборка из последнего коммита 
  - slim — облегчённые образы на базе python-slim
  - latest — последний стабильный релиз
 
### Используемые технологии
 1. Docker
 2. Python 3.10
 3. StaticJinjaPlus
 4. Jinja2

## Сборка образов
Пример: сборка версии 0.1.1 (Ubuntu)
```bash
docker build \
  -f Dockerfile.ubuntu \
  --build-arg VERSION=0.1.1 \
  --build-arg ARCHIVE_NAME=0.1.1.tar.gz \
  --build-arg ARCHIVE_SHA256=<SHA256_ХЭШ> \
  -t static-jinja-plus:0.1.1 \
  .
```

Пример: сборка develop-slim
```bash
docker build \
  -f Dockerfile.slim \
  --build-arg VERSION=<COMMIT_SHA> \
  --build-arg ARCHIVE_NAME=<COMMIT_SHA>.tar.gz \
  --build-arg ARCHIVE_SHA256=<SHA256_ХЭШ> \
  -t static-jinja-plus:develop-slim \
  .
```

## Запуск контейнера
Пример: static-jinja-plus:latest
```bash
docker run --rm static-jinja-plus:latest
```
