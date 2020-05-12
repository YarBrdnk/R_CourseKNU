Лабораторна робота № 7.
Бердник Ярослави

Для виконання роботи можна скористатись бібліотекою stringr від tidyverse https://stringr.tidyverse.org/index.html
Частина 1.
Завантажте файл “olympics.csv” за посиланням https://www.dropbox.com/s/9oayr45v7nj30nv/olympics.csv?dl=0
Цей файл базується на статті в Wikipedia All Time Olympic Games Medals Спочатку необхідно провести базову обробку файлу.
Напишіть функцію prepare_set <- function(file_name) {} яка в якості аргументу приймає ім’я файлу і повертає дата фрейм. Збережіть цей дата фрейм в змінну olympics
olympics <- prepare_set(“olympics.csv”)
Функція prepare_set повинна виконувати наступні дії:
1. Зчитати файл
read.csv("olympics.csv", skip = 1, header = TRUE, encoding="UTF-8", stringsAsFactors = FALSE)
> read.csv("olympics.csv", skip = 1, header = TRUE, encoding="UTF-8", stringsAsFactors = FALSE)
                                    X X..Summer X01.. X02.. X03.. Total X..Winter X01...1 X02...1 X03...1
1                   Afghanistan (AFG)        13     0     0     2     2         0       0       0       0
2                       Algeria (ALG)        12     5     2     8    15         3       0       0       0
3                     Argentina (ARG)        23    18    24    28    70        18       0       0       0
4                       Armenia (ARM)         5     1     2     9    12         6       0       0       0
5             Australasia (ANZ) [ANZ]         2     3     4     5    12         0       0       0       0
6           Australia (AUS) [AUS] [Z]        25   139   152   177   468        18       5       3       4
7                       Austria (AUT)        26    18    33    35    86        22      59      78      81
8                    Azerbaijan (AZE)         5     6     5    15    26         5       0       0       0
9                       Bahamas (BAH)        15     5     2     5    12         0       0       0       0
10                      Bahrain (BRN)         8     0     0     1     1         0       0       0       0
11               Barbados (BAR) [BAR]        11     0     0     1     1         0       0       0       0
12                      Belarus (BLR)         5    12    24    39    75         6       6       4       5
13                      Belgium (BEL)        25    37    52    53   142        20       1       1       3
14                      Bermuda (BER)        17     0     0     1     1         7       0       0       0
15            Bohemia (BOH) [BOH] [Z]         3     0     1     3     4         0       0       0       0
16                     Botswana (BOT)         9     0     1     0     1         0       0       0       0
17                       Brazil (BRA)        21    23    30    55   108         7       0       0       0
18    British West Indies (BWI) [BWI]         1     0     0     2     2         0       0       0       0
19                 Bulgaria (BUL) [H]        19    51    85    78   214        19       1       2       3
20                      Burundi (BDI)         5     1     0     0     1         0       0       0       0
21                     Cameroon (CMR)        13     3     1     1     5         1       0       0       0
22                       Canada (CAN)        25    59    99   121   279        22      62      56      52
23                    Chile (CHI) [I]        22     2     7     4    13        16       0       0       0
24                  China (CHN) [CHN]         9   201   146   126   473        10      12      22      19
25                     Colombia (COL)        18     2     6    11    19         1       0       0       0
26                   Costa Rica (CRC)        14     1     1     2     4         6       0       0       0
27            Ivory Coast (CIV) [CIV]        12     0     1     0     1         0       0       0       0
28                      Croatia (CRO)         6     6     7    10    23         7       4       6       1
29                     Cuba (CUB) [Z]        19    72    67    70   209         0       0       0       0
30                       Cyprus (CYP)         9     0     1     0     1        10       0       0       0
31         Czech Republic (CZE) [CZE]         5    14    15    15    44         6       7       9       8
32         Czechoslovakia (TCH) [TCH]        16    49    49    45   143        16       2       8      15
33                  Denmark (DEN) [Z]        26    43    68    68   179        13       0       1       0
34                 Djibouti (DJI) [B]         7     0     0     1     1         0       0       0       0
35           Dominican Republic (DOM)        13     3     2     1     6         0       0       0       0
36                      Ecuador (ECU)        13     1     1     0     2         0       0       0       0
37              Egypt (EGY) [EGY] [Z]        21     7     9    10    26         1       0       0       0
38                      Eritrea (ERI)         4     0     0     1     1         0       0       0       0
39                      Estonia (EST)        11     9     9    15    33         9       4       2       1
40                     Ethiopia (ETH)        12    21     7    17    45         2       0       0       0
41                      Finland (FIN)        24   101    84   117   302        22      42      62      57
42           France (FRA) [O] [P] [Z]        27   202   223   246   671        22      31      31      47
43                        Gabon (GAB)         9     0     1     0     1         0       0       0       0
44                      Georgia (GEO)         5     6     5    14    25         6       0       0       0
45            Germany (GER) [GER] [Z]        15   174   182   217   573        11      78      78      53
46 United Team of Germany (EUA) [EUA]         3    28    54    36   118         3       8       6       5
47           East Germany (GDR) [GDR]         5   153   129   127   409         6      39      36      35
48           West Germany (FRG) [FRG]         5    56    67    81   204         6      11      15      13
49                  Ghana (GHA) [GHA]        13     0     1     3     4         1       0       0       0
50      Great Britain (GBR) [GBR] [Z]        27   236   272   272   780        22      10       4      12
51                   Greece (GRE) [Z]        27    30    42    39   111        18       0       0       0
52                      Grenada (GRN)         8     1     0     0     1         0       0       0       0
53                    Guatemala (GUA)        13     0     1     0     1         1       0       0       0
54                 Guyana (GUY) [GUY]        16     0     0     1     1         0       0       0       0
55                    Haiti (HAI) [J]        14     0     1     1     2         0       0       0       0
56              Hong Kong (HKG) [HKG]        15     1     1     1     3         4       0       0       0
57                      Hungary (HUN)        25   167   144   165   476        22       0       2       4
58                      Iceland (ISL)        19     0     2     2     4        17       0       0       0
59                    India (IND) [F]        23     9     6    11    26         9       0       0       0
60                    Indonesia (INA)        14     6    10    11    27         0       0       0       0
61                     Iran (IRI) [K]        15    15    20    25    60        10       0       0       0
62                         Iraq (IRQ)        13     0     0     1     1         0       0       0       0
   Total.1 X..Games X01...2 X02...2 X03...2 Combined.total
