# Отчёт о проведённом тестировании
## 1. Краткое описание
Проведено автоматизированное тестирование приложения, которое предлагает купить тур двумя способами:
1. Оплата по дебетовой карте
2. Выдача кредита по данным банковской карты

Приложение поддерживает две БД:
- MySQL
- PostgreSQL

## 2. Количество тест-кейсов
Общее количество тест-кейсов - 74:
- 56 пройдено успешно (75.67%)
- 18 не пройдено (24.33%)
  
Создан отчет Allure:
![Снимок экрана 2024-01-10 144110](https://github.com/Navershune/Diploma/assets/119427441/78f72c66-cb16-4d36-80dd-babe3b30efea)

По результатам тестирования были заведены [баг-репорты](https://github.com/Navershune/Diploma/issues)

## 3. Общие рекомендации
1. Устранить обнаруженные [проблемы](https://github.com/Navershune/Diploma/issues)
2. Составить документацию к приложению
3. Добавить возможность неактивности кнопки "Продолжить" до тех пор, пока все поля не будут заполнены корректными значениями
4. Добавить уникальные идентификаторы для элементов страниц (test-id) для ускорения и упрощения автоматизации тестирования
