---
title: Лабораторная работа. Алгоритмы шифрования. Хэширование. Статическая и динамическая соль
---

[К списку лабораторных >>>](../README.md)

---

### Задания

1. 
2. Если вы хотите больше узнать о том, насколько быстрыми могут быть таблицы поиска, попробуйте взломать следующие sha256 хеш-коды с помощью бесплатного хеш-взломщика от CrackStation.
3. Вы можете сгенерировать собственный хеш-код вашего наиболее часто используемого пароля здесь и попробовать взломать его с помощью упомянутого выше инструмента.

---

### [Хеш-функции](https://www.internet-technologies.ru/articles/solenoe-heshirovanie-paroley-delaem-pravilno.html#header-9283-2)

Базы данных учетных записей пользователей часто взламываются, 
поэтому вы однозначно должны сделать что-то для защиты паролей ваших пользователей на случай, если ваш сайт будет взломан.

Самым лучшим способом защиты паролей является «соленое» хеширование пароля. 

hash("hello") = 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
hash("hbllo") = 58756879c05c68dfac9866712fad6a93f8146f337a69afe7dd238f3364946366
hash("waltz") = c0e81794384491161f1777c232bc6bd9ec38f616560b120fda8e90f383853542

Хеш-алгоритмы являются односторонними функциями. 
Они превращают любое количество данных в «дактилоскопический отпечаток» фиксированной длины,
который не может быть обратим.

Также эти алгоритмы имеют такое свойство, что если входное значение изменяется даже совсем немного, 
полученный хеш-код полностью отличается от исходного (смотрите пример выше).

Это отлично подходит для защиты паролей, потому что мы хотим сохранить пароли в зашифрованном виде,
невозможном для расшифровки, и в то же время мы должны быть способны проверить то, 
что пароль пользователя корректен.

Общая схема процесса регистрации аккаунта и аутентификации 
в системе учетных записей, основанной на хешировании, выглядит следующим образом:

1. Пользователь создает учетную запись;
2. Вычисляется хеш-код от пароля и сохраняется в базе данных. Нет никакого смысла в пароле, записанном в обычном текстовом (незашифрованном) формате на жесткий диск;
3. Когда пользователь пытается войти в систему, хеш-код, вычисленный от пароля, который он ввел, сравнивается с хеш-кодом реального пароля (извлеченным из базы данных);
4. Если хеш-коды совпадают, пользователю предоставляется доступ. Если нет – пользователю сообщается, что он ввел неверные данные для входа в учетную запись;

Шаги 3 и 4 повторяются каждый раз, когда кто-либо пытается войти в свой аккаунт.
На шаге 4 никогда не сообщайте пользователю, что именно не так: имя пользователя или пароль. 
Всегда отображайте только общее сообщение, например, «Неверное имя пользователя или пароль». 
Это не позволит злоумышленникам вычислить верные имена пользователей без знания их паролей.

Следует отметить, что хеш-функции, используемые для защиты паролей, это не те же хеш-функции, 
которые вы могли видеть на занятиях по структурам данных. 
Хеш-функции, используемые для реализации структур данных, 
таких как хеш-таблицы, разрабатываются для того, чтобы быть быстрыми, а не безопасными.

Только криптографические хеш-функции могут быть использованы для реализации хеширования паролей. 
Такие функции, как SHA256, SHA512, RipeMD и WHIRLPOOL являются криптографическими хеш-функциями.

Легко подумать, что все, что вы должны сделать, это пропустить пароль через криптографическую хеш-функцию, 
и пароли ваших пользователей будут в безопасности. Это далеко от правды. 
Есть много видов атак, позволяющих очень быстро восстановить пароли из простых хеш-кодов.

### Как взламывается хеш

Самый простой способ взломать хеш-код – это попробовать угадать пароль, 
вычисляя хеш-код для каждого предположения и проверяя, совпадает ли этот хеш-код со взламываемым.

