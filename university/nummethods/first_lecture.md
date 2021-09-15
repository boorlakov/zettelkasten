# Лекция 1

[<- Назад (Численные методы)](https://github.com/boorlakov/zettelkasten/blob/main/university/nummethods/README.md)

## Содержание

Что такое итерационные методы — методы, в которых решение идет последовательно, число шагов = точность, каждый следующий элемент после выражается через предыдущий:
Решая <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;Ax&space;=&space;b&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;Ax&space;=&space;b&space;\end{equation}" title="\large \begin{equation} Ax = b \end{equation}" /></a>

Не хочется матрицу преобразовать, выглядит это так:

<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;X_{k&plus;1}&space;=&space;Bx_{k}&plus;c&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;X_{k&plus;1}&space;=&space;Bx_{k}&plus;c&space;\end{equation}" title="\large \begin{equation} X_{k+1} = Bx_{k}+c \end{equation}" /></a>

### Метод Якоби

Самый простой метод

Считаем, что <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;A&space;=&space;L&space;&plus;&space;D&space;&plus;&space;U&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;A&space;=&space;L&space;&plus;&space;D&space;&plus;&space;U&space;\end{equation}" title="\large \begin{equation} A = L + D + U \end{equation}" /></a>, и что

<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;B&space;=&space;-&space;D^{-1}&space;(L&space;&plus;&space;U)&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;B&space;=&space;-&space;D^{-1}&space;(L&space;&plus;&space;U)&space;\end{equation}" title="\large \begin{equation} B = - D^{-1} (L + U) \end{equation}" /></a>, а <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;c&space;=&space;D^{-1}&space;b&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;c&space;=&space;D^{-1}&space;b&space;\end{equation}" title="\large \begin{equation} c = D^{-1} b \end{equation}" /></a>

Решая

<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;\bigl(\begin{smallmatrix}&space;2&space;&&space;1\\&space;1&space;&&space;2&space;\end{smallmatrix}\bigr)&space;x=&space;\binom{3}{3}&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;\bigl(\begin{smallmatrix}&space;2&space;&&space;1\\&space;1&space;&&space;2&space;\end{smallmatrix}\bigr)&space;x=&space;\binom{3}{3}&space;\end{equation}" title="\large \begin{equation} \bigl(\begin{smallmatrix} 2 & 1\\ 1 & 2 \end{smallmatrix}\bigr) x= \binom{3}{3} \end{equation}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;c&space;=&space;x_{k&plus;1}&space;=&space;\binom{3/2}{3/2}&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;c&space;=&space;x_{k&plus;1}&space;=&space;\binom{3/2}{3/2}&space;\end{equation}" title="\large \begin{equation} c = x_{k+1} = \binom{3/2}{3/2} \end{equation}" /></a> ,
<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;x_{k&plus;2}&space;=&space;\binom{3/4}{3/4}&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;x_{k&plus;2}&space;=&space;\binom{3/4}{3/4}&space;\end{equation}" title="\large \begin{equation} x_{k+2} = \binom{3/4}{3/4} \end{equation}" /></a> ,
<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;x_{k&plus;3}&space;=&space;\binom{9/8}{9/8}&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;x_{k&plus;3}&space;=&space;\binom{9/8}{9/8}&space;\end{equation}" title="\large \begin{equation} x_{k+3} = \binom{9/8}{9/8} \end{equation}" /></a>

Получаем ответ только в пределе.

У всех методов итерационных есть проблема, что все теоремы не строгие (например, для Якоби условие сходимости только при <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;\left&space;\|&space;B&space;\right&space;\|&space;<&space;1&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;\left&space;\|&space;B&space;\right&space;\|&space;<&space;1&space;\end{equation}" title="\large \begin{equation} \left \| B \right \| < 1 \end{equation}" /></a>)

Вспомнили про [норму матрицы](https://en.wikipedia.org/wiki/Matrix_norm)

### Метод Гаусса-Зейделя

<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;B&space;=&space;-(L&space;&plus;&space;D)^{-1}&space;U&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;B&space;=&space;-(L&space;&plus;&space;D)^{-1}&space;U&space;\end{equation}" title="\large \begin{equation} B = -(L + D)^{-1} U \end{equation}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;c&space;=&space;(L&space;&plus;&space;D)^{-1}&space;b&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;c&space;=&space;(L&space;&plus;&space;D)^{-1}&space;b&space;\end{equation}" title="\large \begin{equation} c = (L + D)^{-1} b \end{equation}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;(L&space;&plus;&space;D)^{-1}&space;U&space;x_{k}&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;(L&space;&plus;&space;D)^{-1}&space;U&space;x_{k}&space;\end{equation}" title="\large \begin{equation} (L + D)^{-1} U x_{k} \end{equation}" /></a>

Это модификация метода Якоби!
Как определить класс матриц, где выражение сходится? 

- Как минимум для всех тех же матриц диагонального преобладания

Какие еще могут быть улучшения?

№1 метод последовательной верной релаксации
Хочу, чтобы уравнение первой строки выполнилось
(<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;X_{k&plus;1}&space;=&space;Bx_{k}&plus;c&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;X_{k&plus;1}&space;=&space;Bx_{k}&plus;c&space;\end{equation}" title="\large \begin{equation} X_{k+1} = Bx_{k}+c \end{equation}" /></a>)
Потом говорим, что теперь удовлетворяем, портя предыдущую . . . Дошли до **`n`**, вернулись обратно

На самом деле это метод Зейделя!

Что делать если матрица B явно не написана?

- Указание на то, что это линейная операция!

Есть вектор <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;x_{k&plus;1}&space;-&space;x_k&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;x_{k&plus;1}&space;-&space;x_k&space;\end{equation}" title="\large \begin{equation} x_{k+1} - x_k \end{equation}" /></a>, давайте сделаем <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;x_{k&plus;1}^{*}&space;=&space;x_k&space;&plus;&space;w(x_{k&plus;1}&space;-&space;x_k)&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;x_{k&plus;1}^{*}&space;=&space;x_k&space;&plus;&space;w(x_{k&plus;1}&space;-&space;x_k)&space;\end{equation}" title="\large \begin{equation} x_{k+1}^{*} = x_k + w(x_{k+1} - x_k) \end{equation}" /></a>, где
<a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;0&space;<&space;w&space;<&space;2&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;0&space;<&space;w&space;<&space;2&space;\end{equation}" title="\large \begin{equation} 0 < w < 2 \end{equation}" /></a>

Но есть нюанс, что только если вы знаете собственные числа матрицы, то тогда метод будет сходится **максимально быстро** (бесполезно ирл), потому что собственные числа искать **гораздо** дольше.

### Как улучшить итерационные методы?

Например, посмотреть на несколько шагов назад!

Для положительно определенных хороших матриц идеально подойдет метод сопряженных градиентов

Он помнит все вектора назад. И на самом деле он не очень итерационный. За **`n`** шагов вы получите гарантированную сходимость

### Некоторые нюансы

1. Не пугайтесь разным формулам. Это просто другая нотация. Они все эквиваленты. Можете проверить программно

2. В каком-то смысл он не совсем итерационный

3. На <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;z_k&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;z_k&space;\end{equation}" title="\large \begin{equation} z_k \end{equation}" /></a> нужно умножить один раз

4. Так же как и для метода Зейделя на 1 итерации одно умножение (**самая дорогая операция**)

### Несколько слов по поводу сходимости

1. Когда норма матрицы B больше 1, то теорема ничего не гарантирует

2. Накапливается погрешность — обусловленность матрицы (разнопорядковые числа на диагонали)

3. Для измерения обусловленности вводят еще одно число. Число Тодда

    - <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;Cond(A)&space;=&space;\frac{\lambda_{max}}{\lambda_{min}}&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;Cond(A)&space;=&space;\frac{\lambda_{max}}{\lambda_{min}}&space;\end{equation}" title="\large \begin{equation} Cond(A) = \frac{\lambda_{max}}{\lambda_{min}} \end{equation}" /></a>

4. Какое число считать большим — это сложный вопрос
    - Обычно если Тодд > 10k, то уже плохо

5. Чем Тодд больше, тем сходится хуже и быстрее копится ошибка

### Еще улучшения итерационных методов

А давайте поулучшаем число обусловленности! За дополнительные действия мы получим матрицу А чуть получше и за то все итерационные методы начнут замечательно сходиться

Как? А вот как:

1. Допустим матрица А квадратная неразреженная и смогли построить LU-разложение и научились решать систему <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;L^{-1}&space;A&space;U^{-1}&space;y&space;=&space;L^{-1}&space;b&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;L^{-1}&space;A&space;U^{-1}&space;y&space;=&space;L^{-1}&space;b&space;\end{equation}" title="\large \begin{equation} L^{-1} A U^{-1} y = L^{-1} b \end{equation}" /></a>

2. Все итерационные методы сойдутся за 1 операцию

3. А где собака-то зарыта? А нафига козе баян, если уже все сделали

4. Как можно брать LU? Странно, но возьмем прям L U из <a href="https://www.codecogs.com/eqnedit.php?latex=\large&space;\begin{equation}&space;A&space;=&space;L&space;&plus;&space;D&space;&plus;&space;U&space;\end{equation}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\large&space;\begin{equation}&space;A&space;=&space;L&space;&plus;&space;D&space;&plus;&space;U&space;\end{equation}" title="\large \begin{equation} A = L + D + U \end{equation}" /></a>

Есть еще метод: неполное разложение Холецкого
Заводим L U с этим же портретом с формулами обычного разложения Холецкого.

Курите мануалы!