1        0       13       0       0       2              2
2        0       15       5       2       8             15
3        0       41      18      24      28             70
4        0       11       1       2       9             12
5        0        2       3       4       5             12
6       12       43     144     155     181            480
7      218       48      77     111     116            304
8        0       10       6       5      15             26
9        0       15       5       2       5             12
10       0        8       0       0       1              1
11       0       11       0       0       1              1
12      15       11      18      28      44             90
13       5       45      38      53      56            147
14       0       24       0       0       1              1
15       0        3       0       1       3              4
16       0        9       0       1       0              1
17       0       28      23      30      55            108
18       0        1       0       0       2              2
19       6       38      52      87      81            220
20       0        5       1       0       0              1
21       0       14       3       1       1              5
22     170       47     121     155     173            449
23       0       38       2       7       4             13
24      53       19     213     168     145            526
25       0       19       2       6      11             19
26       0       20       1       1       2              4
27       0       12       0       1       0              1
28      11       13      10      13      11             34
29       0       19      72      67      70            209
30       0       19       0       1       0              1
31      24       11      21      24      23             68
32      25       32      51      57      60            168
33       1       39      43      69      68            180
34       0        7       0       0       1              1
35       0       13       3       2       1              6
36       0       13       1       1       0              2
37       0       22       7       9      10             26
38       0        4       0       0       1              1
39       7       20      13      11      16             40
40       0       14      21       7      17             45
41     161       46     143     146     174            463
42     109       49     233     254     293            780
43       0        9       0       1       0              1
44       0       11       6       5      14             25
45     209       26     252     260     270            782
46      19        6      36      60      41            137
47     110       11     192     165     162            519
48      39       11      67      82      94            243
49       0       14       0       1       3              4
50      26       49     246     276     284            806
51       0       45      30      42      39            111
52       0        8       1       0       0              1
53       0       14       0       1       0              1
54       0       16       0       0       1              1
55       0       14       0       1       1              2
56       0       19       1       1       1              3
57       6       47     167     146     169            482
58       0       36       0       2       2              4
59       0       32       9       6      11             26
60       0       14       6      10      11             27
61       0       25      15      20      25             60
62       0       13       0       0       1              1
 [ reached 'max' / getOption("max.print") -- omitted 85 rows ]