Если хеш-коды одинаковые, то предположенная комбинация является паролем. 
Двумя наиболее распространенными способами угадывания паролей является атаки по словарю и атаки полным перебором.

#### Атака по словарю

Атака по словарю использует файл, содержащий слова, фразы, распространенные пароли и другие строки,
которые с некоторой вероятностью могут быть использованы в качестве пароля. 
Каждое слово в файле захешировано, и его хеш-код сравнивается с хеш-кодом пароля.

Если они совпадают, то данное слово является паролем. 
Такие файлы словарей построены путем извлечения слов из больших массивов текста и даже из реальных баз данных паролей. 
Часто применяется дополнительная обработка файлов словарей, 
например, замена слов «лит спик» эквивалентами ("hello" становится "h3110"), чтобы сделать их более эффективными.

#### Атака полным перебором

Атака полным перебором пробует все возможные комбинации символов до заданной длины. 
Эти атаки требуют очень больших вычислительных затрат, и, как правило, 
они наименее эффективны по показателю число взломанных хеш-кодов на время выполнения, 
но они всегда в конечном счете находят пароль.

Пароли должны быть достаточной длины, чтобы поиск по всем возможным символьным
строкам для его нахождения занимал слишком много времени, чтобы оправдывать себя.

Не существует методов предотвращения атак по словарю или атак полным перебором. 
Можно сделать их менее эффективными, но нет способа предотвратить их полностью. 
Если ваша система хеширования паролей безопасна, 
единственный способ взломать хеш-коды – это выполнить атаку по словарю или полным перебором для каждого хеш-кода.

### Таблицы поиска

Таблицы поиска – это крайне эффективный метод для очень быстрого взлома большого количества хеш-кодов одного типа. Основная идея заключается в том, чтобы заранее вычислить хеш-коды паролей из словаря паролей, а затем сохранить хеш-коды и соответствующие им пароли в структуру данных типа таблица поиска.

Умело реализованные таблицы поиска могут обрабатывать сотни поисков хеш-кодов в секунду, даже если они содержат много миллиардов хеш-кодов.

### Обратные таблицы поиска

Этот вид атаки позволяет злоумышленнику применить атаку по словарю или полным перебором ко многим хеш-кодам одновременно без наличия предварительно вычисленной таблицы поиска.

Сначала злоумышленник создает таблицу поиска, которая сопоставляет каждый хеш-код пароля из скомпрометированной базы данных пользовательских аккаунтов со списком пользователей, имевших этот хеш-код. Затем взломщик хеширует каждый предполагаемый пароль и использует таблицу поиска для получения списка пользователей, чей пароль был угадан взломщиком.

Этот вид атак особенно эффективен, потому что зачастую несколько пользователей имеют один и тот же пароль.


### Радужные таблицы

Радужные таблицы – это техника, являющаяся компромиссом между временем поиска и занимаемой памятью. 
Они похожи на таблицы поиска, за исключением того, что они жертвуют скоростью взлома хеш-кодов, чтобы сделать таблицы поиска меньше.

Так как таблицы меньше, решения для большего количества хеш-кодов могут быть сохранены в том же объеме памяти,
делая такие таблицы более эффективными. Существуют радужные таблицы, 
которые могут взломать любой md5 хеш-код пароля вплоть до 8 символов в длину.

Несмотря на основной замысел хеш-функции, полностью необратимыми назвать их сложно. 
Во всяком случае, это относится к тем функциям, которые существуют уже долгое время
и были изучены насколько это возможно. Их частое использование стало причиной создания радужных таблиц.

Если коротко и просто, то радужные таблицы – это таблицы, которые содержат расшифровки некоторых хеш-значений.
Сам по себе процесс создания таких таблиц гораздо сложнее, чем кажется, 
ведь расшифровать хеш-значение в обратную сторону проблематично. 
Тем не менее, хакеры могут прибегнуть к использованию таких таблиц. 
Имея доступ к хеш-таблице с паролями по радужной таблице можно довольно просто вычислить пароль.

