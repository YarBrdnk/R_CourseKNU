Бердник Ярослави

1. Створити змінні базових (atomic) типів. 
Базові типи:
 - character
> x <- c("a", "b", "c")
Values -   chr [1:3] "a" "b" "c" 

> c("a", "b", "c")
[1] "a" "b" "c"

 - numeric
> x <- c(0.7, 0.9)
Values -   num [1:2] 0.7 0.9

> c(0.7, 0.9)
[1] 0.7 0.9

 - integer
> x <- c (3:42)
Values -   int [1:40] 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42
 
> c (3:42)
 [1]  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29
[28] 30 31 32 33 34 35 36 37 38 39 40 41 42

 - complex
> x <- c (2+0i, 3+6i)
Values -   cplx [1:2] 2+0i 3+6i

> c (2+0i, 3+6i)
[1] 2+0i 3+6i

 - logical
> x <- c(T, FALSE, TRUE, F)
Values -   logi [1:4] TRUE FALSE TRUE FALSE

> c(T, FALSE, TRUE, F)
[1]  TRUE FALSE  TRUE FALSE

2. Створити вектори, які містять:
* послідовність з 3 до 75
> c(3:75)
 [1]  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29
[28] 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56
[55] 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75

* містять числа 3.14, 2.71, 0, 13
> c(3.14, 2.71, 0, 13)
[1]  3.14  2.71  0.00 13.00 

* 100 значень FALSE
> vector(mode = "logical", length = 100)
  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
 [14] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
 [27] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
 [40] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
 [53] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
 [66] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
 [79] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
 [92] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE

3. Створити матрицю за допомогою matrix, та за допомогою cbind або rbind

> matrix(cbind(0.5, 3.9, 0, 2, 1.3, 131, 2.2, 7, 3.5, 3.8, 4.6, 5.1), nrow = 4, ncol = 3)
     [,1]  [,2] [,3]
[1,]  0.5   1.3  3.5
[2,]  3.9 131.0  3.8
[3,]  0.0   2.2  4.6
[4,]  2.0   7.0  5.1

4. Створити довільний список (list), в який включити всі базові типи

> list(0.9, 2, "b", T, 3+6i)
[[1]]
[1] 0.9

[[2]]
[1] 2

[[3]]
[1] "b"

[[4]]
[1] TRUE

[[5]]
[1] 3+6i

5. Створити фактор з трьома рівнями «baby», «child», «adult»

> factor(c("baby", "child", "adult"))
[1] baby  child adult
Levels: adult baby child

Values x -    Factor w/ 3 levels "adult", "baby",..:2 3 1 


> x <- factor(c("baby", "child", "adult"))
> x
[1] baby  child adult
Levels: adult baby child
> table(x)
x
adult  baby child 
    1     1     1 
> unclass(x)
[1] 2 3 1
attr(,"levels")
[1] "adult" "baby"  "child"

6. Знайти індекс першого значення NA в векторі 1, 2, 3, 4, NA, 6, 7, NA, 9, NA,
11.

> x <- c(1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11)
> is.na(x)
 [1] FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE  TRUE FALSE

7. Створити довільний data frame та вивести в консоль

> df <- data.frame(var1=c(11,21,31), var2=c(12,22,32), var3=c(13,23,33), var4=c(14,24,34), row.names=c("case1", "case2", "case3"))
> df
      var1 var2 var3 var4
case1   11   12   13   14
case2   21   22   23   24
case3   31   32   33   34
> nrow(x)
[1] 4
> ncol(x)
[1] 2

або

> df <- data.frame(1:2, 3:4, 5:6, 7:8)
> df
  X1.2 X3.4 X5.6 X7.8
1    1    3    5    7
2    2    4    6    8

8. Змінити імена стовпців цього data frame
> rownames(df) <- c("case_1", "case_2")
> colnames(df) <- c("var_1", "var_2", "var_3", "var_4")
> df
       var_1 var_2 var_3 var_4
case_1     1     3     5     7
case_2     2     4     6     8



