2. Першому стовпцю дати назву “Country”
3. Автоматично в циклі згенерувати назви останніх стовпців за наступними правилами:
3.1. Видалити з назви “X.U.2116..”, тобто “X.U.2116..Summer” буде “Summer”
3.2. “X01..” замінити на “Gold”, тобто “ X01...1” буде “Gold.1”
3.3. “X02..” та “X03..” замінити на “Silver” та “Bronze” відповідно
В результаті повинні бути наступні назви стовпців: "Country", "Summer", "Gold", "Silver", "Bronze", "Total", "Winter", "Gold.1", "Silver.1", "Bronze.1", "Total.1", "Games", "Gold.2", "Silver.2", "Bronze.2", "Combined.total"
4. Необхідно привести назви країн до виду "Afghanistan", "Algeria" і т.п. Для цього можна використати функцію str_split бібліотеки stringr. В назві країн не повинно бути пробілів на початку та в кінці.
5. Додайте до дата фрейму новий стовпець “ID”, в який запишіть трибуквений код країна. Наприклад, "AFG", "ALG" і т.п.
6. Видаліть з дата фрейму останню строку “Totals”
Для кожного наступного питання напишіть функцію, яка повертає вказаний
результат. Назви функції “answer_one” для питання 1, “answer_two” для питання 2 і т.д.
> prepare_set <- function(file_name) {
+ df <- read.csv(file_name, skip = 1, header = TRUE, encoding = "UTF-8", stringsAsFactors = FALSE)
+ names(df)[1] <- "Country"
+ t<-length(colnames(df[1]))
+ for (i in 1:t) {
+ colnames(df)=sub("X..", "", colnames(df), fixed=TRUE)
+ colnames(df)=sub("X01..", "Gold", colnames(df))
+ colnames(df)=sub("X02..", "Silver", colnames(df))
+ colnames(df)=sub("X03..", "Bronze", colnames(df))
+ }
+ spl<-strsplit( df$Country, "[(]" )
+ df$Country<-sapply(spl, "[", 1)
+ df$Country<-str_trim(df$Country)
+ df$ID<-str_sub(sapply(spl, "[", 2), 1, 3)
+ df<-df[-which(df$Country=="Totals"), ]
+ df
+ }

Питання 1
Котра країна виграла найбільшу кількість золотих нагород на літніх іграх? Функція повинна повернути одне текстове значення.
> answer_one<-function() {
+ olympics[which.max(olympics$Gold), "Country"]
+ }
> answer_one()
[1] "United States"

Питання 2
Яка країна має найбільшу різницю між кількістю нагород на літніх та зимових іграх? Функція повинна повернути одне текстове значення.
> answer_two<-function() {
+ olympics[which.max(olympics$Total-olympics$Total.1), "Country"]
+ }
> answer_two()
[1] "United States"

Питання 3
В якій крайні найбільша різниця між літніми та зимовими золотими нагородами відносно до загальної кількості нагород (Summer Gold - Winter Gold) / Total Gold.
Врахувати тільки країни які мають як мінімум по одній нагороді в літніх та зимових іграх.
Функція повинна повернути одне текстове значення.
> answer_three<-function() {
+ my_subset<-subset(olympics, Gold>=1 & Gold.1>=1)
+ my_subset[which.max((my_subset$Gold-my_subset$Gold.1)/my_subset$Gold.2), "Country"]
+ }
> answer_three()
[1] "Bulgaria"

