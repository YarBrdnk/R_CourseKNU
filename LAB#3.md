Бердник Ярослави
Лабораторна робота №3

В лабораторній роботі необхідно написати наступні функції на мові R та вивести результат роботи цих функцій на довільних даних:

1. Функція add2(x, y), яка повертає суму двох чисел.

> a<-21

> b<-3

> add2<-function(x, y){mysum=x+y; mysum}

> add2(a, b)
[1] 24

> add2(-4, 9.8)
[1] 5.8

2. Функція above(x, n), яка приймає вектор та число n, та повертає всі елементі вектору, які більше n. По замовчуванню n = 10.

> v<-c(3, -9.5, -0.3, 24, 0.98, 34, 6.78, 5, -1)

> above<-function(v, n){nv<-v[v>n]; nv}

> above(v, 10)
[1] 24 34

> num<-1

> above(v, num)
[1]  3.00 24.00 34.00  6.78  5.00

3. Функція my_ifelse(x, exp, n), яка приймає вектор x, порівнює всі його елементи за допомогою exp з n, та повертає елементи вектору, 
які відповідають умові expression. Наприклад, my_ifelse(x, “>”, 0) повертає всі елементи x, які більші 0. Exp може дорівнювати “<”, “>”, “<=”, “>=”, “==”.
Якщо exp не співпадає ні з одним з цих виразів, повертається вектор x.

> my_ifelse <- function(x, exp, n){
+ if (exp == "<") {
+ x[x<n]
+ } else if(exp == "<="){
+ x[x<=n]
+ } else if (exp == ">"){
+ x[x>n]
+ } else if (exp == ">="){
+ x[x>=n]
+ } else if (exp == "=="){
+ x[x==n]
+ } else {
+ x} }

> v1<-c(2, 3.6, 21, -7, -0.6, 1.98, 0.01, 0)

> my_ifelse(v1, '<', 1.98)
[1] -7.00 -0.60  0.01  0.00

> my_ifelse(v1, '<=', 3.6)
[1]  2.00  3.60 -7.00 -0.60  1.98  0.01  0.00

> my_ifelse(v1, '>', 0)
[1]  2.00  3.60 21.00  1.98  0.01

> my_ifelse(v1, '>=', 21)
[1] 21

> my_ifelse(v1, '==', -0.6)
[1] -0.6

> my_ifelse(v1, '==', 3)
numeric(0)

4. Функція columnmean(x, removeNA), яка розраховує середнє значення(mean) по кожному стовпцю матриці, або data frame. Логічний параметр
removeNA вказує, чи видаляти NA значення. По замовчуванню він дорівнює TRUE.

> c <- c(NA, NA, 125, -98, 0, 0.36, NA, 8, NA)

> l <- 9:17

> o <- c(1, 2, 3, 4, 5, 6, 7, 8, 9)

> p <- 25:33

> y <- 0.12

> t <- rbind(c, l, o, p, y)

> t
   [,1]  [,2]   [,3]   [,4]  [,5]  [,6]  [,7]  [,8]  [,9]
c    NA    NA 125.00 -98.00  0.00  0.36    NA  8.00    NA
l  9.00 10.00  11.00  12.00 13.00 14.00 15.00 16.00 17.00
o  1.00  2.00   3.00   4.00  5.00  6.00  7.00  8.00  9.00
p 25.00 26.00  27.00  28.00 29.00 30.00 31.00 32.00 33.00
y  0.12  0.12   0.12   0.12  0.12  0.12  0.12  0.12  0.12

> colunmmean<-function(x, removeNA=TRUE)
+ colMeans(x, na.rm = removeNA)

> colunmmean(t)
[1]   8.780   9.530  33.224 -10.776   9.424  10.096  13.280  12.824  14.780

> colunmmean(t, removeNA=FALSE)
[1]      NA      NA  33.224 -10.776   9.424  10.096      NA  12.824      NA

або
> col_mean <- function (x, removeNA=TRUE) {
+ for (f in seq_len(ncol(x))) {
+ print(mean(x[,f], na.rm=removeNA))
+ }
+ }

> col_mean(t)
[1] 8.78
[1] 9.53
[1] 33.224
[1] -10.776
[1] 9.424
[1] 10.096
[1] 13.28
[1] 12.824
[1] 14.78

> col_mean(t, removeNA=TRUE)
[1] 8.78
[1] 9.53
[1] 33.224
[1] -10.776
[1] 9.424
[1] 10.096
[1] 13.28
[1] 12.824
[1] 14.78

> col_mean(t, removeNA=FALSE)
[1] NA
[1] NA
[1] 33.224
[1] -10.776
[1] 9.424
[1] 10.096
[1] NA
[1] 12.824
[1] NA
