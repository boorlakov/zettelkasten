# `if`

[<- Назад (конспекты по осям)](https://github.com/boorlakov/zettelkasten/blob/main/university/operation%20systems%20and%20IDE/README.md)

## About

Условный оператор `if` имеет следующий формат

```shell
if условие then
    список_операторов
[elif условие then
    список_операторов]
[else список_операторов]
fi
```

Здесь условие – любой оператор, возвращающий значение `true`  или `false` (обычно используется оператор `test`)

`список_операторов` - операторы, разделенные точкой с запятой `;`

Пример оператора

```shell
if [ -f /tmp/myfile ] then
  cksum /tmp/myfile
  else
  ls /tmp > /tmp/myfile; cksum /tmp/myfile
fi
```
