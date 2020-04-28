Сборка Python 3 из исходников
=============================

> Алгоритм сборки Python 3 из исходников под ubuntu.

### Создаем папку для исходников
    
    mkdir ~/code/
    
### Скачиваем исходники
    
    wget https://www.python.org/ftp/python/3.8.2/Python-3.8.2.tar.xz
    
### Распаковываем
    
     tar xvf Python-3.8.2
     cd Python-3.8.2

### Создаем папку где будем хранить собранный python

    mkdir ~/.python/
    
### Скачиваем и устанавливаем нужные библиотеки для сборки

    apt-get install -y \
        build-essential libexpat1-dev libssl-dev zlib1g-dev \
        libncurses5-dev libbz2-dev liblzma-dev \
        libsqlite3-dev libffi-dev\
        libffi-dev tcl-dev linux-headers-generic libgdbm-dev \
        libreadline-dev tk-dev \
        libdb-dev \
        libmpdec-dev \
        libncursesw5-dev

### Сборка и установка
-j{количество ядер * 2}

    ./configure --enable-optimizations --prefix=/home/пользователь/.python
    make -j8
    sudo make altinstall
