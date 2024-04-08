ubuntu_kittygram_project - это проект Kittygram реализованный на удаленном сервере под управлением UBUNTU использующий для работы код Frontend(React) и Backend(Python). Данный проект позволяет выкладывать фото своих котов и список их достижений. Проект поддерживает весь функционал CRUD а также работу с медиафайлами. Доменное имя проекта реализовано под управлением No-Ip и имеет сертификат шифрования от Cerbot.

Как запустить проект на удаленном сервере:

Шаг 1: Настройка сервера:

Если вы работаете на Windows, создайте отдельную директорию, например, "vm_access", и поместите в нее текстовый файл и SSH-ключи.
Если вы работаете на Linux или macOS, сохраните текстовый файл в удобном для вас месте. Создайте новую директорию в скрытой директории .ssh для открытого и закрытого SSH-ключей. Выполните следующие команды в терминале:

cd ~/.ssh
mkdir имя-директории
chmod 600 имя-файла-закрытого-SSH-ключа
chmod 644 имя-файла-открытого-SSH-ключа.pub

Шаг 2: Подключение к серверу:

Используйте команду ssh с указанием пути к файлу с SSH-ключом:
ssh -i путь-к-файлу-с-SSH-ключом/имя-файла-с-SSH-ключом-без-расширения login@ip
Введите пароль:
Enter passphrase for key 'D:/Dev/vm_access/yc-user':

Шаг 3: Подключение сервера к аккаунту на GitHub:

Установите Git на сервер.
Добавьте публичный SSH-ключ сервера в настройки вашего аккаунта на GitHub.

Шаг 4: Клонирование проекта на сервер:
Выполните команду git clone, указав ссылку на репозиторий:
git clone git@github.com:ваш-аккаунт/ubuntu_kittygram_project.git

Шаг 5: Запуск бэкенд-приложения:
Установите на сервер необходимые компоненты: интерпретатор Python, менеджер пакетов pip и утилиту для создания виртуального окружения venv:
sudo apt install python3-pip python3-venv -y
python3 -m venv venv
source venv/bin/activate

Установите зависимости из файла requirements.txt:
pip install -r requirements.txt

Выполните миграции:
python manage.py migrate
python manage.py createsuperuser
Настройте файл settings.py.

Шаг 6: Запуск фронтенд-приложения:
Установите на сервер пакетный менеджер npm.
Установите зависимости для фронтенд-приложения.

Шаг 7: Объединение работы Frontend и Backend:
Настройте работу демона Gunicorn.
Настройте работу Nginx.
Пропишите соответствующие настройки в файле конфигурации DEFAULT.
Зарегистрируйте и получите доменное имя.
Привяжите доменное имя.

Шаг 8: Настройка безопасности и мониторинга приложения:
Настройте шифрование HTTPS.
Настройте мониторинг в Sentry.

После выполнения всех этих шагов вы должны быть готовы запустить проект Kittygram на удаленном сервере под управлением Ubuntu.