Питання 4
Необхідно знайти кількість балів по кожній крайні. Бали рахуються наступним чином: Золота нагорода Gold.2 це три бали, срібна Silver.2 - 2 бали та бронзова Bronze.2 – 1 бал.
Функція повинна повертати дата фрейм довжиною 146, який складається з двох колонок: "Country", "Points".
> answer_four<-function() {
+ olympics$Points<-(olympics$Gold.2*3 + olympics$Silver.2*2 + olympics$Bronze.2*1)
+ olympics[, c("Country", "Points")]
+ }
> answer_four()
                             Country Points
1                        Afghanistan      2
2                            Algeria     27
3                          Argentina    130
4                            Armenia     16
5                        Australasia     22
6                          Australia    923
7                            Austria    569
8                         Azerbaijan     43
9                            Bahamas     24
10                           Bahrain      1
11                          Barbados      1
12                           Belarus    154
13                           Belgium    276
14                           Bermuda      1
15                           Bohemia      5
16                          Botswana      2
17                            Brazil    184
18               British West Indies      2
19                          Bulgaria    411
20                           Burundi      3
21                          Cameroon     12
22                            Canada    846
23                             Chile     24
24                             China   1120
25                          Colombia     29
26                        Costa Rica      7
27                       Ivory Coast      2
28                           Croatia     67
29                              Cuba    420
30                            Cyprus      2
31                    Czech Republic    134
32                    Czechoslovakia    327
33                           Denmark    335
34                          Djibouti      1
35                Dominican Republic     14
36                           Ecuador      5
37                             Egypt     49
38                           Eritrea      1
39                           Estonia     77
40                          Ethiopia     94
41                           Finland    895
42                            France   1500
43                             Gabon      2
44                           Georgia     42
45                           Germany   1546
46            United Team of Germany    269
47                      East Germany   1068
48                      West Germany    459
49                             Ghana      5
50                     Great Britain   1574
51                            Greece    213
52                           Grenada      3
53                         Guatemala      2
54                            Guyana      1
55                             Haiti      3
56                         Hong Kong      6
57                           Hungary    962
58                           Iceland      6
59                             India     50
60                         Indonesia     49
61                              Iran    110
62                              Iraq      1
63                           Ireland     55
64                            Israel     10
65                             Italy   1333
66                           Jamaica    131
67                             Japan    866
68                        Kazakhstan    113
69                             Kenya    168
70                       North Korea     90
71                       South Korea    609
72                            Kuwait      2
73                        Kyrgyzstan      4
74                            Latvia     47
75                           Lebanon      6
76                     Liechtenstein     15
77                         Lithuania     38
78                        Luxembourg      9
79                         Macedonia      1
80                          Malaysia      9
81                         Mauritius      1
82                            Mexico    109
83                           Moldova      9
84                          Mongolia     37
85                        Montenegro      2
86                           Morocco     39
87                        Mozambique      4
88                           Namibia      8
89                       Netherlands    727
90              Netherlands Antilles      2
91                       New Zealand    203
92                             Niger      1
93                           Nigeria     37
94                            Norway    985
95                          Pakistan     19
96                            Panama      5
97                          Paraguay      2
98                              Peru      9
99                       Philippines     11
100                           Poland    520
101                         Portugal     39
102                      Puerto Rico     10
103                            Qatar      4
104                          Romania    572
105                           Russia   1042
106                   Russian Empire     14
107                     Soviet Union   2526
108                     Unified Team    287
109                     Saudi Arabia      4
110                          Senegal      2
111                           Serbia     11
112            Serbia and Montenegro     17
113                        Singapore      6
114                         Slovakia     58
115                         Slovenia     56
116                     South Africa    148
117                            Spain    268
118                        Sri Lanka      4
119                            Sudan      2
120                         Suriname      4
121                           Sweden   1217
122                      Switzerland    630
123                            Syria      6
124                   Chinese Taipei     32
125                       Tajikistan      4
126                         Tanzania      4
127                         Thailand     44
128                             Togo      1
129                            Tonga      2
130              Trinidad and Tobago     27
131                          Tunisia     19
132                           Turkey    191
133                           Uganda     14
134                          Ukraine    220
135             United Arab Emirates      3
136                    United States   5684
137                          Uruguay     16
138                       Uzbekistan     38
139                        Venezuela     18
140                          Vietnam      4
141                   Virgin Islands      2
142                       Yugoslavia    171
143 Independent Olympic Participants      4
144                           Zambia      3
145                         Zimbabwe     18
146                       Mixed team     38

