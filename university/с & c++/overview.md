# Описание лекций и ссылки

TO-DO:- add links [from](http://sorokin.github.io/cpp-course/#cite_note_1)

[<- Назад (C++ от Сорокина)](https://github.com/boorlakov/zettelkasten/blob/main/university/с%20%26%20c%2B%2B/README.md)

## Лекции [раз](https://www.youtube.com/playlist?list=PLd7QXkfmSY7ZESrq5BWw4xJrG5CeTkRwJ), [два](https://www.youtube.com/playlist?list=PLd7QXkfmSY7YsYNecuoJLsurtqsMNyhNF)

## [Конспекты](https://github.com/lejabque/cpp-notes)

### Лекция 1 [[1](https://github.com/boorlakov/zettelkasten/blob/main/books/assembler.pdf)]

- `i8086`
- регистры общего назначения, регистр `IP`
- операция `mov`, понятие `endian`
- распространенные арифметические операции: `add`, `sub`, `[i]mul`, `[i]div`, `inc`, `dec`, `neg`
- битовые операции, сдвиги: `not`, `and`, `or`, `xor`, `shl`, `shr`, `sar`
- операция `lea`
- команды безусловных переходов
- регистр флагов и некоторые биты в нём (`ZF`, `CF`, `OF`, `SF`)
- команды условных переходов
- команды `cmp` и `test`
- `i80386`, `32`-битные регистры

### Лекция 2 [[1](https://github.com/boorlakov/zettelkasten/blob/main/books/assembler.pdf)]

- *(offtopic) деление на константу не используя, команду `div` [[2]()]*
- регистр `SP` и команды для работы со стеком (`push`, `pop`)
- команды `call` и `ret`
- регистр `BP`, стековый фрейм [[54]()] [[55]()]
- соглашения вызова функций [[9]()]

### Лекция 3 [[1](https://github.com/boorlakov/zettelkasten/blob/main/books/assembler.pdf)]

- прерывания
- вытесняющая многозадачность
- защищенный режим, страничная адресация

### Лекция 4 [[3]()]

- кеш-память [[4]()] [[5]()] [[6]()]
- translation lookaside buffer
- спекулятивное исполнение команд [[25]()] [[26]()]
- branch prediction [[27]()]
- выравнивание

### Лекция 5[7]()

- пересечение языков `C` и `C++`
- целочисленные типы, `ABI`
- числа с плавающей точкой [[8]()] [[10]()]

### Лекция 6[7]

- структуры
- указатели
- операции взятия адреса и разыменования
- массивы, неявное приведение к указателю
- операции инкремента, декремента, сложения с числом, вычитание числа и разности указателей
- синтаксис указателей и массивов в общем случае, использование скобок для указания приоритета операций
- указатели на функцию

### Лекция 7, 8

- процесс компиляции программ
- объектные файлы
- трансляция, единица трансляция
- линковка [[24]()] [[45]()]
- объявления и определения для переменных и для функций
- модификатор `static`
- препроцессор, примеры директив
- `header`-файлы
- `include guard`

### Лекция 9, 10 [string-demo]

- классы, функции члены-класса, неявный аргумент `this`
- спецификаторы доступа

  ```c++
  private, public
  ```

- отличие ключевых слов
  
  ```c++
  struct, class
  ```

- конструкторы, деструкторы
- время жизни объекта
- для объектов с автоматическим `storage-class`'ом
- для временных объектом
- ссылки, сравнение ссылок с указателями
- перегрузка операторов
- специальные функции члены-класса, правила их генерации
- конструктор по умолчанию
- конструктор копирования
- оператор присваивания
- деструктор
- `deleted functions`
- выражения

  ```c++
  new, new[], delete, delete[]
  ```

- функции

  ```c++
  malloc, free
  ```

- разница между функциями **`malloc`**, **`free`** и выражениями **`new`**, **`delete`**

### Лекции 11, 12 [[23]()] [[40]()]

- наследование, виртуальные функции, таблица виртуальных функции
- как вызвать виртуальную функцию не виртуально?
- спецификатор доступа

  ```c++
  protected
  ```

- абстрактные функции, абстрактные классы
- можно ли вызвать абстрактную функцию?
- виртуальный деструктор
- может ли деструктор быть абстрактным?
- множественное наследование
- виртуальное наследование, таблица виртуальных баз
- пусть есть два класса **`B`** и **`D`**. **`B`** — виртуальная база **`D`**. Можно ли привести **`B*`** к **`D*`**?

### Лекции 13, 14

- исключения [[52]()] [[53]()]
- гарантии безопасности исключений [[46]()] [[47]()]
- `RAII` (resource allocation is initialization)
- `scoped_ptr`
- swap trick

### Лекция 15

- механизмы ОС для аллокации памяти
- `mmap` / `munmap`
- `VirtualAlloc` / `VirtualFree`
- аллокаторы памяти [[28]()]
- small-object optimization [[29]()] [[30]()]
- copy-on-write optimization [[30]()]

### Лекция 16, 17

- `templates`
- понятия явной специализации (`explicit specialization`), частичной специализации (`partial specialization`) и `primary template`
- перегрузка функции и специализация функций
- аргументы шаблона по умолчанию
- `declaration` / `expression ambiguities`
- порядок инстанцирования, неполные типы
- зависимые имена, ключевые слова

  ```c++
  typename, template
  ```

- two-phase name lookup [[39]()]
- `Cfront`- / `borland`-способы реализации шаблонов, линковка, `ODR`
- Явная инстанциация, подавление инстанциации
- `type-traits`

### Лекция 18

- обзор STL [[35]()] [[36]()] [[38]()] [[31.1]()] [[31.2]()] [[31.6]()] [[31.7]()] [[32.2]()] [[19]()]
- tag-dispatching

### Лекция 19

- `namespaces`, `qualified` имена
- `namespace aliases`
- `using` directive
- `using` declaration
- `anonymous namespaces`
- `ADL`
- `C++-style` casts

### Лекция 20

- strict aliasing rule
- restrict keyword
- `undefined behavior`[[48]()] [[49]()] [[50]()]

### Лекция 21

- `custom deleter`
  
```c++
std::shared_ptr
```

- `shared_ptr` на члены-класса
- внутреннее устройство `shared_ptr`

```c++
std::make_shared
```

- `weak_ptr`
- `*_pointer_cast`
- return value optimization, named return value optimizations

### Лекция 22

- `rvalue` references
- `overloading`

```c++
std::move
```

```c++
std::auto_ptr
```

- проблемы **`auto_ptr`**, зачем нужен **`std::unique_ptr`**
- сравнить

  ```c++
  vector<shared_ptr<file_descriptor>>
  ```

  ```c++
  vector<file_descriptor*>
  ```

  ```c++
  ptr_vector<file_descriptor>
  ```

  ```c++
  vector<unique_ptr<file_descriptor>>
  ```

  ```c++
  vector<int>
  ```

  ```c++
  vector<file_descriptor>
  ```

- `rvalue` references
- deduction rules
- reference collapsing rule

  ```c++
  std::forward
  ```

  ```c++
  noexcept
  ```

- `variadic templates`

### Лекция 23

- `anonymous functions`

  ```c++
  std::function
  ```

- понятие type-erasure
  
  ```c++
  std::function, any, any_iterator, any_range
  ```

- статический полиморфизм vs. динамический полиморфизм
- `signals` (aka `listeners`, `observers`)
- понятие `reentrancy`

### Лекция 24

- `result_type`, протокол `result_of`

```c++
decltype
```

```c++
std::optional
```

```c++
alignment, alignof, alignas
```

```c++
std::variant
```

- **`Boost.TypeErasure`**

### Лекции 25, 26

- понятие многопоточности

```c++
std::thread
```

- понятие race condition

```c++
std::mutex
```

- закон Амдала
- понятие **`deadlock`**

```c++
std::atomic
```

- `false sharing`
- `relaxed atomics`
- пример `concurrent_queue`

```c++
std::condition_variable
```
