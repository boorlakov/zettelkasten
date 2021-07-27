# `for`

[<- Назад (конспекты по осям)](https://github.com/boorlakov/zettelkasten/blob/main/university/operation%20systems%20and%20IDE/README.md)

## About

Оператор предопределенного цикла for имеет следующий формат

```shell
for имя  [in список] do
    список_операторов
done
```

Если список значений для переменной не задан, то в качестве списка используется значение внутренней переменной `@`, содержащей список аргументов сценария

Пример оператора

```shell
list=”word 1 word2 word3 word4”
for VAL in $LIST do
    echo $VAL
done
```
