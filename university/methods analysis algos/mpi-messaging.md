# Основные функции передачи данных в `MPI`

[<- Назад (Методы построения и анализа алгоритмов)](https://github.com/boorlakov/zettelkasten/blob/main/university/methods%20analysis%20algos/README.md)

## About

В библиотеке `MPI` имеется большое множество функций для управления передачей данных. Мы рассмотрим лишь основные функции.

```c
int MPI_Send(void* buf, 
             int count,
             MPI_Datatype type,
             int dest,
             int tag,
             MPI_Comm comm);
```

`buf` - адрес передаваемого буфера с данными
`count` - количество передаваемых элементов
`type` - тип передаваемых элементов `(MPI_INT, MPI_DOUBLE, ...)`
`dest` - номер процесса, которому передаются данные
`tag` - тег (метка) сообщения
`comm` - имя коммуникатора

Функция `MPI_Send` передает массив `buf` процессу с номером `dest` в коммуникаторе `comm`. Тег сообщения нужен, чтобы различать разные сообщения от одного процесса.

```c
int MPI_Recv(void* buf, 
             int count, 
             MPI_Datatype type, 
             int source, 
             int tag, 
             MPI_Comm comm,
             MPI_Status *st);
```

`source` - номер передающего процесса
`st` - структура, содержащая статус сообщения
Остальные параметры имеют тот же смысл, что и в функции `MPI_Send`

Функция `MPI_Recv` принимает данные от процесса с номером `source` и записывает его в массив `buf`.

С помощью функций `MPI_Send` и `MPI_Recv` можно передавать файлы, предварительно считав их в символьный массив.

Функции `MPI_Send` и `MPI_Recv` являются блокирующими. Возвращение из `MPI_Send` не происходит до тех пор, пока данные сообщения не будут скопированы во внутренний буфер `MPI`. `MPI_Recv` возвращает управление только после того, как сообщение было принято. Возможно возникновение ситуаций, при которых ни один процесс не может продолжить свою работу. Поэтому необходимо проявлять осторожность при работе с блокирующими функциями.

Функция `MPI_Irecv` осуществляет неблокирующий прием сообщений.

```c
int MPI_Irecv(void* buf, 
              int count, 
              MPI_Datatype type, 
              int source, 
              int tag, 
              MPI_Comm comm, 
              MPI_Request *rq);
```

В отличие от `MPI_Recv`, возврат управления из `MPI_Irecv` производится немедленно. Функция `MPI_Irecv` лишь инициирует прием данных. Поэтому во время пересылки сообщения принимающий процесс может продолжать выполнять вычисления. Для того чтобы узнать, пришло ли полностью сообщение, используется функция `MPI_Test`.

```c
int MPI_Test(MPI_Request *rq, 
             int *flag, 
             MPI_Status *st);
```

Переменная `MPI_Request` `rq` служит идентификатором запроса на передачу данных и должна быть одной и той же в функциях `MPI_Irecv` и `MPI_Test`

`flag==true`, если прием данных выполнен. Отправку данных можно выполнять функцией `MPI_Send`
