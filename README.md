# Дипломный проект профессии "Тестировщик"

## Документация по проекту
1. [План тестирования](https://github.com/Butanya/Diploma_QA/blob/master/Plan.md)
2. [Отчет по итогам тестирования](https://github.com/Butanya/Diploma_QA/blob/master/Report.md)
3. [Отчет по итогам автоматизации](https://github.com/Butanya/Diploma_QA/blob/master/Summary.md)

## Запуск приложения

* Для запуска приложения необходим Docker или Docker Toolbox.

* склонировать репозиторий `https://github.com/Butanya/Diploma_QA.git`

* переключиться в папку Diploma_QA

* проверить есть ли образы MySql, PostgreSQL и Node.js командой docker image ls

* скачать нужный образ командой docker image pull <имя образа>

* запустить `docker container docker-compose up -d`. Дождаться пока контейнеры запустятся

* в терминале IntelliJ IDEA запустить SUT:

  - с использованием БД MySQL командой `java "-Dspring.datasource.url=jdbc:mysql://localhost:3300/app" -jar artifacts/aqa-shop.jar`
  - с использованием БД PostgreSQL командой `java -jar artifacts/aqa-shop.jar "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app"`

* запустить автотесты командой:

  - для конфигурации БД MySql:
`./gradlew clean test "-Ddatasource.url=jdbc:mysql://localhost:3300/app"`
  - для конфигурации БД PostgreSQL:
`./gradlew clean test "-Ddatasource.url=jdbc:postgresql://localhost:5432/app"`

* запустить отчеты командой:

  - ./gradlew allureReport (первоначальная команда)

  - ./gradlew allureServe (запуск и открытие отчетов)

* остановить SUT комбдинацией клавиш CTRL+C

* остановить контейнеры командой docker-compose stop, удалить контейнеры командой docker-compose down
