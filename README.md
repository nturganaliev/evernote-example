# evernote-example

Работа с заметками на сервиcе [Evernote](https://evernote.com) через API. .

## Установка

- Клонируем репозиторий :
```bash
git@github.com:nturganaliev/evernote-example.git
```

- Должен быть установлен Python версии 2.7 .

- Устанавливаем pip :
```
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py
sudo python2 get-pip.py
```
- Устанавливаем зависимости:
```bash
python2 pip install -r requirements.txt
```
## Настройка
Создаем `.env` файл со следующими переменными :

- EVERNOTE_CONSUMER_KEY - ваш consumer key, получите его на [dev.evernote.com](https://dev.evernote.com/#apikey).
- EVERNOTE_CONSUMER_SECRET - ваш consumer secret, получите его на [dev.evernote.com](https://dev.evernote.com/#apikey).
- EVERNOTE_PERSONAL_TOKEN - ваш ключ разработчика, получите его на [evernote](https://www.evernote.com/Login.action?targetUrl=%2Fapi%2FDeveloperToken.action).
- JOURNAL_TEMPLATE_NOTE_GUID - GUID заметки. Будет использоваться в качестве шаблона. 
- JOURNAL_NOTEBOOK_GUID - GUID блокнота для заметок.
- INBOX_NOTEBOOK_GUID - GUID блокнота, здесь хранятся входящие сообщения.


## Описание модулей

### add_note2journal.py
Создает новую запись, используя шаблон (настройка `JOURNAL_TEMPLATE_NOTE_GUID` в файле `.env`) и сохраняет ее в блокноте, который указан в настройке `JOURNAL_NOTEBOOK_GUID`.

В заголовке шаблона должны быть предусмотрены места для вставки даты и дня недели (`{date}--{dow}`).
По умолчанию в заголовок вставляются текущие дата и время из настроек системы. Если вам необходимо установить
другие дату и время, вы можете передать их в ISO-формате(YYYY-MM-DD) в виде аргумента при вызове скрипта:
```
python add_note2journal.py [YYYY-MM-DD]
```

### dump_inbox.py
Выводит в консоль список заметок, которые хранятся в блокноте для входящих сообщений. GUID блокнота указывается в настройке `INBOX_NOTEBOOK_GUID`, в файле .env.

В консоль выводится 10 последних заметок (по умолчанию), но возможно изменить количество отображаемых заметок, передав нужное число в качестве аргумента при запуске файла:
```
python dump_inbox.py [ваше количество заметок]
```

### list_notebooks.py
По запросу к API Evernote и выводит в консоль список всех блокнотов в аккаунте (GUID, заголовок).


### Цель проекта

Код написан в образовательных целях на онлайн-курсе для веб-разработчиков [dvmn.org](https://dvmn.org).