Частина 2.
Для наступних питань використаємо дані перепису населення від United States Census Bureau. Цей набір даних містить дані по населенню для округів і штатів в США з 2010 по 2015 рокі. В цьому документі є опис назв змінних.
Завантажити файл можна за посиланням https://www.dropbox.com/s/c1b2vqg8i3m1n93/census.csv?dl=0
Файл необхідно завантажити в змінну census_df #Зчитуємо файл census_df <- read.csv("census.csv", stringsAsFactors = FALSE)
> census_df <- read.csv("census.csv", stringsAsFactors = FALSE)
> census_df
   SUMLEV REGION DIVISION STATE COUNTY  STNAME         CTYNAME CENSUS2010POP ESTIMATESBASE2010
1      40      3        6     1      0 Alabama         Alabama       4779736           4780127
2      50      3        6     1      1 Alabama  Autauga County         54571             54571
3      50      3        6     1      3 Alabama  Baldwin County        182265            182265
4      50      3        6     1      5 Alabama  Barbour County         27457             27457
5      50      3        6     1      7 Alabama     Bibb County         22915             22919
6      50      3        6     1      9 Alabama   Blount County         57322             57322
7      50      3        6     1     11 Alabama  Bullock County         10914             10915
8      50      3        6     1     13 Alabama   Butler County         20947             20946
9      50      3        6     1     15 Alabama  Calhoun County        118572            118586
10     50      3        6     1     17 Alabama Chambers County         34215             34170
   POPESTIMATE2010 POPESTIMATE2011 POPESTIMATE2012 POPESTIMATE2013 POPESTIMATE2014 POPESTIMATE2015
1          4785161         4801108         4816089         4830533         4846411         4858979
2            54660           55253           55175           55038           55290           55347
3           183193          186659          190396          195126          199713          203709
4            27341           27226           27159           26973           26815           26489
5            22861           22733           22642           22512           22549           22583
6            57373           57711           57776           57734           57658           57673
7            10887           10629           10606           10628           10829           10696
8            20944           20673           20408           20261           20276           20154
9           118437          117768          117286          116575          115993          115620
10           34098           33993           34075           34153           34052           34123
   NPOPCHG_2010 NPOPCHG_2011 NPOPCHG_2012 NPOPCHG_2013 NPOPCHG_2014 NPOPCHG_2015 BIRTHS2010 BIRTHS2011
1          5034        15947        14981        14444        15878        12568      14226      59689
2            89          593          -78         -137          252           57        151        636
3           928         3466         3737         4730         4587         3996        517       2187
4          -116         -115          -67         -186         -158         -326         70        335
5           -58         -128          -91         -130           37           34         44        266
6            51          338           65          -42          -76           15        183        744
7           -28         -258          -23           22          201         -133         39        169
8            -2         -271         -265         -147           15         -122         65        276
9          -149         -669         -482         -711         -582         -373        317       1382
10          -72         -105           82           78         -101           71         81        401
   BIRTHS2012 BIRTHS2013 BIRTHS2014 BIRTHS2015 DEATHS2010 DEATHS2011 DEATHS2012 DEATHS2013 DEATHS2014
1       59062      57938      58334      58305      11089      48811      48357      50843      50228
2         615        574        623        600        152        507        558        583        504
3        2092       2160       2186       2240        532       1825       1879       1902       2044
4         300        283        260        269        128        319        291        294        310
5         245        259        247        253         34        278        237        281        211
6         710        646        618        603        133        570        592        585        589
7         122        132        118        123         52        132        116        120         99
8         241        240        267        257         60        261        271        261        265
9        1357       1309       1355       1335        312       1326       1357       1412       1407
10        393        404        421        429         80        441        475        452        491
   DEATHS2015 NATURALINC2010 NATURALINC2011 NATURALINC2012 NATURALINC2013 NATURALINC2014 NATURALINC2015
