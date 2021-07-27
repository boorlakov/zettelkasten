# Глобальные переменные в `shell script`

## Каждая программа на `shell` всегда имеет **минимальный** набор **глобальных** переменных

|  **Переменная** | **Значение** |
| --- | --- |
| **`?`** | **Код завершения** последней команды (`0` – нормальное завершение) |
| **`$`** | `PID` **текущего** процесса `shell` |
| **`!`** | `PID` **последнего фонового** процесса |
| **`#`** | **Число** параметров, переданных в `shell` |
| **`*`** | **Список** параметров `shell` в виде **одной** строки |
| **`@`** | **Список** параметров `shell` в виде **набора** слов |
| **`-`** | **Флаги**, передаваемые в `shell` |
| **`HOME`** | **Имя** **домашнего** каталога |
| **`PATH`** | **Пути** поиска исполняемых файлов |
| **`PS1`** | Вид системной подсказки |
| **`SHELL`** | **Имя** каталога, в котором выполняется **интерпретатор** |
| **`USER`** | **Имя** учетной записи текущего пользователя |
---

### Пользователь может использовать в сценариях глобальные переменные интерпретатора и собственные локальные переменные. Переменные всегда имеют тип (строчный ведь) и задаются сразу со значением (возможно с пустым)

### При объявлении переменной ее имя и значение должны быть записаны **без пробелов относительно символа равенства**