Установка pgadmin4 - python
===========================

> pgAdmin 4 — это основной выпуск pgAdmin, созданный с использованием Python, Javascript/jQuery, и среды выполнения рабочего стола написанной на C++ с использованием Qt. pgAdmin 4 значительно расширяет возможности использования, в отличие от pgAdmin 3, благодаря обновленным элементам updated user interface (UI), многопользовательским/веб-вариантам развертывания, панелям мониторинга и более современному, элегантному дизайну.

### Создаем окружение python

    python -m venv pgadmin4/
    cd ./pgadmin4

### Скачиваем python weel pgAdmin4

    wget https://ftp.postgresql.org/pub/pgadmin/pgadmin4/v2.0/pip/pgadmin4-2.0-py2.py3-none-any.whl

### Активируем окружение

    . /bin/activate
        
### Устанавливаем pgadmin4

    pip install pgadmin4-2.0-py2.py3-none-any.whl
        
### Настраиваем на быстрый запуск
Создаем файл конфигурации

    cd ~/pgadmin4/lib/python3.7/site-packages/pgadmin4
    touch config_local.py
        
Редактируем файл

    vim config_local.py

Прописываем в файле

    import os
        
    SERVER_MODE = False
    DATA_DIR = os.path.realpath(os.path.expanduser(u'~/.pgadmin/'))
    LOG_FILE = os.path.join(DATA_DIR, 'pgadmin4.log')
    SQLITE_PATH = os.path.join(DATA_DIR, 'pgadmin4.db')
    SESSION_DB_PATH = os.path.join(DATA_DIR, 'sessions')
    STORAGE_DIR = os.path.join(DATA_DIR, 'storage')

Сохраняем и выходим

    esc -> : -> wq -> enter
        
Переконфигурируем
        
    python ~/pgadmin4/lib/python3.7/site-packages/pgadmin4/setup.py
    
Проверяем

    python ~/pgadmin4/lib/python3.7/site-packages/pgadmin4/pgAdmin4.py

Выходим из окружения
        
    deactivate
        
### Для быстрого запуска
Создаем файл bash скрипта
    
    touch ~/pgadmin4/pgadmin4.sh
        
Прописываем в нем
        
    #!/usr/bin/env bash
    
    cd ~/pgadmin4/
    . bin/activate
    python ~/pgadmin4/lib/python3.7/site-packages/pgadmin4/pgAdmin4.py
        
### Псевдоним в системе
Открываем файл конфигурации оболочки
        
    vim ~/.bashrc

Пишем
        
    alias pgadmin4='~/pgadmin4/pgadmin4.sh'
        
Перезагружаем bachrc
        
    source ~/.bashrc
        
Запускам

    pgadmin4