1       50330           3137          10878          10705           7095           8106           7975
2         467             -1            129             57             -9            119            133
3        1992            -15            362            213            258            142            248
4         309            -58             16              9            -11            -50            -40
5         223             10            -12              8            -22             36             30
6         590             50            174            118             61             29             13
7         109            -13             37              6             12             19             14
8         236              5             15            -30            -21              2             21
9        1395              5             56              0           -103            -52            -60
10        457              1            -40            -82            -48            -70            -28
   INTERNATIONALMIG2010 INTERNATIONALMIG2011 INTERNATIONALMIG2012 INTERNATIONALMIG2013 INTERNATIONALMIG2014
1                  1357                 4926                 4904                 4834                 5529
2                    33                   20                   16                   16                   18
3                    69                  187                  172                  170                  212
4                     2                   -4                   -7                   -3                   -2
5                     2                   10                   16                   18                   21
6                     5                    3                   19                   20                   28
7                     7                   21                   25                   28                   31
8                     0                    2                    2                    2                    2
9                     6                   43                   61                   54                   64
10                    7                   31                   29                   31                   34
   INTERNATIONALMIG2015 DOMESTICMIG2010 DOMESTICMIG2011 DOMESTICMIG2012 DOMESTICMIG2013 DOMESTICMIG2014
1                  5726             537              11            -929            1838            2816
2                    19              49             398            -161            -166             125
3                   221             856            2743            3327            4211            3799
4                     0             -62            -129             -68            -191            -105
5                    21             -69            -126            -115            -140              -4
6                    28              -3             104             -68            -101            -119
7                    32             -23            -333             -55             -12             154
8                     2              -5            -292            -240            -115              22
9                    66            -155            -727            -542            -646            -519
10                   34             -74             -93             131              98             -78
   DOMESTICMIG2015 NETMIG2010 NETMIG2011 NETMIG2012 NETMIG2013 NETMIG2014 NETMIG2015 RESIDUAL2010
1            -2268       1894       4937       3975       6672       8345       3458            3
2             -140         82        418       -145       -150        143       -121            8
3             3469        925       2930       3499       4381       4011       3690           18
4             -281        -60       -133        -75       -194       -107       -281            2
5                4        -67       -116        -99       -122         17         25           -1
6              -79          2        107        -49        -81        -91        -51           -1
7             -174        -16       -312        -30         16        185       -142            1
8             -132         -5       -290       -238       -113         24       -130           -2
9             -391       -149       -684       -481       -592       -455       -325           -5
10              46        -67        -62        160        129        -44         80           -6
   RESIDUAL2011 RESIDUAL2012 RESIDUAL2013 RESIDUAL2014 RESIDUAL2015 GQESTIMATESBASE2010 GQESTIMATES2010
1           132          301          677         -573         1135              116185          116212
2            46           10           22          -10           45                 455             455
3           174           25           91          434           58                2307            2307
4             2           -1           19           -1           -5                3193            3193
5             0            0           14          -16          -21                2224            2224
6            57           -4          -22          -14           53                 489             489
7            17            1           -6           -3           -5                1690            1690
8             4            3          -13          -11          -13                 333             333
9           -41           -1          -16          -75           12                2933            2934
10           -3            4           -3           13           19                 458             458
   GQESTIMATES2011 GQESTIMATES2012 GQESTIMATES2013 GQESTIMATES2014 GQESTIMATES2015 RBIRTH2011 RBIRTH2012
1           115560          115666          116963          119088          119599   12.45302   12.28258
2              455             455             455             455             455   11.57279   11.13848
3             2307            2249            2304            2308            2309   11.82635   11.09652
4             3382            3388            3389            3353            3352   12.27848   11.03245
5             2224            2224            2224            2233            2236   11.66820   10.79890
6              489             489             489             489             489   12.92969   12.29576
7             1690            1777            1715            1757            1757   15.70924   11.49046
8              333             333             333             333             333   13.26381   11.73292
9             2882            2958            2812            2797            2804   11.70170   11.54628
10             458             458             458             458             458   11.77836   11.54728
   RBIRTH2013 RBIRTH2014 RBIRTH2015 RDEATH2011 RDEATH2012 RDEATH2013 RDEATH2014 RDEATH2015 RNATURALINC2011
