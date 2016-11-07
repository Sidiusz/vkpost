Автоматический загрузчик видеофайлов vk "vkpost" в группы и аккаунты.

Автор основного javascript кода: Seiya Loveless. 
Автор batch скрипта и этого описания: Corak the Avatar

Что делать:
1. Ввести токен:
Прежде всего необходимо получить token управления видеороликами с вашего текущего аккаунта (в который вы залогинены).
a. Для этого пройдите по ссылке
https://oauth.vk.com/authorize?client_id=4218952&display=page&redirect_uri=https%3A%2F%2Fvk.com%2Fblank.html&response_type=token&scope=video,groups,offline
b. Разрешите доступ.
c. Дальше из адресной строки скопируйте токен, это цифро-буквенный набор - все что после "#access_token=" до "&expires_in=0":
У вас должен получиться примерно такой, но ваш собственный токен:
d687c545657f87994f2d61266fff88ebf26a65f6388764fd608f78d7110f7f7f9847bf87187b18f6fe01d

Можете добавить его в переменную в "upload_video_vk_all.bat" файле
в строке:
set token=

или в файл конфигурации "scripts\config\vkpost.json" в строку access_token, между пустыми ковычками:
"access_token": "",

2. Пути к файлам:
В "upload_video_vk_all.bat" файле измените адреса к файлам iojs.exe и vkpost.js,
в строках:
set iojs=e:\Work\Seiya\iojs\iojs.exe
set vkpost=e:\Work\Seiya\scripts\vkpost.js

3. Видео в группу:
Если вы хотите, чтобы видео было загружено в группу, то измените параметр
set groupid=
Там введите id номер вашей группы.
Его можно получить из любой ссылки поста на стене, например если это "vk.com/wall-62542735_1042", то id адрес вашей группы 62542735. Его и копируйте туда.

4. Разместить bat файл.
Далее можете просто скопировать .bat файл в любую папку с видеороликами и далее просто запустить его. Видео будут загружены.

5. Видео в подпапках.
Если вы хотите, чтобы были загружены все видео, находящиеся внутри других папок, кроме текущей, то добавьте параметр /r после for. То есть измените строку
for %%G in (%ext%) do (
на
for /r %%G in (%ext%) do (
Это позволит загружать все видеофайлы, которые находятся в подпапках текущей папки, где у вас размещен bat файл.

6. Логи.
После загрузки видеофайлов, будут созданы логи в файле log.txt. Там можно просмотреть статус загрузки видео, какие видеофайлы не были загружены из-за какой-то ошибки (например видео заблокировано по копирайтам) или ваш аккаунт заблокирован, или его возможность загружать видео (на месяц или более) за загрузку некоторого количества свежезаблокированных видео. 
Если в вашем аккаунте заблокирована возможность загружать видео, то подождите примерно месяц, пока эту возможность не разблокируют или используйте другой аккаунт и повторите с ним операцию по добавлению токена (пункт 1).
