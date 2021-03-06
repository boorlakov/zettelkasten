# `expr`

[<- Назад (конспекты по осям)](https://github.com/boorlakov/zettelkasten/blob/main/university/operation%20systems%20and%20IDE/README.md)

## About

В качестве значения переменной можно присвоить результат выполнения команды Linux, указав имя команды в обратных кавычках (обычно этот символ находится на клавише для ввода символов «~» и «ё»)

- VAR_2=`pwd`

Как способ хранения данных помимо переменных есть массивы (неизвестно динамические или статические)

- Обращаться надо примерно так `step=${steps[2]}`

С помощью `expr` имеет возможность обработки переменных как целых чисел, выполняя операции сложения (**`+`**), вычитания (**`-`**), умножения (**`*`**), целочисленного деления (**`/`**) и получения остатка от деления (**`%`**)

```shell
a=`expr $x + $y`
b=`expr $x - $y`
c=`expr $x / $y`
d=`expr $x % $y`
e=`expr $x “*” $y`
```

Аналогичные результаты можно получить с помощью команды let, которая сама реализует преобразование строковых значений в числовые (???)

```shell
let “a=x+y”
let “b=x-y”
let “c=x/y”
let “d=x%y”
let “e=x*y”
```