### Статическая и динамическая «соль»

Для защиты от радужных таблиц специалисты по безопасности разработали достаточно простое решение: 
вместе с основными данными на вход подается еще одна строка, именуемая как «соль». 
За счет этого получается совершенно другое хеш-значение, которое не найти в стандартных радужных таблицах.

Различают статическую и динамическую «соль». 

#### Статическая «соль»

Статическая «соль» – это строка данных, которая будет одинаковой для всех входных данных.
При этом, если злоумышленник узнает значение «соли»,
то он сможет создать радужные таблицы на основе этих данных, 
из-за чего рекомендуется применять динамическую «соль».

#### Динамическая «соль»

Динамическая «соль» – это такая строка данных, которая генерируется для каждого значения индивидуально. 
Это обеспечивает безопасность и тем пользователям, чьи пароли совпадают, 
так как их хеш-значения будут разными. К тому же в создании хеш-значений
с динамической «солью» применяются алгоритмы, которые добавляют новую строку данных 
в разные части входного значения и на разных итерациях хеширования.

Таким образом, процесс подбора паролей будет выглядеть следующим образом:

1. Нет соли — используем уже готовые радужные таблицы.
2. Есть одна на всех соль — генерируем одну радужную таблицу и «ломаем» по ней всех пользователей.
3. Есть отдельная соль для каждого пользователя — отдельно брутфорсим каждого пользователя, что уже значительно сложнее

### Использование «соли»

Не имеет значения, до или после пароля идет «соль», 
можно выбрать что-то одно и придерживаться этого варианта для обеспечения совместимости.
В большинстве случаев принято располагать «соль» перед паролем.
Например, стандартный алгоритм сравнения строк "xyzabc" и "abcxyz" немедленно обнаружит, 
что первые символы отличаются, и не потрудится проверить оставшуюся часть строки. 
С другой стороны, при сравнении строк "aaaaaaaaaaB" и "aaaaaaaaaaZ", 
алгоритм сравнения просматривает последовательность символов "a" прежде, чем определит, что строки неодинаковы.

Из всего существующего самым «популярным» является сохранение пароля 
в базе в виде md5(md5(password)+salt), при этом соль хранится в базе в соседней колонке (ну или в той же колонке где и хэш).
Такой способ конечно усложняет взлом пароля, но имея хеш и соль взломать все равно можно.

Есть смысл использовать динамическую соль в виде:

1. хешируем пароль: hash1 = md5(password)
2. в качестве соли берем допустим 10 символом от хеша hash1
3. получаем итоговый хэш по старому алгоритму: md5(md5(password)+salt), или
md5( md5(password)+substr(md5(password),0,10) )

Если уж хочется чего-то «хитро-изварщенного», то можно хранить в базе что-то такое:

substr(md5(md5 (<динамическая соль> . $password)  .  <статическая соль>), 0, 16);

где динамическая соль будет вычисляться так, например:

substr($login, 0, 3) . ($password, 1, 5) . $login[4] .$password[0] .  <статическая соль> 

Однако, будет лучше, если соль будет сгенерирована при помощи криптографически стойкого генератора псевдослучайных чисел 
(англ. Cryptographically secure pseudorandom number generator, CSPRNG).
Такие генераторы сильно отличаются от обычных генераторов псевдослучайных чисел, наподобие функции rand() в языке C.

Как следует из названия, криптографически стойкие генераторы предназначены быть криптографически надежными,
в том смысле, что они обеспечивают высокий уровень случайности и совершенно непредсказуемы.

