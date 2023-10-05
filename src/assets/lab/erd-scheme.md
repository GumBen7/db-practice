Проектирование базы данных

Полный цикл разработки базы данных включает концептуальное, логическое и физическое ее проектирование.
Концептуальное проектирование базы данных
Первая фаза процесса проектирования базы данных заключается в создании для анализируемой части предприятия концептуальной модели данных.
В построении общей концептуальной модели данных выделяют ряд этапов.
	Выделение локальных представлений, соответствующих обычно относительно независимым данным. Каждое такое представление проектируется как подзадача.
	Формулирование сущностей, описывающих локальную предметную область проектируемой БД, и описание атрибутов, составляющих структуру каждой сущности.
	Выделение ключевых атрибутов.
	Спецификация связей между сущностями. Удаление избыточных связей.
	Анализ и добавление неключевых атрибутов.
	Объединение локальных представлений.
Созданная концептуальная модель данных предприятия является источником информации для фазы логического проектирования базы данных.
Логическое проектирование базы данных
Цель второй фазы проектирования базы данных состоит в создании логической модели данных для исследуемой части предприятия.
Логическая модель, отражающая особенности представления о функционировании предприятия одновременно многих типов пользователей, называется глобальной логической моделью данных.
Процесс проектирования БД должен опираться на определенную модель данных (реляционная, сетевая, иерархическая), которая определяется типом предполагаемой для реализации информационной системы СУБД.
Концептуальное и логическое проектирование — это итеративные процессы, которые включают в себя ряд уточнений, продолжающиеся до тех пор, пока не будет получен наиболее соответствующий структуре предприятия продукт.
Физическое проектирование базы данных
Целью проектирования на данном этапе является создание описания СУБД ориентированной модели БД.
Действия, выполняемые на этом этапе, слишком специфичны для различных моделей данных, поэтому их сложно обобщить. Остановимся на реляционной модели данных. В этом случае под физическим проектированием подразумевается:
	создание описания набора реляционных таблиц и ограничений для них на основе информации, представленной в глобальной логической модели данных;
	определение конкретных структур хранения данных и методов доступа к ним, обеспечивающих оптимальную производительность системы с базой данных;
	разработка средств зашиты создаваемой системы.

Разработка приложений

Параллельно с проектированием системы базы данных выполняется разработка приложений. Главные составляющие данного процесса — это проектирование транзакций и пользовательского интерфейса.
Проектирование транзакций
Транзакции представляют некоторые события реального мира.
Транзакция может состоять из нескольких операций, однако с точки зрения пользователя эти операции представляют собой единое целое, переводящее базу данных из одного непротиворечивого состояния в другое. Реализация транзакций опирается на тот факт, что СУБД способна обеспечивать сохранность внесенных во время транзакции изменений в БД и непротиворечивость базы данных даже в случае возникновения сбоя.
Проектирование транзакций заключается в определении:
	данных, которые используются транзакцией;
	функциональных характеристик транзакции;
	выходных данных, формируемых транзакцией;
	степени важности и интенсивности использования транзакции.
Проектирование пользовательского интерфейса
Интерфейс должен быть удобным и обеспечивать все функциональные возможности, предусмотренные в спецификациях требований пользователей.
Специалисты рекомендуют при проектировании пользовательского интерфейса использовать следующие основные элементы и их характеристики:
	содержательное название;
	ясные и понятные инструкции;
	логически обоснованные группировки и последовательности полей;
	визуально привлекательный вид окна формы или поля отчета;
	легко узнаваемые названия полей;
	согласованную терминологию и сокращения;
	согласованное использование цветов;
	визуальное выделение пространства и границ полей ввода данных;
	удобные средства перемещения курсора;
	средства исправления отдельных ошибочных символов и целых
	полей;
	средства вывода сообщений об ошибках при вводе недопустимых
	значений;
	особое выделение необязательных для ввода полей;
	средства вывода пояснительных сообщений с описанием полей;
	средства вывода сообщения об окончании заполнения формы.

