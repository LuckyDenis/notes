pybabel
=======
>Babel is an integrated collection of utilities that assist in internationalizing and localizing Python applications, with an emphasis on web-based applications.

[Официальная документация](http://babel.pocoo.org/)

##### Шаг 1

__stdin:__<br/>
    
    pybabel extract project.py -o locales/myproject.pot

`project.py` - файл в котором находятся строки, которые хотим перевести <br/>
`locales/` - папка в которой будут файлы локализации, можно использовать любое имя <br/>

__Опции:__ <br/>
`--project=MyProject` - добавить/изменить имя проекта <br/>
`--version=2.2` - добавить/изменить версию проекта <br/>

##### Шаг 2

Создаем `*.po` файлы. Для русского и английского `en`, `ru`.

    echo {en,ru} | xargs -n1 pybabel init -i locales/myproject.pot -d locales -D myproject -l

##### Шаг 3
Переводим текст.

##### Шаг 4
Сборка перевода.
    
    pybabel compile -d locales -D myproject

##### Шаг 5
Когда хотим обновить перевод.

>Повторяем Шаг 1 <br/>
>Обновляем *.po файлы:

    pybabel update -d locales -D myproject -i locales/myproject.pot

>Переводим <br/>
>Повторяем Шаг 4