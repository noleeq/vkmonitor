# VKMonitor — небольшой мониторинг сообществ VK

![VKMonitor (превью отчёта)](https://github.com/noleeq/vkmonitor/assets/140243180/65306e01-ec49-4036-a1a5-8a3ffc577470)

## Описание

VKMonitor — это небольшой асинхронный бот, написанный на Python, который использует API VK для мониторинга заданных сообществ и Telegram API для отправки отчетов со статистикой в чат Telegram.

Каждые 24 часа VKMonitor автоматически запускается и собирает статистику сообщества за последние сутки, включая полный охват, охват подписчиков, количество постов, количество рекламных постов, количество постов с бирж и количество подписавшихся или отписавшихся пользователей.

После сбора данных, VKMonitor отправляет отчет в структурированном виде в чат Telegram, который указан в конфигурационном файле. Вместе с каждым отчетом VKMonitor также отправляет изображение, связанное с сообществом в конфигурационном файле.

VKMonitor — необходимый инструмент для мониторинга статистики сообществ в VK, который позволяет автоматически собирать и отправлять данные в Telegram без необходимости ручного сбора данных.

## Требования

- Python 3.7 или выше
- aiogram
- aiovk
- APScheduler
- babel
- pymorphy3
- pytz

## Установка

1. Клонируйте репозиторий:
    ```
    git clone https://github.com/noleeq/vkmonitor.git
    ```

2. Перейдите в директорию проекта:
    ```
    cd vkmonitor
    ```

3. Установите зависимости:
    ```
    pip install -r requirements.txt
    ```
    
## Конфигурация

Для настройки бота отредактируйте файл `config.py`:

1. **Основные настройки**
    - `telegramToken`: Токен вашего бота Telegram.
    - `telegramChatID`: ID чата Telegram, куда будут отправляться отчеты.
    - `vkToken`: Ключ доступа пользователя VK (access token). Его всегда можно получить на [VKHost](https://vkhost.github.io), выбрав приложение VK Admin.
    - `groupIDs`: Список ID сообществ VK, которые нужно мониторить.
    - `specialChar`: Специальный символ, используемый в публикациях с прямой рекламой.
    - `appLocale`: Язык локализации времени (например, "ru" для русского).

2. **Настройки изображений**
    - `imageStart`: Путь к изображению, которое отправляется при запуске мониторинга.
    - `imageStop`: Путь к изображению, которое отправляется при остановке мониторинга.
    - `imagesGroup`: Словарь, где ключи — это ID сообществ, а значения — это пути к соответствующим изображениям.

3. **Настройки времени**
    - `timeZone`: Название временной зоны, которую вы хотите использовать для отправки отчёта (в формате "Region/City").
    - `timeHours`: Часы, в которые будет отправляться отчёт.
    - `timeMinutes`: Минуты, в которые будет отправляться отчёт.

5. **Настройки текста**
    - `captionImageStart`: Текстовое сообщение, которое отправляется при запуске мониторинга.
    - `captionImageStop`: Текстовое сообщение, которое отправляется при остановке мониторинга.

После внесения изменений сохраните и закройте файл. 

## Запуск

Чтобы запустить бота, используйте следующую команду:

```
python main.py
```

## Лицензия

Этот проект распространяется на условиях лицензии MIT. Пожалуйста, обратите внимание на файл `LICENSE` для получения дополнительной информации.
