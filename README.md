# Balance Telegram Bot
Этот бот записывает всех вошедших в чат пользователей и выдаёт им каждый день какое-то количество монет. Пользователи могут переводить монеты друг другу с помощью команды /send и смотреть баланс командой /balance. Если пользователь выходит из чата, он автоматически удаляется из базы данных.

Раз в несколько действий (переводов между пользователями и просмотров баланса) бот отправляет в чат рекламное сообщение или несколько сообщений, текст которого берёт из json файла, имеющего URL-адрес.
## Настройка
### Рекламные сообщения
Первым делом заполните шаблон для сообщений, он есть в этом репозитории с название messages.json. Затем, загрузите его куда-нибудь, куда бот сможет сделать http запрос и получить данные. Я использовал [Github Pages](https://pages.github.com/).

[Вот пример моей настройки.](https://davisdmitry.github.io/get_msg_plaguecasino/messages.json)
### Конфигурация
`logging_level = logging.INFO` - уровень логгирования

`bot_token = os.environ.get('BOT_TOKEN')` - токен бота, берётся из переменной окружения

`aviable_chats = []` - id чатов, в которых будет работать бот / массив чисел

`counter_max = 25` - количество действий, через которое будут выводиться рекламные сообщения / число

`messages_url = ''` - URL json файла с настройками рекламных сообщений / строка

`everyday_money = 5000` - количество монет, которое будет выдаваться пользователям в чате каждый день / число
### Venv
Создайте виртуальное окружение и установите зависимости из файла requirements.txt. Затем, задайте переменную окружения BOT_TOKEN.
### База данных
Чтобы создать базу данных активируйте виртуальное окружение и запустите python. Исполните код:

`from models import User`

`User.create_table()`

`exit()`

База данных создана.
## Применяемые библиотеки
- Aiogram - для работы с Telegram Bots API
- SQLite3 - в качестве базы данных
- Peewee - ORM для работы с БД