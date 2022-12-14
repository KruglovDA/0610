#Подробнее о Git

Git (произносится «гит») — распределённая система управления версиями. Проект был создан Линусом Торвальдсом для управления разработкой ядра Linux, первая версия выпущена 7 апреля 2005 года. На сегодняшний день его поддерживает Джунио Хамано.

Среди проектов, использующих Git — ядро Linux, Swift, Android, Drupal, Cairo, GNU Core Utilities, Mesa, Wine, Chromium, Compiz Fusion, FlightGear, jQuery, PHP, NASM, MediaWiki, DokuWiki, Qt, ряд дистрибутивов Linux.

Git — система управления версиями с распределенной архитектурой. В отличие от некогда популярных систем вроде CVS и Subversion (SVN), где полная история версий проекта доступна лишь в одном месте, в Git каждая рабочая копия кода сама по себе является репозиторием. Это позволяет всем разработчикам хранить историю изменений в полном объеме.
Git (читается как «гит») — это система контроля версий, которая помогает отслеживать историю изменений в файлах. Git используют программисты для совместной работы над проектами.

В самом простом виде контроль версий — это сохранение на компьютере серии измененных файлов, например с разными датами в названии, или режим отслеживания исправлений в текстовых документах.

Разработчикам часто бывает нужно вернуться к предыдущей версии кода:

- если оказывается, что решаемая задача больше не актуальна;
- если требуется внести исправления в более раннюю версию программы;
- если ошибка нашлась во время работы над новой задачей.


##Что внутри коммита?
Каждый раз, когда вы создаете файл и коммитите изменения, Git архивирует файл и сохраняет его в своей структуре данных. Архивированный объект создается с уникальным именем и хранится в папке объектов.

Перед изучением папки объектов уточним, что же такое коммит. Коммит — это слепок текущего состояния файлов в рабочей папке, но не только это.

По факту, когда вы коммитите изменения, Git производит всего два действия:
1. Если файл в рабочей папке не изменялся, он просто добавляет имя сжатого файла (хеш) в снимок.
2. Если файл в рабочей папке изменялся, он сжимает его, помещает в папку объектов и добавляет имя сжатого файла (хеш) в снимок.


**Коммит состоит из четырех вещей:**

1. Имя (хеш) снимка рабочей директории.
Комментарий.
2. Информация о том, кто выполнил коммит.
3. Хеш родительского коммита.
4. Git всегда подскажет разработчику, если тот запутался, например:

##Настройка
1. Команда git --help - выводит общую документацию по git
2. Если введем git log --help - он предоставит нам документацию по какой-то определенной команде (в данном случае это - log)
3. Если вы вдруг сделали опечатку - система подскажет вам нужную команду
4. После выполнения любой команды - отчитается о том, что вы натворили
5. Также Гит прогнозирует дальнейшие варианты развития событий и всегда направит разработчика, не знающего, куда двигаться дальше

##Определение состояния
status — это еще одна важнейшая команда, которая показывает информацию о текущем состоянии репозитория: актуальна ли информация на нём, нет ли чего-то нового, что поменялось, и так далее.

Для того, чтобы начать отслеживать новый файл, нужно его специальным образом объявить.

##Подготовка файлов
В git есть концепция области подготовленных файлов. Можно представить ее как холст, на который наносят изменения, которые нужны в коммите. Сперва он пустой, но затем мы добавляем на него файлы (или части файлов, или даже одиночные строчки) командой add и, наконец, коммитим все нужное в репозиторий (создаем слепок нужного нам состояния) командой commit.

