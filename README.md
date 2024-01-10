# Дипломный проект по курсу «Тестировщик ПО»
В рамках дипломного проекта необходимо автоматизировать тестирование комплексного сервиса приобретения тура, взаимодействующего с СУБД и API Банка. В приложении используются два отдельных сервиса оплаты: Payment Gate и Credit Gate.

[Ссылка на Дипломное задание](https://github.com/netology-code/qa-diploma)

# Тестовая документация

- [План автоматизации тестирования веб-формы сервиса покупки туров интернет-банка](https://github.com/Navershune/Diploma/blob/main/Documentation/Plan.md)
- [Отчёт о проведённом тестировании](https://github.com/Navershune/Diploma/blob/main/Documentation/Report.md)
- [Отчет о проведенной автоматизации](https://github.com/Navershune/Diploma/blob/main/Documentation/Summary.md)

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
   java -jar artifacts/aqa-shop.jar --spring.datasource.url=jdbc:mysql://localhost:3306/app
   ```
   
      * Для PostgreSQL:
   ```
   java -jar artifacts/aqa-shop.jar --spring.datasource.url=jdbc:postgresql://localhost:5432/app
   ```
   
1. Убедиться в готовности системы. Сервис должен быть доступен по адресу:
```
http://localhost:8080/
```

### Запуск тестов
1. В новой вкладке терминала ввести команду в зависимости от запущенной БД в п.2 Запуска:
   
  * Для MySQL:
```
.\gradlew clean test -DdbUrl=jdbc:mysql://localhost:3306/app
```
  * Для PostgreSQL:
```
.\gradlew clean test -DdbUrl=jdbc:postgresql://localhost:5432/app
```

### Формирование отчета по результатам тестирования
1. Для получения отчета ввести в терминале команду
```
.\gradlew allureServe
```
2. Чтобы закрыть отчет, требуется ввести команду ``Ctrl + C``, чтобы подтвердить выход, необходимо ввести ``Y``
3. Для остановки работы контейнеров ввести команду ``docker-compose down``
