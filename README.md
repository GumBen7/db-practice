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
* 10.Решение задач на проектирование и sql 
* 11.Решение задач на хранимые процедуры и триггеры
* [12. Нормализация](src/Lab12.md)
* 13.Курсоры. Оконные функции
* 14.Динамический SQL, XML и JSON. Импорт и экспорт данных
* 15.Пространственные данные 

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

* Представления: создание и удаление
* Табличные переменные (DECLARE)
* Производные таблицы
* Временные таблицы
* Обобщенные табличные выражения (WITH)
* Пользовательские функции (скалярные, INLINE, MULTI-STATEMENT, удаление функций)

+ 6 заданий
+ 4 задания
+ 11 заданий
+ 5 заданий
  

### 9. Хранимые процедуры и триггеры

* Хранимые процедуры: создание, удаление, вызов
* Передача входных и выходных параметров
* Триггеры: создание, удаление, приостановление
* Триггеры после и вместо событий
* Виртуальные таблицы в триггерах
  
### 10. Решение задач на проектирование и sql

* Решение задач на sql
* Из файла про MySQL
* На проектирование 30 таблиц


### 11. Решение задач на хранимые процедуры и триггеры

* Решение задач на хранимые процедуры и триггеры


### [12. Нормализация](src/Lab12.md)

* Временные таблицы
* Сложные скрипты создания с дофига ограничениями и внешними ключами
* Проектирование и создание пачкой
  + Создание по картинке
* Создать таблицы с заданными типами связей
* Создать по образу и подобию заданной схемы
* Создать по текстовому описанию
* Отредактировать созданное

### 13. Курсоры. Оконные функции

* Использование курсоров
* Прокрутка курсоров
* Использование циклов в курсорах
* Использование переменных в курсорах
* Оконные функции
* Аналитические функции
* Ранжирующие функции
* Функции смещения


### Инструкции OLAP (\#5)

* ROLLUP
* CUBE
* GROUPING SETS
* PIVOT
* UNPIVOT


### 14. Динамический SQL, XML и JSON. Импорт и экспорт данных

* Использование динамического SQL
* Вывод данных в формате XML
* Вывод данных в формате JSON
* Импорт CSV в SQL Server 
* Использование оператора BULK INSERT


### 15. Пространственные данные

* Пространственные данные
* Тип данных GEOMETRY
* Тип данных GEOGRAPHY