Реализация

На данном этапе осуществляется физическая реализация базы данных и разработанных приложений, позволяющих пользователю формулировать требуемые запросы к БД и манипулировать данными в БД.
База данных описывается на языке определения данных выбранной СУБД. В результате компиляции его команд и их выполнения создаются схемы и пустые файлы базы данных. На этом же этапе определяются и все специфические пользовательские представления.
Прикладные программы реализуются с помощью языков третьего или четвертого поколений. Кроме того, на этом этапе создаются другие компоненты проекта приложения — например, экраны меню, формы ввода данных и отчеты.
Реализация этого, а также и более ранних этапов проектирования БД может осуществляться с помощью инструментов автоматизированного проектирования и создания программ, которые принято называть CASE-инструментами (Computer-Aided Software Engineering).

Загрузка данных

На этом этапе созданные в соответствии со схемой базы данных пустые файлы, предназначенные для хранения информации, должны быть заполнены данными. Наполнение базы данных может протекать по-разному, в зависимости от того, создается ли база данных вновь или новая база данных предназначена для замены старой.

Тестирование

Для оценки законченности и корректности выполнения приложения базы данных может использоваться несколько различных стратегий тестирования:
	нисходящее тестирование;
	восходящее тестирование;
	тестирование потоков;
	интенсивное тестирование.

Эксплуатация и сопровождение

Основные действия, связанные с этим этапом сводятся к наблюдению за созданной системой и поддержке ее нормального функционирования по окончании развертывания.
Поддержка БД предполагает разрешение проблем, возникающих в процессе эксплуатации БД и связанных как с ошибками реализации БД, так и с изменениями в самой предметной области, созданием дополнительных программных компонент или модернизацией самой БД.


Лекция 8. Концептуальное проектирование БД

План:
1.	Модель "Сущность - Связь"(ERD)
2.	Структурный подход при разработке инфологической модели
3.	Моделирование локальных представлений
4.	Правила преобразования ER-диаграмм в реляционные таблицы
	
	Концептуальная модель отображает реальный мир в некоторые понятные человеку концепции, полностью независимые от параметров среды хранения данных. Существует множество подходов к построению таких моделей: графовые модели, семантические сети, модель "сущность-связь" и т.д. Наиболее популярной из них оказалась модель "сущность-связь".

Модель "Сущность - Связь"(ERD)
	
	Это модель предметной области, которая используется на этапе концептуального проектирования. 
	Модель использует три основных элемента: сущность, атрибут и связь.
	Сущность - это абстракция какого-либо объекта, процесса или явления реального мира, о котором нужно хранить информацию. В качестве сущности могут выступать материальные (предприятие, товар) и нематериальные (описание явления, реферат статьи) объекты.
	Тип сущности определяет набор однородных объектов, а экземпляр сущности - конкретный объект в наборе.
	 Каждый тип сущности обладает одним или несколькими атрибутами.
	 Каждому типу сущности должно быть дано уникальное имя. К одному и тому же имени должна всегда применяться одна и та же интерпретация. 
	Для идентификации конкретных экземпляров сущностей используются атрибуты – идентификаторы (один или несколько), которые позволяют однозначно отличать один экземпляр сущности от другого.
Каждая сущность может обладать любым количеством связей с другими сущностями модели. 
	Атрибут - это поименованная характеристика сущности, которая принимает значения из некоторого множества значений. 
	Чтобы задать атрибут в модели, необходимо присвоить ему наименование, привести смысловое описание атрибута, определить множество его допустимых значений и указать, для чего он используется.
	Основное назначение атрибута - описание свойства сущности, а также идентификация экземпляров сущности. 
	Атрибут может быть либо обязательным, либо необязательным. Обязательность означает, что атрибут не может принимать неопределенных значений (null values). Атрибут может быть либо описательным, либо входить в состав уникального идентификатора (первичного ключа). 
	Первичный ключ – набор атрибутов, значения которого однозначно определяют экземпляр сущности.
	Внешний ключ - это набор атрибутов, используемый для представления связей между сущностями.
