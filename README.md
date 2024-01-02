# Дипломный проект по курсу «Тестировщик ПО»
В рамках дипломного проекта необходимо автоматизировать тестирование комплексного сервиса приобретения тура, взаимодействующего с СУБД и API Банка. В приложении используются два отдельных сервиса оплаты: Payment Gate и Credit Gate.

[Ссылка на Дипломное задание](https://github.com/netology-code/qa-diploma)

# Тестовая документация

- [План автоматизации тестирования веб-формы сервиса покупки туров интернет-банка](https://github.com/Navershune/Diploma/blob/main/Documentation/Plan.md)

## Запуск приложения
### Подготовительный этап
1. Установить и запустить IntelliJ IDEA;
2. Установать и запустить Docker Desktop;
3. Скопировать репозиторий с Github [по ссылке](https://github.com/Navershune/Diploma).
4. Открыть проект в IntelliJ IDEA.

### Запуск тестового приложения
1. Запустить MySQL, PostgreSQL, NodeJS через терминал командой:
   ```
   docker-compose up -d
   ```
1. В новой вкладке терминала запустить тестируемое приложение:
    * Для MySQL:
   ```
   java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar artifacts/aqa-shop.jar
   ```
    * Для PostgreSQL:
   ```
   java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar artifacts/aqa-shop.jar
   ```
   .
1. Убедиться в готовности системы. Сервис должен быть доступен по адресу:
```
http://localhost:8080/
```
