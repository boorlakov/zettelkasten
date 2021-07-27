# `case`

[<- Назад (конспекты по осям)](https://github.com/boorlakov/zettelkasten/blob/main/university/operation%20systems%20and%20IDE/README.md)

## About

Оператор множественного выбора `case` имеет следующий формат:

```shell
case строка in
    шаблон_1) список_операторов;;
    шаблон_2) список_операторов;;
    шаблон_n) список_операторов;;
esac
```

Пример оператора

```shell
echo  –n ‘please enter symbol from A to C:‘
read ENTRY
case $ENTRY in
     A|a) echo ‘Apple’;;
     B|b) echo ‘Baby’;;
     C|c) echo ‘Coke’;;
       *) echo ‘Please type A, B or C !’;;
esac
```