1    12.01208  12.056286   12.01497  10.183524  10.056360  10.541099  10.380963  10.371556       2.2694961
2    10.41619  11.293597   10.84628   9.225478  10.106133  10.579514   9.136393   8.442022       2.3473111
3    11.20559  11.072868   11.10500   9.868812   9.966716   9.867141  10.353587   9.875515       1.9575398
4    10.45592   9.667584   10.09305  11.692048  10.701480  10.862337  11.526735  11.593877       0.5864350
5    11.47185  10.962917   11.21156  12.194587  10.446281  12.446295   9.365083   9.882124      -0.5263851
6    11.18518  10.711314   10.45686   9.905808  10.252236  10.128993  10.208680  10.231421       3.0238782
7    12.43289  10.998742   11.42857  12.269939  10.925359  11.302628   9.227758  10.127758       3.4393010
8    11.80260  13.173150   12.71333  12.542951  13.193447  12.835329  13.074475  11.674499       0.7208593
9    11.19468  11.652506   11.52785  11.227535  11.546283  12.075549  12.099687  12.045956       0.4741644
10   11.84265  12.345136   12.58526  12.953254  13.956632  13.249692  14.397771  13.406674      -1.1748983
   RNATURALINC2012 RNATURALINC2013 RNATURALINC2014 RNATURALINC2015 RINTERNATIONALMIG2011
1        2.2262204       1.4709812      1.67532229       1.6434167            1.02771996
2        1.0323469      -0.1633201      2.15720397       2.4042590            0.36392419
3        1.1298086       1.3384450      0.71928052       1.2294818            1.01121530
4        0.3309736      -0.4064140     -1.85915074      -1.5008255           -0.14660876
5        0.3526171      -0.9744430      1.59783405       1.3294337            0.43865421
6        2.0435200       1.0561856      0.50263450       0.2254381            0.05213583
7        0.5651048       1.1302628      1.77098383       1.3008130            1.95203569
8       -1.4605292      -1.0327276      0.09867528       1.0388326            0.09611457
9        0.0000000      -0.8808651     -0.44718104      -0.5181056            0.36409051
10      -2.4093554      -1.4070470     -2.05263544      -0.8214155            0.91054618
   RINTERNATIONALMIG2012 RINTERNATIONALMIG2013 RINTERNATIONALMIG2014 RINTERNATIONALMIG2015 RDOMESTICMIG2011
1             1.01983977            1.00221611            1.14271613            1.17996289      0.002294949
2             0.28978158            0.29034687            0.32629976            0.34346557      7.242091472
3             0.91233374            0.88192114            1.07385542            1.09562691     14.832960211
4            -0.25742392           -0.11084017           -0.07436603            0.00000000     -4.728132388
5             0.70523416            0.79727156            0.93206986            0.93060356     -5.527043032
6             0.32904136            0.34629036            0.48530227            0.48555896      1.807375482
7             2.35460325            2.63727983            2.88949993            2.97328688    -30.953708870
8             0.09736861            0.09835501            0.09867528            0.09893643    -14.032727010
9             0.51902967            0.46181279            0.55037666            0.56991620     -6.155669863
10            0.85208909            0.90871783            0.99699436            0.99743308     -2.731638543
   RDOMESTICMIG2012 RDOMESTICMIG2013 RDOMESTICMIG2014 RDOMESTICMIG2015 RNETMIG2011 RNETMIG2012 RNETMIG2013
