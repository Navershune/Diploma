## **План автоматизации тестирования сервиса для приобретения тура**

#### Валидные данные для заполнения формы оплаты или покупки в кредит:

- Поле “Номер карты”: 16 цифр
- Поле “Месяц”: две цифры от 01 до 12, если в поле “Год” карты указан текущий, то месяц должен быть не ранее текущего
- Поле “Год”: две последние цифры текущего года или пяти последующих
- Поле “Владелец”: имя и фамилия латинскими буквами, в любом регистре, в том числе с использованием заглавных или строчных букв в любой последовательности, заполнены через пробел, допускается двойная фамилия через дефис, допускается двойное имя через пробел или дефис, максимальное число знаков - 64 с учетом пробела
- Поле “CVC/CVV”: любые три цифры


#### Тестовые данные:

- Номер карты - 4444 4444 4444 4441, статус при проверке в БД - APPROVED
- Номер карты - 4444 4444 4444 4442, статус при проверке в БД - DECLINED

### Позитивные сценарии:

1. **Номер карты со статусом APPROVED.**
   * Ввести валидные данные для заполнения формы (номер карты - 4444 4444 4444 4441).
   * Нажать на кнопку "Продолжить".
   
   **Ожидаемый результат:**
   - Появится сообщение "Успешно! Операция одобрена банком".
  
 
2. **Номер карты со статусом DECLINED.**
   * Ввести валидные данные для заполнения формы (номер карты - 4444 4444 4444 4442).
   * Нажать на кнопку "Продолжить".

   **Ожидаемый результат:**
   - Появится сообщение "Ошибка! Банк отказал в проведении операции".

   ### Негативные сценарии:

1. **Пустая форма**
   * Оставить все поля формы пустыми;
   * Нажать на кнопку "Продолжить".
   
   **Ожидаемый результат:**
   -  Под полями появятся сообщение об ошибке: "Поле обязательно для заполнения".
   

2. **Форма с невалидным номером карты**
   
   2.1. **Номер карты 4444 4444 4444 4443**
      * Ввести валидные данные для заполнения формы (номер карты - 4444 4444 4444 4443).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
       - Появится сообщение "Ошибка! Банк отказал в проведении операции".

   2.2. **Номер карты все нули**
      * Ввести валидные данные для заполнения формы (номер карты - 0000 0000 0000 0000).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Появится сообщение "Ошибка! Банк отказал в проведении операции".
   
   2.3. **Форма, где в номере карт цифр меньше 16**
      * Ввести валидные данные для заполнения формы (номер карты - 4444 4444 4444 444).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Номер карты" появится сообщение об ошибке "Неверный формат".

3. **Форма с невалидным значением месяца**
   
   3.1. **Месяц 00**
      * Ввести валидные данные для заполнения формы (в поле "Месяц" ввести 00).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Месяц" появится сообщение об ошибке "Неверно указан срок действия карты".
	  
   3.2. **Месяц более 12**
      * Ввести валидные данные для заполнения формы (в поле "Месяц" ввести 13).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Месяц" появится сообщение об ошибке "Неверно указан срок действия карты".
	  
   3.3. **Месяц менее 2 цифр**
      * Ввести валидные данные для заполнения формы (в поле "Месяц" ввести 1).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Месяц" появится сообщение об ошибке "Неверный формат".
	  
4. **Форма с невалидным значением года**

   4.1. **Год 00**
      * Ввести валидные данные для заполнения формы (в поле "Год" ввести 00).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Год" появится сообщение об ошибке "Истёк срок действия карты".
   
   4.2. **Год более допустимого**
      * Ввести валидные данные для заполнения формы (в поле "Год" ввести 99).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Год" появится сообщение об ошибке "Неверно указан срок действия карты".
   
   4.3. **Год менее допустимого**
      * Ввести валидные данные для заполнения формы (в поле "Год" ввести 22).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Год" появится сообщение об ошибке "Истёк срок действия карты".
	  
5. **Форма с невалидным значением поля Владелец**

   5.1. **В поле Владелец имя и фамилия на кириллице**
      * Ввести валидные данные для заполнения формы (в поле "Владелец" ввести Фамилию и Имя на кириллице).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Владелец" появится сообщение об ошибке "Неверный формат".
   
   5.2 **В поле Владелец ввести цифры**
      * Ввести валидные данные для заполнения формы (в поле "Владелец" ввести 1234567890).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Владелец" появится сообщение об ошибке "Неверный формат".
   
   5.3. **В поле Владелец одна буква**
      * Ввести валидные данные для заполнения формы (в поле "Владелец" ввести F).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Владелец" появится сообщение об ошибке "Неверный формат".
   
   5.4. **В поле Владелец - спецсимволы**
      * Ввести валидные данные для заполнения формы (в поле "Владелец" ввести спецсимволы).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "Владелец" появится сообщение об ошибке "Неверный формат".
	  
6. **Форма с невалидным "CVC/CVV"**

   6.1. **В поле "CVC/CVV" две цифры**
      * Ввести валидные данные для заполнения формы (в поле "CVC/CVV" ввести 99).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "CVC/CVV" появится сообщение об ошибке "Неверный формат".
   
   6.2. **В поле "CVC/CVV" одна цифра;**
      * Ввести валидные данные для заполнения формы (в поле "CVC/CVV" ввести 9).
      * Нажать на кнопку "Продолжить".

      **Ожидаемый результат:**
      - Под полем "CVC/CVV" появится сообщение об ошибке "Неверный формат".

      ## Перечень используемых инструментов:

1. `IntelliJ IDEA`- интегрированная среда разработки ПО для многих языков программирования. Удобная среда подготовки авто-тестов.
2. `JDK11` - пакет для работы и создания приложений на базе языка Java, удобен в использовании, много возможностей для разработки, распространенный язык, актуальная, стабильно работающая версия.
3. `JUnit 5` - инструмент тестирования, среда модульного тестирования для языка программирования Java.
4. `Gradle` - мощная и простая система автоматической сборки проектов, которая используется для упрощения работы с JAVA.
5. `Selenide` - это фреймворк для автоматизированного тестирования веб-приложений на основе Selenium WebDriver, дающий следующие преимущества: изящный API, поддержка AJAX для стабильных тестов, мощные селекторы, простая конфигурация.
6. `Faker` - это библиотека, которая позволяет генерировать случайные данные. С ее помощью можно заполнить таблицы в базе данных, построить корректные XML-документы, сформировать JSON-ответы для REST.
7. `Allure` - фреймворк, предназначенный для создания визуально наглядной картины выполнения тестов.
8. `Docker` - Запуск необходимых приложений из контейнера без необходимости их установки на ОС;

## Перечень и описание возможных рисков при автоматизации:

1. Отсутствие документации на проект.
2. Необходимость проверки взаимодействия сразу двух СУБД. Возможно возникнут сложности при написании и прогоне тестов.
3. Необходима установка и подключение нескольких приложений и сервисов плюс их взаимодействие друг с другом. Это затратно по времени.
4. Отсутствие "test_id" усложняет написание и поддержку тестов. 

## Интервальная оценка с учётом рисков в часах:

1. Подготовка окружения, развертывание БД - 8 часов;
2. Написание автотестов и отладка - 96 часов;
3. Отчетные документы по итогам тестирования: 10 ч;
4. Отчетные документы по итогам автоматизации: 10 ч;
