# `test`

## About

### Оператор `test` проверяет выполнение условия и возвращает `истина` (`0`) или `ложь` (`1`)

### **Общий** формат оператора

- `test условие` или `[ условие ]`

**Замечание**: вторая форма записи оператора предусматривает **наличие обязательных пробелов** между квадратными скобками и выражением условия. Если строка условия в команде `test` пустая, то возвращается значение `1`.

## Возможны условия нескольких видов

### 1. Проверка файлов или переменных

- Формат команды: `test  ключ  имя_файла | имя_переменной`

  - Ключ команды задает режим проверки и может принимать следующие значения:
    - `-f` - указанный файл является обычным файлом
    - `-d` - указанный файл является обычным каталогом
    - `-с` - указанный файл является символьным устройством
    - `-r` - указанный файл доступен для чтения
    - `-w` - указанный файл доступен для записи
    - `-s` - указанный файл не является пустым
    - `-n` - указанная переменная имеет значение (не пустая)
    - `-z` - указанная переменная не имеет значения

  - Примеры команды:
    - `test –f /usr/user1/file_1` возвращает `0`, если `/usr/user1/file_1` является обычным файлом
    - `test –w /usr/user1/file_1` возвращает `0`, если файл /usr/user1/file_1 доступен для записи
    - `test –n $ALFA` возвращает `0`, если переменная `ALFA` имеет значение.

### 2. Сравнение строк

- Формат команды: `test  строка1  отношение  строка2`
  - Операции отношения строк: `=` (равно) или `!=` (не равно)

  - Примеры команд:
    - `test $A = $B` возвращает `0`, если значение переменной `A` равно значению переменной `B`
    - `test $A != $B` возвращает `0`, если значение переменной `A` не равно значению переменной `B`
    - **Замечание**: операция отношения **обязательно** с двух сторон окружается **пробелами**.

### 3. Сравнение целых чисел

- Формат команды
  - `test  число1  отношение  число2` операции отношения чисел:
    - `-eq`  - равно
    - `-ne`  - не равно
    - `-gt`  - больше
    - `-ge`  - больше или равно
    - `-lt`  - меньше
    - `-le`  - меньше или равно