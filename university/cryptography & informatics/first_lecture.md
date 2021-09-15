# Лекция №1

[<- Назад (Основные понятия теории информации)](https://github.com/boorlakov/zettelkasten/blob/main/university/cryptography%20%26%20informatics/README.md)

## Введение

### Про теорию информации

Теория информации - прикладная математики + радиотехника + информатика про измерение информации, про предельные свойства соотношения для систем передачи данных

Использует математический аппарат как теорию вероятности и математическую статистику

Основые понятия:

- Энтропия информационная

- Количество информации

- Криптография

Основная статья, положившая основу дисциплины

[Статья "Математическая теория связи" (1948)](http://shannon.usu.edu.ru/Shannon/shannon1948/)

### Виды информации

Информация - нематериальная сущность, при помощи которой с любой точностью описывается любой понятийный факт

- Дискретная точные значения величины (удобнее для человека)

- Непрерывная (датчики и т.д.)

Сжать проще неравномерную информацию (и кстати она более криптостойкая(?))

<a href="https://www.codecogs.com/eqnedit.php?latex=a&space;=&space;b" target="_blank"><img src="https://latex.codecogs.com/gif.latex?a&space;=&space;b" title="a = b" /></a> несет столько же информации, что и <a href="https://www.codecogs.com/eqnedit.php?latex=a^3&space;=&space;b^3" target="_blank"><img src="https://latex.codecogs.com/gif.latex?a^3&space;=&space;b^3" title="a^3 = b^3" /></a>

Математическое ожидание и дисперсия дают полную информацию о случайной величине.

#### Пример

`Y = X + Z`

`X` это отправляемая инфа,
`Z` помехи

чем меньше дисперсия `Z` тем больше инфы получим о `X`

### *Про энтропию как рассеивание информации.*

Чем меньше энтропия, тем больше мы имеет инфы об объекте. на этом факте основывается метод исследования информации с помощью нейронок (grad down E -> лучше результат)

### Еще про информацию и связанные с ней формулы

Пусть есть алфавит <a href="https://www.codecogs.com/eqnedit.php?latex=A&space;=&space;{x_1,&space;x_2,&space;...,&space;x_n}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;=&space;{x_1,&space;x_2,&space;...,&space;x_n}" title="A = {x_1, x_2, ..., x_n}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=X&space;=&space;{x_1&space;\rightarrow&space;P(x_1),&space;x_2&space;\rightarrow&space;P(x_2),&space;...,x_n&space;\rightarrow&space;P(x_n)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?X&space;=&space;{x_1&space;\rightarrow&space;P(x_1),&space;x_2&space;\rightarrow&space;P(x_2),&space;...,x_n&space;\rightarrow&space;P(x_n)}" title="X = {x_1 \rightarrow P(x_1), x_2 \rightarrow P(x_2), ...,x_n \rightarrow P(x_n)}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\sum_{i}^{}P(x_i)&space;=&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sum_{i}^{}P(x_i)&space;=&space;1" title="\sum_{i}^{}P(x_i) = 1" /></a>

Собственная информация, <a href="https://www.codecogs.com/eqnedit.php?latex=I(x)&space;=&space;log_b(\frac{1}{P(x)})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(x)&space;=&space;log_b(\frac{1}{P(x)})" title="I(x) = log_b(\frac{1}{P(x)})" /></a>, если `b = 2`, тогда измеряем в битах.

### Свойства собственной информации

1. <a href="https://www.codecogs.com/eqnedit.php?latex=I(x)\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(x)\geq&space;0" title="I(x)\geq 0" /></a>, <a href="https://www.codecogs.com/eqnedit.php?latex=x&space;\in&space;X" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x&space;\in&space;X" title="x \in X" /></a>

2. Монотонность

3. Аддитивность (у независимых событий) (т.к. инфа это логарифм, а логарифм произв это сумма логарифмов)

### [Взаимная информация](https://ru.wikipedia.org/wiki/Взаимная_информация)

Формула:

<a href="https://www.codecogs.com/eqnedit.php?latex=I(x_j,&space;y_k)&space;=&space;log_b{\frac{P(x_j&space;|&space;y_k)}{P(x_j)&space;P(y_k)}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(x_j,&space;y_k)&space;=&space;log_b{\frac{P(x_j&space;|&space;y_k)}{P(x_j)&space;P(y_k)}}" title="I(x_j, y_k) = log_b{\frac{P(x_j | y_k)}{P(x_j) P(y_k)}}" /></a>

Свойства:

<a href="https://www.codecogs.com/eqnedit.php?latex=-\infty&space;<&space;I(x_j,&space;y_k)&space;<&space;\infty" target="_blank"><img src="https://latex.codecogs.com/gif.latex?-\infty&space;<&space;I(x_j,&space;y_k)&space;<&space;\infty" title="-\infty < I(x_j, y_k) < \infty" /></a>

#### Как связано кол-во информации с [энтропией](https://ru.wikipedia.org/wiki/Информационная_энтропия)

Для дискретных величин X, Y, заданных законами распределения <a href="https://www.codecogs.com/eqnedit.php?latex=P(X=X_i,&space;Y=Y_j)&space;=&space;p_j" target="_blank"><img src="https://latex.codecogs.com/gif.latex?P(X=X_i,&space;Y=Y_j)&space;=&space;p_j" title="P(X=X_i, Y=Y_j) = p_j" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=I(X,&space;Y)&space;=&space;\sum_{i,j}^{}&space;(log_2{\frac{p_{ij}}{p_i&space;p_j}})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(X,&space;Y)&space;=&space;\sum_{i,j}^{}&space;(log_2{\frac{p_{ij}}{p_i&space;p_j}})" title="I(X, Y) = \sum_{i,j}^{} (log_2{\frac{p_{ij}}{p_i p_j}})" /></a>

Определим энтропию через среднюю взаимную информацию как:

<a href="https://www.codecogs.com/eqnedit.php?latex=I(X,&space;Y)&space;=&space;\sum_{i,&space;j}&space;p_i&space;log_2\frac{p_{ij}}{p_i&space;q_j}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(X,&space;Y)&space;=&space;\sum_{i,&space;j}&space;p_i&space;log_2\frac{p_{ij}}{p_i&space;q_j}" title="I(X, Y) = \sum_{i, j} p_i log_2\frac{p_{ij}}{p_i q_j}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=I(X,&space;X)&space;=&space;HX&space;=&space;HX&space;=&space;\sum_i&space;p_i&space;\ast&space;log_2\frac{1}{p_i}&space;=&space;-&space;\sum_i&space;p_i&space;\ast&space;log_2(p_i)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(X,&space;X)&space;=&space;HX&space;=&space;HX&space;=&space;\sum_i&space;p_i&space;\ast&space;log_2\frac{1}{p_i}&space;=&space;-&space;\sum_i&space;p_i&space;\ast&space;log_2(p_i)" title="I(X, X) = HX = HX = \sum_i p_i \ast log_2\frac{1}{p_i} = - \sum_i p_i \ast log_2(p_i)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=I(X,Y)&space;=&space;I(Y,X)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(X,Y)&space;=&space;I(Y,X)" title="I(X,Y) = I(Y,X)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=I(X,Y)&space;=&space;HX&space;&plus;&space;HY&space;-&space;H(X,Y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(X,Y)&space;=&space;HX&space;&plus;&space;HY&space;-&space;H(X,Y)" title="I(X,Y) = HX + HY - H(X,Y)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=H(X,Y)&space;=&space;-&space;\sum_{ij}p_{ij}&space;log_2(p_{ij})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H(X,Y)&space;=&space;-&space;\sum_{ij}p_{ij}&space;log_2(p_{ij})" title="H(X,Y) = - \sum_{ij}p_{ij} log_2(p_{ij})" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=I(X,Y)&space;\leq&space;I(X,X)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I(X,Y)&space;\leq&space;I(X,X)" title="I(X,Y) \leq I(X,X)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=HX&space;=&space;0,&space;X&space;\in&space;const" target="_blank"><img src="https://latex.codecogs.com/gif.latex?HX&space;=&space;0,&space;X&space;\in&space;const" title="HX = 0, X \in const" /></a>

Доказательсво свойства 1 основано на факте 
<a href="https://www.codecogs.com/eqnedit.php?latex=e^{x-1}&space;\geq&space;x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?e^{x-1}&space;\geq&space;x" title="e^{x-1} \geq x" /></a>
