# Что еще помнить

[<- Назад (конспекты по осям)](https://github.com/boorlakov/zettelkasten/blob/main/university/operation%20systems%20and%20IDE/README.md)

- Для выполнения скрипта Linux запускает интерпретатор отдельно. Поэтому глобальные переменные `*`, `#` и `@` имеют **собственные** значения для **каждого** запущенного скрипта

- Все переменные, известные скрипту во время выполнения, образуют его окружение (`env`), включающее переменные, которые сценарий получает путем наследования от родительского процесса (от интерпретатора `shell`) и собственные локальные переменные

- При загрузке системы `Shell` выполняет команды, содержащие­ся в `/etc/profile`, затем команды, содержащиеся в `$HOME` `/.profile`. Для того, чтобы при входе в систему автома­тически устанавливались необходимые переменные, следует откорректировать файл `.profile`, находя­щийся в Вашем домашнем каталоге
