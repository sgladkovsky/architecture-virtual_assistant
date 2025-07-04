﻿# Back для AI

Команды разворачинвания (windows)

```shell
python -m ensurepip --upgrade
pip install virtualenv
python -m venv rasa_env

```

Активация venv
```shell
.\rasa_env\Scripts\activate
```

В связи с тем, что требует старую версию Python (3.4+, но 3.13 не подходит)
Перешел в Pycharm создал проект с python 3.9
Имя venv - rasa_venv

В терминале 
```shell
pip install rasa
pip install transformers
```

Проверяем корректность установки
```shell
rasa --version
```
Результат
```
C:\repo\yapracticum\sp5\architecture-virtual_assistant\back\rasa_venv\lib\site-packages\rasa\core\tracker_store.py:1044: MovedIn20Warning: Deprecated API feature
s detected! These feature(s) are not compatible with SQLAlchemy 2.0. To prevent incompatible upgrades prior to updating applications, ensure requirements files a
re pinned to "sqlalchemy<2.0". Set environment variable SQLALCHEMY_WARN_20=1 to show all deprecation warnings.  Set environment variable SQLALCHEMY_SILENCE_UBER_WARNING=1 to silence this message. (Background on SQLAlchemy 2.0 at: https://sqlalche.me/e/b8d9)
  Base: DeclarativeMeta = declarative_base()
Rasa Version      :         3.6.21
Minimum Compatible Version: 3.6.21
Rasa SDK Version  :         3.6.2
Python Version    :         3.9.13
Operating System  :         Windows-10-10.0.22631-SP0
Python Path       :         C:\repo\yapracticum\sp5\architecture-virtual_assistant\back\rasa_venv\Scripts\python.exe

```

Инициализация rasa
```shell
rasa init
```

Скопировать файлы

Запустить тренировку
```shell
rasa train 
```

*Внимание!* Оказалось файл конфигурации скопировался с nbsp последовательностями, для того чтобы заработало заменил все на пробелы

После тренировки запустить rasa с ассистентом
```shell
rasa run --enable-api 
```

Так как запускается все с единого хоста, то чтобы не попасть на вызов CORS надо разрешить вызов с одного хоста
Тогда запускать
```shell
rasa run --enable-api --cors "*" 
```

Прверка вызова rasa
```shell

curl --location 'http://localhost:5005/    webhooks/rest/webhook' \--header 'Content-Type: application/json' \--data '{"sender": "Петя", "message":     "Привет!"}'

```

*Вывод* Редкостное гавно. После тренировки все время один и тот же результат - вначале рассказывало про архитектуру (один и тот же ответ на любые запросы), потом потренировал спрашивало что я хочу в итоге (после очередной тренировки) вообще отказалась разговаривать - пустой ответ
###### Может я его не умею готовить?