Связь  - поименованная ассоциация между двумя сущностями, значимая для рассматриваемой предметной области. Связь – это средство, с помощью которого представляются отношения между сущностями, имеющие место в предметной области. Связи может даваться имя, выражаемое грамматическим оборотом глагола. Имя каждой связи между двумя данными сущностями должно быть уникальным, но имена связей в модели не обязаны быть уникальными. 
	Связи могут быть между двумя (бинарные), тремя (тернарные) и более сущностями. Чаще всего используются бинарные. Они классифицируются следующим образом:
	Связь "один - к - одному" (1:1)
	Когда каждому экземпляру сущности А соответствует один и только один экземпляр сущности Б, и наоборот. Связь двунаправленная.
	Связь "один - ко - многим" (1:М)
	Это такой тип связи, когда каждому экземпляру сущности А может соответствовать ни одного, один или несколько экземпляров сущности Б, однако каждому экземпляру сущности Б соответствует один и только один экземпляр сущности А.
 
	Связь "многие - к - одному" (М:1)
	Это отображение обратно предыдущему.
	Связь "многие - ко - многим" (отображение М:N)
	Это такой тип связи, при котором каждому экземпляру сущности А может соответствовать ни одного, один или несколько экземпляров сущности Б, и наоборот.
	
	Информацию о проекте оформляют составлением спецификаций по сущностям, атрибутам и отношениям с использованием  графических диаграмм. На диаграмме обозначают:
	сущности - прямоугольниками;
	атрибуты - овалами, соединяя их с соответствующими сущностями ненаправленными ребрами; идентифицирующие атрибуты подчеркиваются;
	связи (отношения) - ромбами, соединяя их с соответствующими сущностями ненаправленными ребрами, за исключением бинарных связей, которые соединяются направленными ребрами.
	При моделировании используются следующие общие правила:
	используются только три типа конструктивных элементов - сущность, атрибут и связь;
	в отдельном проектном представлении каждый компонент информации моделируется только одним конструктивным элементом, то есть необходимо избегать избыточности.

Структурный подход при разработке инфологической модели

Сущность структурного подхода к разработке ИС заключается в ее декомпозиции (разбиении) на автоматизируемые функции: система разбивается на функциональные подсистемы, которые в свою очередь делятся на подфункции, подразделяемые на задачи и так далее. Процесс разбиения продолжается вплоть до конкретных процедур. При этом автоматизируемая система сохраняет целостное представление, в котором все составляющие компоненты взаимоувязаны. При разработке системы "снизу-вверх" от отдельных задач ко всей системе целостность теряется, возникают проблемы при информационной стыковке отдельных компонентов. При моделировании предметной области проектировщик разбивает ее на ряд локальных областей, моделирует каждое локальное представление, а затем их объединяет.
 
Моделирование локальных представлений
Выбор локального представления зависит от масштабов предметной области. Для удобства проектирования желательно использовать в отдельных локальных представлениях шесть - семь сущностей.
1.	Формулирование сущностей
На этом этапе необходимо указать типы объектов, о которых нужно хранить информацию. Иногда это сложно сделать, так как отдельный объект можно представить и в виде сущности, и в виде атрибута и в виде связи. Тогда следует проработать несколько вариантов моделей и выбрать наиболее гибкий.
Каждой выбранной сущности должно быть присвоено четкое наименование. Общее их количество не должно быть большим.
2.	Выбор идентифицирующего атрибута для каждой сущности.
Необходимо для каждой сущности указать идентификатор, позволяющий однозначно распознавать экземпляры сущности. Это один или несколько атрибутов, называемых ключом. Если в наборе атрибутов такого нет, то его надо ввести. Обычно в этом случае для каждого экземпляра сущности вводится внутренний номер, не имеющий смысла вне системы. Он называется суррогатным ключом. 
Один и тот же набор объектов может иметь несколько ключей. Один из них является первичным. Это ключ, который однозначно идентифицирует отдельные экземпляры сущности. Первичный ключ должен включать в свой состав минимальное количество атрибутов. Ключ, состоящий их нескольких атрибутов, называется составным.  
3.	 Назначение сущностям описательных атрибутов
Спецификация атрибутов заканчивается указанием для каждого атрибута множества значений, которые он может принимать. Если это множество бесконечное, то оно задается указанием типа значений (числовой, символьный и пр.) и диапазона значений для чисел и количества символов для алфавитно-цифровых значений.
4.	Спецификация связей 
Выявляются зависимости между двумя и более сущностями. Определяется какие из них необходимые, какие избыточные. Каждый тип связи именуется. 
  