Мы не хотим, чтобы наша соль была предсказуема, поэтому мы и должны использовать криптографически стойкий генератор.
На платформе .NET (C#, VB.NET) используется генератор (System.Security.Cryptography.RNGCryptoServiceProvider](http://msdn.microsoft.com/ru-ru/library/system.security.cryptography.rngcryptoserviceprovider.aspx)

Таким образом, для повышения уровня безопасности соль должна быть своя для каждого пользователя и пароля. 
Каждый раз, когда пользователь создает учетную запись или изменяет свой пароль, 
пароль должен быть захеширован с помощью новой случайной соли. 
Никогда не используйте соль повторно.

Также соль должна быть длинной, поэтому существует очень много возможных вариантов. 
Опираясь на жизненный опыт, следует использовать соль, по меньшей мере, той же длины, что и выход хеш-функции.
Соль должна быть сохранена в таблице учетных записей пользователей вместе с хеш-кодом.

### Работа с паролем

Сохранение пароля:

1. Генерируем длинную случайную соль, используя криптографически стойкий генератор псевдослучайных чисел;
2. Присоединяем соль к паролю и вычисляем хеш-код с помощью стандартной криптографической хеш-функции, например, SHA256;
3. Сохраняем и соль, и хеш-код в записи базы данных пользователей.

Проверка пароля:

1. Извлекаем соль и хеш-код пользователя из базы;
2. Добавляем соль к введенному паролю и вычисляем хеш-код с помощью той же самой функции;
3. Сравниваем хеш-код введенного пароля с хеш-кодом из базы данных. Если они совпадают, пароль верен. В противном случае, пароль введен неправильно.

[Образец кода для хеширования пароля на ASP.NET (C#)](https://crackstation.net/hashing-security.htm#aspsourcecode)

### Использование нескольких хеш-функций 

Некоторые могут поспорить, что использование нескольких хеш-функций делает 
процесс вычисления хеш-кодов более медленным, поэтому дешифрование становится медленнее, 
однако, как мы увидим позже, существует более разумный способ сделать процесс взлома более медленным.

Ниже приведены некоторые примеры чокнутых хеш-функций, взятые с просторов Интернета:

md5(sha1(пароль))
md5(md5(соль) + md5(пароль))
sha1(sha1(пароль))
sha1(str_rot13(пароль + соль))
md5(sha1(md5(md5(пароль) + sha1(пароль)) + md5(пароль)))

Не используйте ни одну из них.

Бытует мнение, что замудренные хеш-функции – это хорошая вещь, потому что лучше, 
если злоумышленник не знает, какая хеш-функция используется.

Тогда менее вероятно наличие у злоумышленника предварительно вычисленных радужных таблиц для мудреной хеш-функции, 
и вычисление хеш-функции занимает больше времени.

Злоумышленник не может атаковать хеш-код, когда он не знает алгоритм, но учитывая принцип Керкгоффса,
взломщик обычно обладает доступом к исходному коду (особенно если это приложение бесплатное или с открытым исходным кодом),
и ему известны несколько пар пароль/хеш-код из целевой системы,
поэтому не составляет никакого труда выполнить реверсивное программирование алгоритма.

Вычисление мудреных хеш-функций действительно занимает больше времени,
но только с небольшим константным коэффициентом. Лучше использовать итеративный алгоритм,
спроектированный так, чтобы его было очень сложно распараллелить (такие алгоритмы обсуждаются ниже).
А, добавление соли в хеш-код, выполненное должным образом, решает проблем радужных таблиц.

### Коллизии хеш-функций

Так как хеш-функции отображают произвольное количество данных в строке фиксированной длины,
должны существовать такие входные данные, хеш-коды которых совпадают. 
Криптографические хеш-функции разработаны так, что такие коллизии встретить невероятно трудно. 
Время от времени криптографы находят «атаки» на хеш-функции, которые облегчают нахождение коллизий.

Недавний пример – это хеш-функция алгоритма MD5, для которой действительно были найдены коллизии.

Атаки коллизии – это признак того, что существует вероятность наличия для строки,
отличной от пароля пользователя, точно такого же хеш-кода. 
Однако нахождение коллизий даже в такой слабой хеш-функции как MD5 требует большой вычислительной мощности, 
поэтому маловероятно, что такие коллизии «нечаянно» произойдут на практике.

Пароль, захешированный с помощью MD5 и соли, так же надежен, для всех практических целей, 
как если бы он был захеширован при помощи SHA256 и соли. 
Тем не менее, неплохо использовать и более безопасные хеш-функции,
такие как SHA256, SHA512, RipeMD или WHIRLPOOL, если это возможно.

ВЕРНЫЙ способ: как производить хеширование правильно

Какую угрозу несут коллизии?
Хеш-функции используются для проверки неизменности входных данных. 
Хешируя входные данные, мы получаем единственное соответствующее им значение.
Нетрудно догадаться, что будет, если мы получим одно и то же значение при разных входных данных: станет возможна подмена.

Наиболее очевидна опасность коллизий на примере хеш-таблиц, которые хранят пароли пользователей сайта. 
При получении доступа к этой таблице восстановить исходные данные невозможно, если хеш-функция необратима. 
Но если злоумышленник умеет искать коллизии, то ему не составит труда подобрать ложные пароли, 
которые система посчитает верными. Это не так сложно, учитывая,
что у хакеров действительно есть специальные методы по поиску коллизий, разработанные как под общие случаи, так и конкретные.

Не стоит также забывать, что хеш-функции используются для создания цифровых подписей,
подтверждения валютных операций и во многих других механизмах, требующих повышенной защищенности.

### Пример использования «соли» в алгоритмах хеширования

Представим простую авторизацию.
От пользователя к нам приходит связка значений логин/пароль,
мы получаем хеш пароля и сравниваем данную связку с данными, хранящимися в базе.
Для простоты будем использовать MD5 и примеры кода на PHP.
       $password = md5($password);

В данном случае, если у пользователя пароль qwerty, мы получим следующий хеш: d8578edf8458ce06fbc5bb76a58c5ca4. 
Если злоумышленник получит доступ к нашей базе, 
для подбора паролей он может воспользоваться уже готовыми сервисами(http://wordd.org/D8578EDF8458CE06FBC5BB76A58C5CA4),
в которых уже есть значения, дающие данный хеш, либо сбрутить самому.

Для защиты от уже готовых таблиц хешей с значениями, можно использовать статическую соль:
       $password = md5($password . "MyUniqueSault");

Сейчас при том же пароле qwerty мы получим совершенно другой хеш bdadb0330124cda0e8499c9cd118f7bd. 
Готовые таблицы уже не помогут злоумышленнику, ему придется использовать брутфорс. 
Вот здесь и кроется минус статической соли: злоумышленник сможет сгенерировать свою таблицу хешей
со статической солью и получить значения большинства паролей из базы. 
Для устранения этого минуса используется уникальная соль к каждому хешу:
       $sault = GenerateRandomString();
       $password = md5($password . $sault);

Т.е. теперь помимо логина/хеша пароля в базе необходимо будет хранить
значение сгенерированной соли для каждого пользователя. 
Разберем пример: у нас два пользователя: user1 и user2. Оба используют пароль qwerty. 
Но у первого была сгенерирована соль zxcv а у второго asdf. 
В итоге у пользователей при одинаковом пароле будут различные хеши: 1d8f3272b013387bbebcbedb4758586d и a192862aa3bf46dffb57b12bdcc4c199.

Что это дает: теперь нельзя будет сгененерировать одну таблицу хешей, 
для нахождения значения хеша с динамической солью придется генерировать заново.
Все это направлено на увеличение времени подбора значений в случае «слива» базы,
при использовании «хороших» алгоритмов хеширования,
на подбор хотя бы пары паролей уже может уйти значительное количество времени. 
Важно понимать, что генерируемая соль защищает не одного единственного пользователя, 
а всех вместе от массового брута. На этом все, хочу напомнить что 
используйте криптостойкие алгоритмы хеширования SHA1, SHA512. 

Используемый выше MD5 к использованию не желателен, т.к. признан устаревшим.

