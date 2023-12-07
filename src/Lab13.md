---
title: Лабораторная работа 13. Динамический SQL, XML и JSON. Импорт и экспорт данных
---

[Архив с данными для импорта](assets/lab/DE_norm.zip)

[К списку лабораторных >>>](../README.md)

---

### Задания по всем подрядд таблицам

1. Создайте и запустите динамический SQL-запрос, выбирающий первые N строк из заданной таблицы.
2. Создайте и запустите динамический SQL-запрос, выбирающий все страны из таблицы «Страны», последняя буква названия которых расположена в заданном диапазоне.
3. Создайте временную таблицу #Temp и добавьте к ней название столбцов таблицы «Страны». Создайте курсор, который, построчно читая таблицу #Temp, выбирает каждый раз соответствующий столбец из таблицы «Страны».
4. Создайте процедуру, которая принимает как параметр список столбцов, название таблицы и выбирает заданные столбцы из заданной таблицы.
5. Создайте процедуру, принимающую как параметр список столбцов, название таблицы, название проверяемого столбца, знак сравнения, значение проверки и выбирающую заданные столбцы из заданной таблицы в заданных условиях.
6. Выберите список европейских стран из таблицы «Страны» и экспортируйте в RAW формате XML.
7. Выберите список стран с населением больше 100 млн. чел. из таблицы «Страны» и экспортируйте в PATH формате XML.
8. Выберите список учеников из школы «Лицей» из таблицы «Ученики» и экспортируйте в PATH формате JSON

### Задания по импорту данных

1. Подготовить Excel-файлы для импорта на основе модели из [Лабораторной №12](Lab12.md)
2. Написать скрипт для создания таблиц
3. Написать скрипт для импорта данных в таблицы

---

### [Использование динамического SQL]()

В интерактивных приложениях часто состав SQL-запросов заранее не известен и может изменяться в зависимости от условий.
Для решения таких ситуаций используется динамический SQL. Запросы формируются в виде текстовых строк непосредственно во время работы программы. 
Выполнение динамического SQL медленнее, чем статического.
Для выполнения динамического SQL используется команда EXEC | EXECUTE. Упрощенный синтаксис имеет следующий вид:
EXEC | EXECUTE (<строка динамического SQL>)

Пример: Создайте и запустите динамический SQL-запрос, выбирающий все данные из заданной таблицы:
```sql
DECLARE @DSQL VARCHAR(100)
DECLARE @TN VARCHAR(50)
SET @TN = 'Ученики'
SET @DSQL = 'SELECT * FROM ' + @TN
EXECUTE (@DSQL)
```

Пример: Создайте временную таблицу #Temp и добавить в нее название пяти таблиц из базы данных «Учебная». 
Создайте курсор, который, построчно читая таблицу #Temp, выбирает из каждой таблицы все данные:
```sql
CREATE TABLE #TEMP
(
TABLENAME VARCHAR(50)
)
INSERT INTO
#TEMP
VALUES
('Дисциплина'),
('Заявка'),
('Инженер'),
('Кафедра'),
('Сотрудник')
DECLARE TC CURSOR
FOR SELECT TABLENAME FROM #TEMP
OPEN TC
DECLARE @TN VARCHAR(50)
FETCH FROM TC INTO @TN
WHILE @@FETCH_STATUS = 0
BEGIN
EXECUTE ('SELECT * FROM ' + @TN)
FETCH FROM TC INTO @TN
END
CLOSE TC
DEALLOCATE TC
DROP TABLE #TEMP
```

---

### [Вывод данных в формате XML]()

Результат выполнения запроса можно получать в формате XML. Для этого в запросе необходимо указать предложение FOR XML.
В предложении FOR XML можно указать один из следующих режимов:

* RAW – в этом режиме создается одиночный элемент <row> для каждой строки набора строк, возвращенного инструкцией SELECT. 
  XML-иерархию можно создать с помощью написания вложенных запросов FOR XML.
* AUTO – в этом режиме вложенность XML создается эвристически, в зависимости от метода определения инструкции SELECT.
* EXPLICIT – этот режим предоставляет больше возможностей по управлению формой XML-структуры.
  В XML-структуре могут быть использованы смешанные атрибуты и элементы. Однако написание запросов в режиме EXPLICIT может быть очень обременительным.
* PATH – этот режим совместно с вложенным запросом FOR XML обеспечивает гибкость режима EXPLICIT более простым образом.
  