##Базовые операции
1. **Создание локальной копии главного репозитория.** Для начала нужно перейти в каталог, в котором вы хотите, чтобы появился каталог репозитория, и запустить в нем терминал.
- Для пользователей Linux/MacOS: запустить Терминал и с помощью команды *cd* перейти в нужный каталог.
2. **Добавление новых файлов в репозиторий.** Давайте создадим в каталоге репозитория test текстовый файл first.txt, содержащий строку текста *"Some text"*. Однако то, что файл появился в каталоге репозитория не означает, что git его уже отслеживает. Нужно указать это явно командой git add first.txt.
- Теперь наш файл находится под наблюдением git. Давайте сохраним изменения в репозитории и сделаем первый коммит: 
*git commit -m "My first commit"* 
Ключ *-m* позволяет задать описание коммита. Описание обязательно, иначе коммит не будет выполнен. 
3. **Сохранение изменений файлов.** Добавим в файл *first.txt* еще одну строчку "Some more text" (не забудьте сохранить файл!). И снова закоммитим изменения.
Однако если мы воспользуемся известной нам командой *git commit -m "more text added to first.txt"* то мы получим сообщение, что коммитить в общем-то нечего. Почему? Дело в том, что git опять же не знает, какие именно из измененных файлов мы хотим сохранить.
- Чтобы указать это явно, необходимо воспользоваться описанной выше командой *git add*. В то же время самый частый сценарий сохранить изменения во всех
файлах. Для этих целей в команде git commit есть ключик *a*. 
- Итого наша команда будет такой: *git commit a m "more text added to first.txt"*
Чтобы меньше запоминать, вам будет достаточно для всех коммитов пользоваться командой именно такого вида. 
4. **Отправка изменений в главный репозиторий.** К этому моменту мы уже немало сделали в нашей локальной копии репозитория, однако если вы обновите вебстраничку с главным репозиторием, вы увидите, что в нем никаких изменений нет. Как их туда внести? Для этого используется команда *git push*. В процессе выполнения команды от вас потребуется ввести ваш и логин и пароль от аккаунта на GitHub. Когда после успешного завершения команды мы обновим страничку с главным репозиторием, мы увидим, что теперь его содержимое совпадает с нашим локальным репозиторием. 
5. **Получение изменений из главного репозитория**. Смоделируем ситуацию, в которой нам это пригодится. Для этого откроем еще один терминал в каталоге отличном от того, в котором лежит наш локальный репозиторий. И создадим еще одну локальную копию главного репозитория (как описано выше). Итого у нас
теперь есть два локальных репозитория: первый (старый) и второй (только что созданный). Представим, что второй репозиторий на самом деле находится на другом компьютере и с ним работает второй участник. И он решает внести какие-то изменения в файл *first.txt*, находящийся в его локальной копии, т.е. во втором репозитории.
- Сохраняем файл и коммитим: *git commit a m "more changes in first.txt"* и отправляем изменения на сервер: *git push*.
- Сейчас у нас синхронизированы главный и второй локальный репозитории, но первый локальный отстает. Ему нужно получить изменения из главного
репозитория командой *git pull*.
6. **Разрешение конфликтов.** В заключение рассмотрим еще один частый сценарий, распространенный при одновременной работе нескольких человек. Давайте в нашем первом локальном репозитории внесем еще какиe-нибудь изменения в файл *first.txt*, закоммитим и отправим их в главный репозиторий. А затем во втором локальном репозитории создадим файл *second.txt* и тоже закоммитим. Однако если теперь из второго репозитория мы попробуем сделать *git push*, то получим ошибку из-за конфликта изменений. Почему?
- Для простоты можно считать, что при отправке изменений в локальном репозитории должна быть версия, основанная на версии главного репозитория. Тогда как мы во втором репозитрии пока ничего не знаем про последний коммит *first.txt*. Что делать? - Сначала нам нужно получить изменения из главного репозитория, затем объединить их с нашими
изменениями, и то, что получилось, отправить на главный репозиторий. Звучит непросто, но на самом деле первые два шага сама умеет делать команда *git pull*. Она достаточно умна, чтобы понять, что в нашем случае надо обновить файл *first.txt* и добавить *second.txt*. После чего нам остается просто отправить изменения командой *git push*. 
Итого получаем, что при отправке изменений безопасно пользоваться двумя последовательными командами: 
- *git pull* (проверить на наличие новых изменений в репозитории и, если они есть, выкачать их и объединить с локальными изменениями)
- *git push* (отправить изменения в репозиторий)
- Таким образом, git умеет разрешать конфликты самостоятельно. Но к сожалению, не все. Если бы мы вместо создания *second.txt* во втором репозитории тоже изменили *first.txt*, то мы бы имели две измененные версии одного файла и здесь уже *git* самостоятельно разрешить конфликт не может: нужно вмешательство человека.

## Работа с удалённми репозиториями
Для того, чтобы внести вклад в какой-либо Git-проект, вам необходимо уметь работать с удалёнными репозиториями. Удалённые репозитории представляют собой версии вашего проекта, сохранённые в интернете или ещё где-то в сети. У вас может быть несколько удалённых репозиториев, каждый из которых может быть доступен только для чтения или для чтения/записи.

#### git fetch
Команда git fetch связывается с удалённым репозиторием и забирает из него все изменения, которых у вас пока нет и сохраняет их локально.

#### git pull
Команда git pull работает как комбинация команд git fetch и git merge, т. е. Git вначале забирает изменения из указанного удалённого репозитория, а затем пытается слить их с текущей веткой.

#### git push
Команда git push используется для установления связи с удалённым репозиторием, вычисления локальных изменений отсутствующих в нём, и собственно их передачи в вышеупомянутый репозиторий. Этой команде нужно право на запись в репозиторий, поэтому она использует аутентификацию.

#### git remote
Команда git remote служит для управления списком удалённых репозиториев. Она позволяет сохранять длинные URL репозиториев в виде понятных коротких строк, например «origin», так что вам не придётся забивать голову всякой ерундой и набирать её каждый раз для связи с сервером. Вы можете использовать несколько удалённых репозиториев для работы и git remote поможет добавлять, изменять и удалять их.

#### git archive
Команда git archive используется для упаковки в архив указанных коммитов или всего репозитория.

#### git submodule
Команда git submodule используется для управления вложенными репозиториями. Например, это могут быть библиотеки или другие, используемые не только в этом проекте ресурсы. У команды submodule есть несколько под-команд —add, update, sync и др. — для управления такими репозиториями.