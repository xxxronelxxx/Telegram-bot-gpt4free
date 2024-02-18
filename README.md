# Telegram-bot-gpt4free
Telegram bot ChatGPT based on gpt4free
Инструкция по созданию телеграм-бота на Linux Ubuntu в картинках для самых маленьких

Для начала идем в телеграм-бот @BotFatherи пишем команду /newbot; далее выбираем название бота. Следующим сообщением нужно выбрать username — в конце обязательно нужно указать _bot по принципу, как сделано на скриншоте. Все, ваш бот создан.
Копируем токен бота в код.

# Инициализация бота
API_TOKEN = 'ВАШ ТОКЕН ТЕЛЕГРАМ'
bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)

Далее сразу нужно создать кнопку в меню для очистки истории диалога, чтобы потом не возвращаться к этому. Пишем команду /mybots. Выбираем свой бот. Нажимаем Edit bot, далее Edit commands. Затем пишите clear — очистка истории сообщений. Теперь при написании команды или выборе в меню /clear будет очищаться диалог с пользователем.

Запускаем Putty и подключаемся к серверу либо из терминала:

git clone https://github.com/xxxronelxxx/Telegram-bot-gpt4free.git
cd Telegram-bot-gpt4free

Обновляем список пакетов:

sudo apt update
По умолчанию в ubuntu уже установлен Python, проверяем командой:

python3 --version
pip3 --version
Обычно менеджер пакетов pip3 не установлен в Ubuntu, устанавливаем командой:

sudo apt install python3-pip
Также установите виртуальное окружение venv командой:

sudo apt install python3.10-venv
Далее убедитесь, что вы находитесь в нужной вам папке. Если нет — воспользуйтесь командой cd, а также командой ls и проверьте, содержатся ли в папке нужные вам файлы.

Создаем виртуальное окружение внутри папки:

python3 -m venv venv
Активируйте виртуальное окружение командой:

source venv/bin/activate
Установите необходимые библиотеки командой:

pip install -r requirements.txt
Теперь нужно сделать так, чтобы бот автоматически запускался и был активен при старте сервера. Идем в папку /etc/systemd/system/ и создаем любым удобным вам образом, я рекомендую через winSCP. Файл tgbot.service, в нем пишем:

[Unit]\
Description=My Telegram bot\

[Service]\
WorkingDirectory=/tgbot/\
User=ИМЯ ПОЛЬЗОВАТЕЛЯ ЗАМЕНИТЕ НА СВОЕ\
ExecStart=/tgbot/venv/bin/python3 /tgbot/main.py\

[Install]
WantedBy=multi-user.target
Замените в тексте имя пользователя на свое, а также tgbot замените на вашу директорию с папкой.

Далее используйте следующие команды:

sudo systemctl daemon-reload
sudo systemctl start tgbot.service
sudo systemctl enable tgbot.service
Ваш бот готов, чтобы проверить его статус, используйте команду:

sudo systemctl status tgbot.service

### Список моделей
GPT-4
g4f.Provider.Bing
g4f.Provider.FreeChatgpt
g4f.Provider.Liaobots
g4f.Provider.OpenaiChat
g4f.Provider.Raycast
g4f.Provider.Theb
g4f.Provider.GeekGpt

Доступный список всех моделей: https://github.com/xtekky/gpt4free?tab=readme-ov-file#gpt-4