Эти режимы на самом деле работают только при выполнении запросов, для которых они установлены. Они не влияют на результаты любых последующих запросов.

Пример: Выберите данные из таблицы «Ученики» и экспортируйте в RAW формате XML:
```sql
SELECT
ID, Фамилия, Предмет, Школа, Баллы
FROM Ученики
FOR XML RAW
```

---

### [Вывод данных в формате JSON]()

Результат выполнения запроса можно получать в формате JSON. Для этого в запросе необходимо указать предложение FOR JSON. 
Предложение FOR JSON упрощает клиентские приложения, делегируя форматирование выходных данных JSON из приложения в SQL Server.
В предложении FOR XML можно указать один из следующих режимов:

* PATH – этот режим используется для того чтобы сохранить полный контроль над форматом выходных данных JSON. 
  Можно создавать объекты-оболочки и вкладывать сложные свойства друг в друга.
* AUTO – этот режим используется для того чтобы отформатировать выходные данные автоматически на основе структуры инструкции SELECT.

Пример: Выберите данные из таблицы «Ученики» и экспортируйте в PATH формате JSON:
```sql
SELECT
ID, Фамилия, Предмет, Школа, Баллы
FROM Ученики
FOR JSON PATH
```

---

### Импорт CSV в SQL Server

---

### Использование оператора BULK INSERT

Оператор BULK INSERT в SQL Server позволяет осуществлять импорт данных из файла в таблицу.
В предложении WITH для данного оператора можно задавать опции.
Например:

* FIELDTERMINATOR - Указывает разделитель для столбцов. По умолчанию, разделителем в функции BULK INSERT является символ табуляции (\t).
В CSV разделителем по умолчанию является запятая.

* ROWTERMINATOR - Указывает разделитель для строк.

Привем, как выгрузить данные для простого CSV-Файла.
Этот файл содержит несколько строк для простого отчета. 

Используйте следующий код:

```sql
IF (OBJECT_ID('CSV_Export') IS NOT NULL) DROP TABLE dbo.CSV_Export;

CREATE TABLE CSV_Export (
	DateReport VARCHAR(15),
	CountView INT,
	CountClicks INT,
	CTR FLOAT,
	RPM FLOAT,
	Profit FLOAT
)

BULK INSERT dbo.CSV_Export FROM 'D:\VKI\CSV_Export.csv'
WITH (FIELDTERMINATOR = ';', ROWTERMINATOR = '\n');
```

В качестве разделителя в исходном CSV-файле используется знак табуляции (Tab). 
В CSV также можно использовать запятые, точки с запятой и другие символы в качестве разделителя столбцов. 
Главное указать символ в параметре FIELDTERMINATOR.

Выберите теперь все строки из таблицы CSV_Export с помощью оператора SELECT для проверки результата:
```sql
SELECT TOP 100 * FROM CSV_Export;
```

Как правило, данные из CSV-файла нужно сохранять во временную таблицу, а затем из нее вставлять в основную, 
т.к. зачастую необходимо парсить даты, числа с плавающей запятой и другие форматы. 
Их можно парсить в строку во временной таблице и привести к нужному формату в основной.

```sql
-- Создаем временную таблицу и импортируем данные из CSV
IF (OBJECT_ID('tempdb..#csv_temp') IS NOT NULL) DROP TABLE #csv_temp;
CREATE TABLE #csv_temp (
    DateReport VARCHAR(15),
	CountView INT,
	CountClicks INT,
	CTR FLOAT,
	RPM FLOAT,
	Profit FLOAT
);

BULK INSERT #csv_temp FROM 'D:\VKI\CSV_Export.csv'
WITH (fieldterminator = ';', rowterminator = '\n');
-- Создаем основную таблицу
IF (OBJECT_ID('CSV_Export') IS NOT NULL) DROP TABLE dbo.CSV_Export;

CREATE TABLE CSV_Export (
	DateReport DATETIME,
	CountView INT,
	CountClicks INT,
	CTR FLOAT,
	RPM FLOAT,
	Profit FLOAT
)
-- Заполняем данными из временной таблицы
INSERT INTO CSV_Export
SELECT CONVERT(datetime, DateReport, 105), -- Строку в дату
	CountView, CountClicks, CTR, RPM, Profit
FROM #csv_temp;

-- Проверяем
SELECT TOP 100 *FROM CSV_Export;
```

Теперь в основной таблице столбец DateReport будет храниться в формате даты.


---