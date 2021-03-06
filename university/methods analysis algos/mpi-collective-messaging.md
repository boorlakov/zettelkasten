# Коллективные операции в `MPI`

[<- Назад (Методы построения и анализа алгоритмов)](https://github.com/boorlakov/zettelkasten/blob/main/university/methods%20analysis%20algos/README.md)

## About

### Рассылка информации от одного процесса всем остальным

Широковещательная рассылка данных выполняется с помощью функции `MPI_Bcast`. Процесс с номером `root` рассылает сообщение из своего буфера передачи всем процессам области связи коммуникатора `comm`

```c
int MPI_Bcast(void* buffer, 
              int count, 
              MPI_Datatype datatype, 
              int root, 
              MPI_Comm comm)
```

| Название       | Назначение|
| ---            | ---|
| **`buffer`**   | адрес начала расположения в памяти рассылаемых данных|
| **`count`**    | число посылаемых элементов |
| **`datatype`** | тип посылаемых данных |
| **`root`**     | номер процесса-отправителя |
| **`comm`**     | коммуникатор |

После завершения подпрограммы каждый процесс в области связи коммуникатора `comm`, включая и самого отправителя, получит копию сообщения от процесса-отправителя `root`.

### Сборка распределенного по процессам массива в один массив

Функция `MPI_Gather` производит сборку блоков данных, посылаемых всеми процессами группы, в один массив процесса с номером `root`. Длина блоков предполагается одинаковой. Объединение происходит в порядке увеличения номеров процессов-отправителей. То есть данные, посланные процессом `i` из своего буфера `sendbuf`, помещаются в `i-ю` порцию буфера `recvbuf` процесса root. Длина массива, в который собираются данные, должна быть достаточной для их размещения

```c
int MPI_Gather(void* sendbuf, 
               int sendcount, 
               MPI_Datatype sendtype, 
               void* recvbuf, 
               int recvcount, 
               MPI_Datatype recvtype, 
               int root, 
               MPI_Comm comm)
```

| Название        | Назначение|
| ---             | ---|
| **`sendbuf`**   | адрес начала размещения посылаемых данных |
| **`sendcount`** | число посылаемых элементов |
| **`sendtype`**  | тип посылаемых элементов |
| **`recvbuf`**   | адрес начала буфера приема (используется только в процессе-получателе root) |
| **`recvcount`** | число элементов, получаемых от каждого процесса (используется только в процессе-получателе root) |
| **`recvtype`**  | тип получаемых элементов |
| **`root`**      | номер процесса-получателя |
| **`comm`**      | коммуникатор |

Тип посылаемых элементов `sendtype` должен совпадать с типом `recvtype` получаемых элементов, а число `sendcount` должно равняться числу `recvcount`. То есть, `recvcount` в вызове из процесса `root` - это число собираемых от каждого процесса элементов, а не общее количество собранных элементов.

Функция `MPI_Gatherv` позволяет собирать блоки с разным числом элементов от каждого процесса, так как количество элементов, принимаемых от каждого процесса, задается индивидуально с помощью массива recvcounts. Эта функция обеспечивает также большую гибкость при размещении данных в процессе-получателе, благодаря введению в качестве параметра массива смещений `displs`.

```c
int MPI_Gatherv(void* sendbuf, 
                int sendcount, 
                MPI_Datatype sendtype, 
                void* rbuf, 
                int* recvcounts, 
                int* displs, 
                MPI_Datatype recvtype, 
                int root, 
                MPI_Comm comm)
```

| Название         | Назначение|
| ---              | ---|
| **`sendbuf`**    | адрес начала размещения посылаемых данных  |
| **`sendcount`**  | число посылаемых элементов |
| **`sendtype`**   | тип посылаемых элементов |
| **`rbuf`**       | адрес начала буфера приема |
| **`recvcounts`** | число элементов, получаемых от каждого процесса (используется только в процессе-получателе `root`) |
| **`displs`**     | целочисленный массив (размер равен числу процессов в группе), `i-ое` значение определяет смещение `i-го` блока данных относительно начала `rbuf` |
| **`recvtype`**   | тип получаемых элементов |
| **`root`**       | номер процесса-получателя |
| **`comm`**       | коммуникатор |

Сообщения помещаются в буфер приема процесса `root` в соответствии с номерами посылающих процессов, а именно, данные, посланные процессом `i`, размещаются в адресном пространстве процесса `root`, начиная с адреса `rbuf + displs[i]`.

### Разбиение массива и рассылка его фрагментов всем процессам

Функция `MPI_Scatter` разбивает сообщение из буфера посылки процесса `root` на равные части размером sendcount и посылает `i-ю` часть в буфер приема процесса с номером `i` (в том числе и самому себе). Процесс `root` использует оба буфера (посылки и приема), поэтому в вызываемой им подпрограмме все параметры являются существенными. Остальные процессы группы с коммуникатором `comm` являются только получателями, поэтому для них параметры, специфицирующие буфер посылки, не существенны

```c
int MPI_Scatter(void* sendbuf, 
                int sendcount, 
                MPI_Datatype sendtype, 
                void* recvbuf, 
                int recvcount, 
                MPI_Datatype recvtype, 
                int root, MPI_Comm comm)
```

| Название        | Назначение|
| ---             | ---|
| **`sendbuf`**   | адрес начала размещения посылаемых данных |
| **`sendcount`** | число посылаемых элементов |
| **`sendtype`**  | тип посылаемых элементов |
| **`recvbuf`**   | адрес начала буфера приема (используется только в процессе-получателе `root`) |
| **`recvcount`** | число элементов, получаемых от каждого процесса (используется только в процессе-получателе `root`) |
| **`recvtype`**  | тип получаемых элементов |
| **`root`**      | номер процесса-получателя |
| **`comm`**      | коммуникатор |

Тип посылаемых элементов `sendtype` должен совпадать с типом `recvtype` получаемых элементов, а число посылаемых элементов `sendcount` должно равняться числу принимаемых recvcount. Значение `sendcount` в вызове из процесса `root` - это число посылаемых каждому процессу элементов, а не общее их количество. Операция `Scatter` является обратной по отношению к `Gather`

Функция `MPI_Scaterv` является векторным вариантом функции `MPI_Scatter`, позволяющим посылать каждому процессу различное количество элементов. Начало расположения элементов блока, посылаемого `i-му` процессу, задается в массиве смещений `displs`, а число посылаемых элементов - в массиве `sendcounts`. Эта функция является обратной по отношению к функции `MPI_Gatherv`

```c
int MPI_Scatterv(void* sendbuf, 
                 int* sendcounts, 
                 int* displs, 
                 MPI_Datatype sendtype, 
                 void* recvbuf, 
                 int recvcount, 
                 MPI_Datatype recvtype, 
                 int root, 
                 MPI_Comm comm)
```

| Название         | Назначение|
| ---              | ---|
| **`sendbuf`**    | адрес начала размещения посылаемых данных  |
| **`sendcount`**  | число посылаемых элементов |
| **`sendtype`**   | тип посылаемых элементов |
| **`rbuf`**       | адрес начала буфера приема |
| **`recvcounts`** | число элементов, получаемых от каждого процесса (используется только в процессе-получателе `root`) |
| **`displs`**     | целочисленный массив (размер равен числу процессов в группе), `i-ое` значение определяет смещение `i-го` блока данных относительно начала `rbuf` |
| **`recvtype`**   | тип получаемых элементов |
| **`root`**       | номер процесса-получателя |
| **`comm`**       | коммуникатор |