1        -0.1931956         0.381066        0.5820019       -0.4673692    1.030015   0.8266442    1.383282
2        -2.9159271        -3.012349        2.2659706       -2.5307989    7.606016  -2.6261455   -2.722002
3        17.6472928        21.845705       19.2432865       17.1978722   15.844176  18.5596266   22.727626
4        -2.5006895        -7.056824       -3.9042166      -10.5432988   -4.874741  -2.7581135   -7.167664
5        -5.0688705        -6.201001       -0.1775371        0.1772578   -5.088389  -4.3636364   -5.403729
6        -1.1776217        -1.748766       -2.0625347       -1.3699699    1.859511  -0.8485804   -1.402476
7        -5.1801271        -1.130263       14.3542900      -16.1672474  -29.001673  -2.8255239    1.507017
8       -11.6842336        -5.655413        1.0854281       -6.5298046  -13.936612 -11.5868650   -5.557058
9        -4.6117062        -5.524649       -4.4632108       -3.3763217   -5.791579  -4.0926766   -5.062836
10        3.8490921         2.872721       -2.2872223        1.3494683   -1.821092   4.7011812    3.781439
   RNETMIG2014 RNETMIG2015
1    1.7247181   0.7125937
2    2.5922703  -2.1873334
3   20.3171419  18.2934991
4   -3.9785826 -10.5432988
5    0.7545327   1.1078614
6   -1.5772324  -0.8844110
7   17.2437899 -13.1939605
8    1.1841034  -6.4308682
9   -3.9128341  -2.8064055
10  -1.2902280   2.3469014
 [ reached 'max' / getOption("max.print") -- omitted 3183 rows ]

Питання 5
В якому штаті (state) більше всього округів (county)? Функція повинна повернути одне текстове значення.
> answer_five<-function() {
+ census_df_gr<-split(census_df[ , "CTYNAME"], census_df[ , "STNAME"])
+ ncounty<-sapply(census_df_gr, length)
+ which.max(ncounty)
+ }
> answer_five()
Texas 
   44

Питання 6
Якщо розглядати три найбільш населених округа (county) з кожного штату, які три найбільш населені штати (в порядку з більш до менш населеного)?
Використовуйте CENSUS2010POP. Функція повинна повернути вектор з трьох текстових значень.
> answer_six<-function() {
+ df_order<-census_df[order(census_df$STNAME, -census_df$CENSUS2010POP), ]
+ df_split<-split(df_order, df_order$STNAME)
+ df_split<-lapply(df_split, function (x) sum (x[2:4, "CENSUS2010POP"]))
+ df_split<-df_split[order(unlist(df_split), decreasing = TRUE, na.last = TRUE)]
+ names(df_split) [1:3]
+ }
> answer_six()
[1] "California" "Texas"      "Illinois"

Питання 7
Який округ (county) має найбільшу абсолютну зміну в населенні протягом періоду 2010-2015?
(Підказка: значення населення зберігається в колонках з POPESTIMATE2010 до POPESTIMATE2015. Необхідно розглядати всі шість колонок).
Якщо населення округу за 5річний період 100, 120, 80, 105, 100, 130, то найбільша різниця за період буде |130-80|=50.
Функція повинна повернути одне текстове значення.
> answer_seven<-function() {
+ df_pop2<-census_df[, 10:15]
+ pop_max<-apply(df_pop2, 1, max)
+ pop_min<-apply(df_pop2, 1, min)
+ pop_change<-(pop_max-pop_min)
+ df_pop2<-cbind(CTYNAME = census_df$CTYNAME, pop_change)
+ df_pop2[which.max(pop_change)]
+ }
> answer_seven()
[1] "Texas"

Питання 8
В census_df США поділені на 4 регіони (колонка "REGION"). Напишіть функцію, яка знаходить округи (county), що належать регіонам 1 або 2, назва яких починається з "Washington" та POPESTIMATE2015 більше ніж POPESTIMATE2014.
Функція повинна повернути 5х2 дата фрейм з колонками "STNAME", "CTYNAME".
> answer_eight <- function() {
+ df_pop3<-subset(census_df, (REGION==1 | REGION==2))
+ df_pop4<-df_pop3[grep("Washington", df_pop3$CTYNAME),]
+ df_pop5<-subset(df_pop4, POPESTIMATE2015>POPESTIMATE2014)
+ df_pop5[ , c("STNAME", "CTYNAME")]
+ }
> answer_eight()
           STNAME           CTYNAME
897          Iowa Washington County
1420    Minnesota Washington County
2346 Pennsylvania Washington County
2356 Rhode Island Washington County
3164    Wisconsin Washington County