Рассмотрим понятие класс принадлежности сущности.
Если каждый экземпляр сущности А связан с экземпляром сущности В, то класс принадлежности сущности А является обязательным. Это отмечается на ER-диаграмме черным кружком, помещённым в прямоугольник, смежный с прямоугольником сущности А.
Если не каждый экземпляр сущности А связан с экземпляром сущности В, то класс принадлежности сущности является необязательным. Это отмечается на ER-диаграмме черным кружком, помещённым на линии связи возле прямоугольника сущности А.

Правила преобразования ER-диаграмм в реляционные таблицы

Концептуальные модели позволяют более точно представить предметную область, чем реляционные и другие более ранние модели. Но в настоящее время существует немного СУБД, поддерживающих эти модели. На практике наиболее распространены системы, реализующие реляционную модель. Поэтому необходим метод перевода концептуальной модели в реляционную. Такой метод основывается на формировании набора предварительных таблиц из ER-диаграмм.
Для каждой сущности создается таблица. Причем каждому атрибуту сущности соответствует столбец таблицы.
Правила генерации таблиц из ER-диаграмм опираются на два основных фактора – тип связи и класс принадлежности сущности. Изложим их.
Правило 1: Если связь типа 1:1 и класс принадлежности обеих сущностей является обязательным, то необходима только одна таблица. Первичным ключом этой таблицы может быть первичный ключ любой из двух сущностей.
Правило 2: Если связь типа 1:1 и класс принадлежности одной сущности является обязательным, а другой - необязательным, то необходимо построить таблицу для каждой сущности. Первичный ключ сущности должен быть первичным ключом соответствующей таблицы. Первичный ключ сущности, для которой класс принадлежности является необязательным, добавляется как атрибут в таблицу сущности с обязательным классом принадлежности.
Правило 3: Если связь типа 1:1 и класс принадлежности обеих сущностей необязательный, то необходимо построить три таблицы - по одной для каждой сущности и одну для связи. Первичный ключ сущности должен быть первичным ключом соответствующей таблицы. Таблица для связи среди своих атрибутов должна иметь ключи обеих сущностей.
Правило 4: Если связь типа 1:М и класс принадлежности сущности на стороне М является обязательным, то необходимо построить таблицу для каждой сущности. Первичный ключ сущности должен быть первичным ключом соответствующей таблицы. Первичный ключ сущности на стороне 1 добавляется как атрибут в таблицу для сущности на стороне М.
Правило 5: Если связь типа 1:М и класс принадлежности сущности на стороне М является необязательным, то необходимо построить три таблицы - по одной для каждой сущности и одну для связи. Первичный ключ сущности должен быть первичным ключом соответствующей таблицы. Таблица для связи среди своих атрибутов должна иметь ключи обеих сущностей.
Правило 6: Если связь типа М:N, то необходимо построить три таблицы - по одной для каждой сущности и одну для связи. Первичный ключ сущности должен быть первичным ключом соответствующей таблицы. Таблица для связи среди своих атрибутов должна иметь ключи обеих сущностей. 