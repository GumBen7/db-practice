# Группы 107б2, 107д1

# Программа курса
* [00. Знакомство с MS SQL Server. Создание и заполнение таблиц с помощью мастера](src/Lab00.md)
* [0. Создание и заполнение таблиц с помощью скриптов](src/Lab0.md)
* [1. Задания на тренировку создания связанных таблиц](src/Lab1_design.md)
* [2. Команда SELECT](src/Lab2.md)
* [3. Фильтрация данных, подзапросы и объединение однотипных запросов](src/Lab3.md)
* [4. Типы данных и встроенные функции](src/Lab4.md)
* [5. Агрегатные функции и группировка](src/Lab5.md)
* [6. Соединение таблиц и группировка](src/Lab6.md)
* [7. Переменные и управляющие конструкции](src/Lab7.md)
* [8. Представления. Табличные объекты. Пользовательские функции](src/Lab8.md)
* [9. Хранимые процедуры и триггеры](src/Lab9.md)
* [10. Индексы и ограничения](src/Lab10.md) 
* [11. Курсоры. Оконные функции](src/Lab11.md)
* [12. Нормализация](src/Lab12.md)
* [13. Динамический SQL, XML и JSON. Импорт и экспорт данных](src/Lab13.md)
* [14. C#](src/Lab14.md)

# Лабораторные 

### [00. Знакомство с MS SQL Server. Создание и заполнение таблиц](src/Lab00.md)

1. Создание базы данных
2. Создание учетной записи
3. Создание и редактирование таблиц с помощью мастера
4. Связывание таблиц через Диаграммы базы данных

### [0. Создание и заполнение таблиц с помощью скриптов](src/Lab0.md)

1. Создание базы данных
2. Создание и удаление таблиц (CREATE, DROP)
3. Редактирование таблицы, столбцов и атрибутов столбцов
4. Редактирование данных таблицы (ALTER TABLE, INSERT, DROP, UPDATE)
5. Построение диаграммы
6. ADD PRIMARY KEY
7. Связывание таблиц через FOREIGN KEY
8. ON UPDATE, ON DELETE CASCADE


### [1. Задания на тренировку создания связанных таблиц](src/Lab1_design.md)

* Создать таблицы с заданными типами связей
* Создать по образу и подобию имеющейся схемы (текст/картинка)
* Отредактировать созданное


### [2. Команда SELECT](src/Lab2.md)

1. Основы выборки данных
2. Конструкции DISTINCT | ALL
3. Выражение SELECT INTO
4. Сортировка данных
5. Конструкция TOP
6. Конструкции OFFSET и FETCH

+ 12 заданий

* составить 5 запросов с командой select и блоком from
* составить 5 запросов с командой select и вычисляемыми столбцами
* составить 3 запроса с командой select, используя ключевое слово для отброса строк дубликатов
* составить по одному запросу для каждой из конструкиций: ORDER BY, TOP, PERCENT, OFFSET, FETCH
* составить 3 запроса с записью данных в новую таблицу
* составить 3 запроса с сортировкой по вычисляемому значению


### [3. Фильтрация данных, подзапросы и объединение однотипных запросов](src/Lab3.md)

1. Фильтрация
2. WHERE
3. Операции сравнения
4. Логические операторы
5. BETWEEN, LIKE | ESCAPE, NULL, IN и NOT IN
6. Подзапросы/вложенные запросы и их виды
7. Некоррелирующие и коррелирующие подзапросы
8. Применение конструкции IN к подзапросам
9. Конструкция ALL и [SOME | ANY](https://learn.microsoft.com/ru-ru/sql/t-sql/language-elements/some-any-transact-sql?view=sql-server-ver16)
10. Предикат [EXISTS](https://learn.microsoft.com/ru-ru/sql/t-sql/language-elements/exists-transact-sql?view=sql-server-ver16)
11. Объединение однотипных запросов: UNION, EXCEPT, INTERSECT

+ 12 заданий
+ 12 заданий
+ 3 задания
+ 3 задания


### [4. Типы данных и встроенные функции](src/Lab4.md)

1. Изучить основные типы данных.
2. Изучить встроенные функции для работы со строками.
3. Изучить встроенные функции для работы с числами.
4. Изучить встроенные функции для работы с датами и временем.
5. Изучить встроенные функции преобразования данных.
6. *Изучить CASE и IIF.
7. *Функции проверки значений
8. *Функция NEWID

+ 14 заданий
+ *4 задания по таблице стран
+ 9 заданий для своих таблиц


### [5. Агрегатные функции и группировка](src/Lab5.md)

0. Основы агрегации данных
1. Функции MAX | MIN
2. Функция SUM
3. Функция AVG
4. Функция COUNT
5. *Комбинирование функций(м)
5. Группировка данных
6. GROUP BY и HAVING
7. Изучить применение фильтрации в группировке данных
8. Инструкции OLAP (OVER, ROLLUP, GROUPING SETS, CUBE)

+ 12 заданий
+ 12 заданий
+ доделать хитровыдуманные на подсчет среднего

### [6. Соединение таблиц и группировка](src/Lab6.md)

0. Проектирование и создание связанных таблиц
  * Проектирование и создание пачкой
  * Создание по картинке
  * Создать по образу и подобию заданной схемы
  * Создать таблицы с заданными типами связей
  * Создать по текстовому описанию
  * Отредактировать созданное

1. Неявное соединение таблиц
2. INNER JOIN и OUTER JOIN
3. LEFT | RIGHT | FULL OUTER JOIN, Перекрестное соединение CROSS JOIN
4. Группировка в соединениях

+ 5 заданий на проектирование
+ 6 запросов по этим таблицам
+ 12 заданий
  
### [7. Переменные и управляющие конструкции](src/Lab7.md)

1. Переменные
2. Условные выражения
3. Циклы
4. try/catch
5. Обработка ошибок

+ 12 заданий
+ 4 задания
+ 3 задания
+ 5 заданий
+ 1 задание


### [8. Представления. Табличные объекты. Пользовательские функции](src/Lab8.md)

1. Представления: создание и удаление
2. Табличные переменные (DECLARE)
3. Производные таблицы
4. Временные таблицы
5. Обобщенные табличные выражения (WITH)
6. Пользовательские функции (скалярные, INLINE, MULTI-STATEMENT, удаление функций)

+ 6 заданий
+ 4 задания
+ 11 заданий
+ 5 заданий
  

### [9. Хранимые процедуры и триггеры](src/Lab9.md)

1. Хранимые процедуры: создание, удаление, вызов
2. Передача входных и выходных параметров
3. Триггеры: создание, удаление, приостановление
4. Триггеры после и вместо событий
5. Виртуальные таблицы в триггерах

+ 8 заданий
+ 9 задания
+ 7 заданий
+ задание  
  
### [10. Индексы и ограничения](src/Lab10.md)

1. Индексы
2. Ограничения
3. Сложные скрипты создания с дофига ограничениями и внешними ключами
  
+ 7 заданий
+ 10 заданий

### [11. Курсоры. Оконные функции](src/Lab11.md)

1. Использование курсоров
2. Прокрутка курсоров
3. Использование циклов в курсорах
4. Использование переменных в курсорах
5. Оконные функции
6. Аналитические функции
7. Ранжирующие функции
8. Функции смещения

+ 12 заданий
+ 7 заданий
  

### [12. Нормализация](src/Lab12.md)

* Нормализация и приведение к форме
* ER-модель

+ 2 задания

### [13. Динамический SQL, XML и JSON. Импорт и экспорт данных](src/Lab13.md)

* Использование динамического SQL
* Вывод данных в формате XML
* Вывод данных в формате JSON
* Импорт CSV в SQL Server 
* Использование оператора BULK INSERT

+ 8 заданий
+ 4 задания

### [14. C#](src/Lab14.md)

* Подключение к базе из среды VS
* Запросы к базе из среды VS на языке C#

  + 2 задания
  + 3 задания
  + 3 задания опционально


