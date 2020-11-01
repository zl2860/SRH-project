EDA
================
Zongchao Liu
10/7/2020

Note: This is only for a simple glance at the data\! A formal analysis
would not be included in this document.

# Import data

# Helper Functions

    ## [1] "factor"

# 初步分析

# topic: 大学生偶然性行为的分布情况和相关因素探究，以及风险控制能力

Casual sex, with a high risk of sexually transmitted diseases (STDs), is
not an unusual event among college students. It has been reported that
young adults who have engaged in sexual intercourse with a relative
stranger are significantly more likely to report a sexually transmitted
infection (STI) than those who have not. While STDs affect individuals
of all ages, STDs take a particularly heavy toll on young people. CDC
estimates that youth ages 15-24 make up just over one quarter of the
sexually active population, but account for half of the 20 million new
sexually transmitted infections that occur in the United States each
year. Therefore, a continued research on the patterns of college student
casual sex, as well as the associated factors can help inform
appropriate and effective strategies to protect students from STI.

## 1\. 偶然性行为的基本情况： 发生率，人口学数据，性行为对象统计

  - 初步选出的人群demographics:7,8,13,519,534,536,469,467,131,511（抑郁量表）,518
    学校地域，高校层次，是否本科生，生理性别，月支出，父母教育程度，吸烟，饮酒，性知识的分，专业

我们以`"B15.是否发生过偶遇性行为(约炮、一夜情、买春等)"` 为标准筛选样本。
54580中共计12280人填写了该问题。在这12280人中共有2199人发生过偶然性行为，发生率=0.1790717。此外，初步的分析结果表明不同亚组人群发生偶然性行为的频率也有较大区别：
1. 东部地区高校学生发生偶然性行为的频率明显高于中西部地区高校学生 2. 男性学生发生的频率明显高于女性学生 3.
本科大学生发生的频率高于专科大学生（虽然如此，但专科学生基数较少，难以确定抽样对结果是否造成了影响）
4. 抑郁量表结果可被认定为抑郁症状的学生，发生偶然性行为的频率较高 5. 当前吸烟者发生频率远高于当前不吸烟者 6.
当前饮酒者发生频率远高于当前不吸烟者 7.
性知识得分情况在发生vs未发生过偶然性行为的两组学生人群中分布基本相同

| 高校所在地域(东中西部) | occur | total | prevalence |
| :----------- | ----: | ----: | ---------: |
| 1            |  1408 | 28525 |  0.0493602 |
| 2            |   342 | 13314 |  0.0256872 |
| 3            |   449 | 12741 |  0.0352406 |

| P6.生理性别 | occur | total | prevalence |
| :------ | ----: | ----: | ---------: |
| 女       |   920 | 35736 |  0.0257443 |
| 男       |  1279 | 18844 |  0.0678731 |

| 高校办学层次 | occur | total | prevalence |
| :----- | ----: | ----: | ---------: |
| 专科     |   356 | 17426 |  0.0204292 |
| 本科     |  1843 | 37154 |  0.0496043 |

| C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状) | occur | total | prevalence |
| :------------------------------ | ----: | ----: | ---------: |
| 抑郁                              |  1253 | 21372 |  0.0586281 |
| 正常                              |   946 | 33208 |  0.0284871 |

| C7.吸烟情况     | occur | total | prevalence |
| :---------- | ----: | ----: | ---------: |
| 从不吸烟        |  1230 | 47132 |  0.0260969 |
| 现在吸烟        |   622 |  3536 |  0.1759050 |
| 过去吸烟，但目前已不抽 |   347 |  3912 |  0.0887014 |

| C6.是否饮酒 | occur | total | prevalence |
| :------ | ----: | ----: | ---------: |
| 0       |   637 | 33473 |  0.0190303 |
| 1       |  1562 | 21107 |  0.0740039 |

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](report_EDA_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

|                                   | 0 (N=52381)          | 1 (N=2199)           | Total (N=54580)      |
| --------------------------------- | :------------------- | :------------------- | :------------------- |
| **高校所在地域(东中西部)**                  |                      |                      |                      |
| 1                                 | 27117 (51.8%)        | 1408 (64.0%)         | 28525 (52.3%)        |
| 2                                 | 12972 (24.8%)        | 342 (15.6%)          | 13314 (24.4%)        |
| 3                                 | 12292 (23.5%)        | 449 (20.4%)          | 12741 (23.3%)        |
| **高校办学层次**                        |                      |                      |                      |
| 专科                                | 17070 (32.6%)        | 356 (16.2%)          | 17426 (31.9%)        |
| 本科                                | 35311 (67.4%)        | 1843 (83.8%)         | 37154 (68.1%)        |
| **P3.是否本科生**                      |                      |                      |                      |
| 0                                 | 1591 (3.0%)          | 288 (13.1%)          | 1879 (3.4%)          |
| 1                                 | 50790 (97.0%)        | 1911 (86.9%)         | 52701 (96.6%)        |
| **P6.生理性别**                       |                      |                      |                      |
| 女                                 | 34816 (66.5%)        | 920 (41.8%)          | 35736 (65.5%)        |
| 男                                 | 17565 (33.5%)        | 1279 (58.2%)         | 18844 (34.5%)        |
| **D4.过去12个月平均每月支出(元,不含学校规定缴费项目)** |                      |                      |                      |
| Mean (SD)                         | 1841.531 (3704.702)  | 3373.517 (6360.148)  | 1903.254 (3858.970)  |
| Range                             | 100.000 - 100000.000 | 100.000 - 100000.000 | 100.000 - 100000.000 |
| **B2.感情状况**                       |                      |                      |                      |
| 一直单身                              | 20151 (38.5%)        | 177 (8.0%)           | 20328 (37.2%)        |
| 有男/女朋友(及已婚)                       | 15230 (29.1%)        | 961 (43.7%)          | 16191 (29.7%)        |
| 目前单身(恋爱过)                         | 17000 (32.5%)        | 1061 (48.2%)         | 18061 (33.1%)        |
| **C7.吸烟情况**                       |                      |                      |                      |
| 从不吸烟                              | 45902 (87.6%)        | 1230 (55.9%)         | 47132 (86.4%)        |
| 现在吸烟                              | 2914 (5.6%)          | 622 (28.3%)          | 3536 (6.5%)          |
| 过去吸烟，但目前已不抽                       | 3565 (6.8%)          | 347 (15.8%)          | 3912 (7.2%)          |
| **C6.是否饮酒**                       |                      |                      |                      |
| 0                                 | 32836 (62.7%)        | 637 (29.0%)          | 33473 (61.3%)        |
| 1                                 | 19545 (37.3%)        | 1562 (71.0%)         | 21107 (38.7%)        |
| **A16.性知识得分(满分9)**                |                      |                      |                      |
| Mean (SD)                         | 3.848 (2.326)        | 5.465 (1.936)        | 3.913 (2.334)        |
| Range                             | 0.000 - 9.000        | 0.000 - 9.000        | 0.000 - 9.000        |
| **D10.是否独生子女**                    |                      |                      |                      |
| N-Miss                            | 1572                 | 71                   | 1643                 |
| 0                                 | 35159 (69.2%)        | 1027 (48.3%)         | 36186 (68.4%)        |
| 1                                 | 15650 (30.8%)        | 1101 (51.7%)         | 16751 (31.6%)        |

## 2\. 性态度，认知情况

  - 性态度seq(132,155,2)

<!-- end list -->

    ## Warning: Unreplaced values treated as NA as .x is not compatible. Please
    ## specify replacements exhaustively or supply .default

|                                                | 0 (N=52381)   | 1 (N=2199)   | Total (N=54580) | p value  |
| ---------------------------------------------- | :------------ | :----------- | :-------------- | :------- |
| **P6.生理性别**                                    |               |              |                 | \< 0.001 |
| 女                                              | 34816 (66.5%) | 920 (41.8%)  | 35736 (65.5%)   |          |
| 男                                              | 17565 (33.5%) | 1279 (58.2%) | 18844 (34.5%)   |          |
| **A16.(性知识)月经前14天左右发生性行为最容易怀孕√**               |               |              |                 | \< 0.001 |
| 不知道                                            | 26621 (50.8%) | 741 (33.7%)  | 27362 (50.1%)   |          |
| 对                                              | 19311 (36.9%) | 1071 (48.7%) | 20382 (37.3%)   |          |
| 错                                              | 6449 (12.3%)  | 387 (17.6%)  | 6836 (12.5%)    |          |
| **(性知识)通常精子在女性体内可以存活7天左右×**                    |               |              |                 | \< 0.001 |
| 不知道                                            | 25419 (48.5%) | 639 (29.1%)  | 26058 (47.7%)   |          |
| 对                                              | 18011 (34.4%) | 962 (43.7%)  | 18973 (34.8%)   |          |
| 错                                              | 8951 (17.1%)  | 598 (27.2%)  | 9549 (17.5%)    |          |
| **(性知识)只要时机准确，体外射精可以有效地避免怀孕×**                 |               |              |                 | \< 0.001 |
| 不知道                                            | 16835 (32.1%) | 127 (5.8%)   | 16962 (31.1%)   |          |
| 对                                              | 12863 (24.6%) | 363 (16.5%)  | 13226 (24.2%)   |          |
| 错                                              | 22683 (43.3%) | 1709 (77.7%) | 24392 (44.7%)   |          |
| **(性知识)安全期同房可以有效地避免怀孕×**                       |               |              |                 | \< 0.001 |
| 不知道                                            | 15841 (30.2%) | 210 (9.5%)   | 16051 (29.4%)   |          |
| 对                                              | 12314 (23.5%) | 328 (14.9%)  | 12642 (23.2%)   |          |
| 错                                              | 24226 (46.2%) | 1661 (75.5%) | 25887 (47.4%)   |          |
| **(性知识)在发生性行为时，安全套是唯一一种既能预防怀孕，又能预防性病、艾滋病的方式√** |               |              |                 | \< 0.001 |
| 不知道                                            | 9985 (19.1%)  | 91 (4.1%)    | 10076 (18.5%)   |          |
| 对                                              | 26484 (50.6%) | 1700 (77.3%) | 28184 (51.6%)   |          |
| 错                                              | 15912 (30.4%) | 408 (18.6%)  | 16320 (29.9%)   |          |
| **(性知识)蚊虫叮咬能够传播艾滋病×**                          |               |              |                 | \< 0.001 |
| 不知道                                            | 7200 (13.7%)  | 130 (5.9%)   | 7330 (13.4%)    |          |
| 对                                              | 15413 (29.4%) | 538 (24.5%)  | 15951 (29.2%)   |          |
| 错                                              | 29768 (56.8%) | 1531 (69.6%) | 31299 (57.3%)   |          |
| **(性知识)生殖器疱疹是一种性传播疾病√**                        |               |              |                 | \< 0.001 |
| 不知道                                            | 23019 (43.9%) | 449 (20.4%)  | 23468 (43.0%)   |          |
| 对                                              | 23077 (44.1%) | 1409 (64.1%) | 24486 (44.9%)   |          |
| 错                                              | 6285 (12.0%)  | 341 (15.5%)  | 6626 (12.1%)    |          |
| **(性知识)女性怀孕以后，月经还会继续来两三个月×**                   |               |              |                 | \< 0.001 |
| 不知道                                            | 20953 (40.0%) | 703 (32.0%)  | 21656 (39.7%)   |          |
| 对                                              | 3857 (7.4%)   | 201 (9.1%)   | 4058 (7.4%)     |          |
| 错                                              | 27571 (52.6%) | 1295 (58.9%) | 28866 (52.9%)   |          |
| **(性知识)相比普通人流，无痛人流更加安全×**                      |               |              |                 | \< 0.001 |
| 不知道                                            | 27344 (52.2%) | 876 (39.8%)  | 28220 (51.7%)   |          |
| 对                                              | 5555 (10.6%)  | 279 (12.7%)  | 5834 (10.7%)    |          |
| 错                                              | 19482 (37.2%) | 1044 (47.5%) | 20526 (37.6%)   |          |

## 3\. potential related factors

  - 
7,8,14,18,159,156,167,173,174,177,180

**不同地域，性别，学校层次，精神状况水平下偶然性行为的发生率**

crude发生率=2199/12280= 0.1790717

## 4\. Association

    ##  [1] "高校所在地域(东中西部)"                            
    ##  [2] "高校办学层次"                                      
    ##  [3] "P3.是否本科生"                                     
    ##  [4] "P6.生理性别"                                       
    ##  [5] "D4.过去12个月平均每月支出(元,不含学校规定缴费项目)"
    ##  [6] "B2.感情状况"                                       
    ##  [7] "C7.吸烟情况"                                       
    ##  [8] "C6.是否饮酒"                                       
    ##  [9] "A16.性知识得分(满分9)"                             
    ## [10] "B15.是否发生过偶遇性行为(约炮、一夜情、买春等)"    
    ## [11] "D10.是否独生子女"                                  
    ## [12] "C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)"

    ## 
    ## Call:
    ## glm(formula = `B15.是否发生过偶遇性行为(约炮、一夜情、买春等)` ~ 
    ##     ., family = binomial(link = "logit"), data = reg)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -2.0851  -0.2617  -0.1451  -0.0826   3.5877  
    ## 
    ## Coefficients:
    ##                                                                Estimate
    ## (Intercept)                                                   -7.142459
    ## `高校所在地域(东中西部)`2                                     -0.102593
    ## `高校所在地域(东中西部)`3                                     -0.176972
    ## 高校办学层次本科                                               0.515258
    ## P3.是否本科生1                                                -0.745807
    ## P6.生理性别男                                                  0.991640
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500  0.713437
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     1.505135
    ## B2.感情状况有男/女朋友(及已婚)                                 1.197131
    ## B2.感情状况目前单身(恋爱过)                                    1.364015
    ## C7.吸烟情况现在吸烟                                            1.212985
    ## C7.吸烟情况过去吸烟，但目前已不抽                              0.682640
    ## C6.是否饮酒1                                                   0.398401
    ## `A16.性知识得分(满分9)`                                        0.213859
    ## D10.是否独生子女1                                              0.109749
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                0.058755
    ##                                                               Std. Error
    ## (Intercept)                                                     0.155269
    ## `高校所在地域(东中西部)`2                                       0.067759
    ## `高校所在地域(东中西部)`3                                       0.062542
    ## 高校办学层次本科                                                0.067600
    ## P3.是否本科生1                                                  0.078220
    ## P6.生理性别男                                                   0.051362
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500   0.069814
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500      0.073283
    ## B2.感情状况有男/女朋友(及已婚)                                  0.089021
    ## B2.感情状况目前单身(恋爱过)                                     0.087661
    ## C7.吸烟情况现在吸烟                                             0.064411
    ## C7.吸烟情况过去吸烟，但目前已不抽                               0.071278
    ## C6.是否饮酒1                                                    0.055709
    ## `A16.性知识得分(满分9)`                                         0.012390
    ## D10.是否独生子女1                                               0.050209
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                 0.003754
    ##                                                               z value
    ## (Intercept)                                                   -46.000
    ## `高校所在地域(东中西部)`2                                      -1.514
    ## `高校所在地域(东中西部)`3                                      -2.830
    ## 高校办学层次本科                                                7.622
    ## P3.是否本科生1                                                 -9.535
    ## P6.生理性别男                                                  19.307
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500  10.219
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     20.539
    ## B2.感情状况有男/女朋友(及已婚)                                 13.448
    ## B2.感情状况目前单身(恋爱过)                                    15.560
    ## C7.吸烟情况现在吸烟                                            18.832
    ## C7.吸烟情况过去吸烟，但目前已不抽                               9.577
    ## C6.是否饮酒1                                                    7.152
    ## `A16.性知识得分(满分9)`                                        17.261
    ## D10.是否独生子女1                                               2.186
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                15.651
    ##                                                               Pr(>|z|)    
    ## (Intercept)                                                    < 2e-16 ***
    ## `高校所在地域(东中西部)`2                                      0.13000    
    ## `高校所在地域(东中西部)`3                                      0.00466 ** 
    ## 高校办学层次本科                                              2.49e-14 ***
    ## P3.是否本科生1                                                 < 2e-16 ***
    ## P6.生理性别男                                                  < 2e-16 ***
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500  < 2e-16 ***
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     < 2e-16 ***
    ## B2.感情状况有男/女朋友(及已婚)                                 < 2e-16 ***
    ## B2.感情状况目前单身(恋爱过)                                    < 2e-16 ***
    ## C7.吸烟情况现在吸烟                                            < 2e-16 ***
    ## C7.吸烟情况过去吸烟，但目前已不抽                              < 2e-16 ***
    ## C6.是否饮酒1                                                  8.58e-13 ***
    ## `A16.性知识得分(满分9)`                                        < 2e-16 ***
    ## D10.是否独生子女1                                              0.02883 *  
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                < 2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 17848  on 52936  degrees of freedom
    ## Residual deviance: 13479  on 52921  degrees of freedom
    ##   (1643 observations deleted due to missingness)
    ## AIC: 13511
    ## 
    ## Number of Fisher Scoring iterations: 7

    ## 
    ## Call:
    ## glm(formula = `B15.是否发生过偶遇性行为(约炮、一夜情、买春等)` ~ 
    ##     ., family = binomial(link = "logit"), data = reg_male)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -1.9818  -0.3689  -0.2280  -0.1356   3.4199  
    ## 
    ## Coefficients:
    ##                                                                Estimate
    ## (Intercept)                                                   -5.444835
    ## `高校所在地域(东中西部)`2                                     -0.060461
    ## `高校所在地域(东中西部)`3                                     -0.107167
    ## 高校办学层次本科                                               0.595007
    ## P3.是否本科生1                                                -0.806060
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500  0.807282
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     1.748917
    ## B2.感情状况有男/女朋友(及已婚)                                 0.957225
    ## B2.感情状况目前单身(恋爱过)                                    1.125547
    ## C7.吸烟情况现在吸烟                                            0.921765
    ## C7.吸烟情况过去吸烟，但目前已不抽                              0.345982
    ## C6.是否饮酒1                                                   0.132881
    ## `A16.性知识得分(满分9)`                                        0.155966
    ## D10.是否独生子女1                                              0.067666
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                0.056358
    ##                                                               Std. Error
    ## (Intercept)                                                     0.184607
    ## `高校所在地域(东中西部)`2                                       0.090105
    ## `高校所在地域(东中西部)`3                                       0.083962
    ## 高校办学层次本科                                                0.084749
    ## P3.是否本科生1                                                  0.104704
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500   0.090664
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500      0.095087
    ## B2.感情状况有男/女朋友(及已婚)                                  0.107456
    ## B2.感情状况目前单身(恋爱过)                                     0.104043
    ## C7.吸烟情况现在吸烟                                             0.081039
    ## C7.吸烟情况过去吸烟，但目前已不抽                               0.102035
    ## C6.是否饮酒1                                                    0.073441
    ## `A16.性知识得分(满分9)`                                         0.015656
    ## D10.是否独生子女1                                               0.066783
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                 0.005211
    ##                                                               z value
    ## (Intercept)                                                   -29.494
    ## `高校所在地域(东中西部)`2                                      -0.671
    ## `高校所在地域(东中西部)`3                                      -1.276
    ## 高校办学层次本科                                                7.021
    ## P3.是否本科生1                                                 -7.698
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500   8.904
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     18.393
    ## B2.感情状况有男/女朋友(及已婚)                                  8.908
    ## B2.感情状况目前单身(恋爱过)                                    10.818
    ## C7.吸烟情况现在吸烟                                            11.374
    ## C7.吸烟情况过去吸烟，但目前已不抽                               3.391
    ## C6.是否饮酒1                                                    1.809
    ## `A16.性知识得分(满分9)`                                         9.962
    ## D10.是否独生子女1                                               1.013
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                10.816
    ##                                                               Pr(>|z|)    
    ## (Intercept)                                                    < 2e-16 ***
    ## `高校所在地域(东中西部)`2                                     0.502221    
    ## `高校所在地域(东中西部)`3                                     0.201822    
    ## 高校办学层次本科                                              2.21e-12 ***
    ## P3.是否本科生1                                                1.38e-14 ***
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500  < 2e-16 ***
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     < 2e-16 ***
    ## B2.感情状况有男/女朋友(及已婚)                                 < 2e-16 ***
    ## B2.感情状况目前单身(恋爱过)                                    < 2e-16 ***
    ## C7.吸烟情况现在吸烟                                            < 2e-16 ***
    ## C7.吸烟情况过去吸烟，但目前已不抽                             0.000697 ***
    ## C6.是否饮酒1                                                  0.070396 .  
    ## `A16.性知识得分(满分9)`                                        < 2e-16 ***
    ## D10.是否独生子女1                                             0.310950    
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                < 2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 8964.4  on 18072  degrees of freedom
    ## Residual deviance: 7203.9  on 18058  degrees of freedom
    ##   (771 observations deleted due to missingness)
    ## AIC: 7233.9
    ## 
    ## Number of Fisher Scoring iterations: 7

    ## 
    ## Call:
    ## glm(formula = `B15.是否发生过偶遇性行为(约炮、一夜情、买春等)` ~ 
    ##     ., family = binomial(link = "logit"), data = reg_female)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -1.4784  -0.1980  -0.1045  -0.0534   3.7950  
    ## 
    ## Coefficients:
    ##                                                                Estimate
    ## (Intercept)                                                   -8.106811
    ## `高校所在地域(东中西部)`2                                     -0.117510
    ## `高校所在地域(东中西部)`3                                     -0.255940
    ## 高校办学层次本科                                               0.343140
    ## P3.是否本科生1                                                -0.665309
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500  0.550006
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     1.078426
    ## B2.感情状况有男/女朋友(及已婚)                                 1.782499
    ## B2.感情状况目前单身(恋爱过)                                    1.958610
    ## C7.吸烟情况现在吸烟                                            1.789205
    ## C7.吸烟情况过去吸烟，但目前已不抽                              1.034590
    ## C6.是否饮酒1                                                   0.691485
    ## `A16.性知识得分(满分9)`                                        0.299478
    ## D10.是否独生子女1                                              0.115684
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                0.052316
    ##                                                               Std. Error
    ## (Intercept)                                                     0.265743
    ## `高校所在地域(东中西部)`2                                       0.103209
    ## `高校所在地域(东中西部)`3                                       0.094381
    ## 高校办学层次本科                                                0.110687
    ## P3.是否本科生1                                                  0.119535
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500   0.109440
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500      0.115479
    ## B2.感情状况有男/女朋友(及已婚)                                  0.176322
    ## B2.感情状况目前单身(恋爱过)                                     0.175859
    ## C7.吸烟情况现在吸烟                                             0.105516
    ## C7.吸烟情况过去吸烟，但目前已不抽                               0.100192
    ## C6.是否饮酒1                                                    0.085207
    ## `A16.性知识得分(满分9)`                                         0.020563
    ## D10.是否独生子女1                                               0.076824
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                 0.005507
    ##                                                               z value
    ## (Intercept)                                                   -30.506
    ## `高校所在地域(东中西部)`2                                      -1.139
    ## `高校所在地域(东中西部)`3                                      -2.712
    ## 高校办学层次本科                                                3.100
    ## P3.是否本科生1                                                 -5.566
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500   5.026
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500      9.339
    ## B2.感情状况有男/女朋友(及已婚)                                 10.109
    ## B2.感情状况目前单身(恋爱过)                                    11.137
    ## C7.吸烟情况现在吸烟                                            16.957
    ## C7.吸烟情况过去吸烟，但目前已不抽                              10.326
    ## C6.是否饮酒1                                                    8.115
    ## `A16.性知识得分(满分9)`                                        14.564
    ## D10.是否独生子女1                                               1.506
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                 9.499
    ##                                                               Pr(>|z|)    
    ## (Intercept)                                                    < 2e-16 ***
    ## `高校所在地域(东中西部)`2                                      0.25489    
    ## `高校所在地域(东中西部)`3                                      0.00669 ** 
    ## 高校办学层次本科                                               0.00193 ** 
    ## P3.是否本科生1                                                2.61e-08 ***
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`1500~2500 5.02e-07 ***
    ## `D4.过去12个月平均每月支出(元,不含学校规定缴费项目)`>=2500     < 2e-16 ***
    ## B2.感情状况有男/女朋友(及已婚)                                 < 2e-16 ***
    ## B2.感情状况目前单身(恋爱过)                                    < 2e-16 ***
    ## C7.吸烟情况现在吸烟                                            < 2e-16 ***
    ## C7.吸烟情况过去吸烟，但目前已不抽                              < 2e-16 ***
    ## C6.是否饮酒1                                                  4.84e-16 ***
    ## `A16.性知识得分(满分9)`                                        < 2e-16 ***
    ## D10.是否独生子女1                                              0.13211    
    ## `C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)`                < 2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 8373.3  on 34863  degrees of freedom
    ## Residual deviance: 6083.2  on 34849  degrees of freedom
    ##   (872 observations deleted due to missingness)
    ## AIC: 6113.2
    ## 
    ## Number of Fisher Scoring iterations: 8

<table style="border-collapse:collapse; border:none;">

<tr>

<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">

 

</th>

<th colspan="3" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">

B<br>15.是否发生过偶遇性行为(约炮、一夜情、买春等)

</th>

</tr>

<tr>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">

Predictors

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

Odds
Ratios

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

CI

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

p

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

(Intercept)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.00

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.00 – 0.00

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校所在地域(东中西部)<br>\[高校所在地域(东中西部)2\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.90

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.79 – 1.03

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.130

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校所在地域(东中西部)<br>\[高校所在地域(东中西部)3\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.84

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.74 – 0.95

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>0.005</strong>

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校办学层次
\[本科\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.67

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.47 – 1.91

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

P3.是否本科生
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.47

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.41 – 0.55

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

P6.生理性别
\[男\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.70

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.44 – 2.98

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D4.过去12个月平均每月支出(元,不含学校规定缴费项目)<br>\[D4.过去12个月平均每月支出(元,不含学校规定缴费项目)1500~2500\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.04

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.78 – 2.34

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D4.过去12个月平均每月支出(元,不含学校规定缴费项目)<br>\[D4.过去12个月平均每月支出(元,不含学校规定缴费项目)\>=2500\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

4.50

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

3.91 – 5.21

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

B2.感情状况
\[有男/女朋友(及已婚)\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

3.31

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.79 – 3.95

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

B2.感情状况
\[目前单身(恋爱过)\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

3.91

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

3.30 – 4.66

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C7.吸烟情况
\[现在吸烟\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

3.36

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.96 – 3.82

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C7.吸烟情况
\[过去吸烟，但目前已不抽\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.98

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.72 – 2.27

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C6.是否饮酒
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.49

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.34 – 1.66

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

A16.性知识得分(满分9)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.24

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.21 – 1.27

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D10.是否独生子女
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.12

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.01 – 1.23

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>0.029</strong>

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.06

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.05 – 1.07

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">

Observations

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="3">

52937

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">

R<sup>2</sup>
Tjur

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="3">

0.132

</td>

</tr>

</table>

<table style="border-collapse:collapse; border:none;">

<tr>

<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">

 

</th>

<th colspan="3" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">

B<br>15.是否发生过偶遇性行为(约炮、一夜情、买春等)

</th>

</tr>

<tr>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">

Predictors

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

Odds
Ratios

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

CI

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

p

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

(Intercept)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.00

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.00 – 0.01

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校所在地域(东中西部)<br>\[高校所在地域(东中西部)2\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.94

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.79 – 1.12

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.502

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校所在地域(东中西部)<br>\[高校所在地域(东中西部)3\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.90

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.76 – 1.06

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.202

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校办学层次
\[本科\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.81

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.54 – 2.14

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

P3.是否本科生
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.45

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.36 – 0.55

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D4.过去12个月平均每月支出(元,不含学校规定缴费项目)<br>\[D4.过去12个月平均每月支出(元,不含学校规定缴费项目)1500~2500\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.24

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.88 – 2.68

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D4.过去12个月平均每月支出(元,不含学校规定缴费项目)<br>\[D4.过去12个月平均每月支出(元,不含学校规定缴费项目)\>=2500\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

5.75

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

4.78 – 6.94

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

B2.感情状况
\[有男/女朋友(及已婚)\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.60

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.12 – 3.23

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

B2.感情状况
\[目前单身(恋爱过)\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

3.08

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.52 – 3.79

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C7.吸烟情况
\[现在吸烟\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.51

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.14 – 2.95

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C7.吸烟情况
\[过去吸烟，但目前已不抽\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.41

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.15 – 1.72

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>0.001</strong>

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C6.是否饮酒
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.14

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.99 – 1.32

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.070

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

A16.性知识得分(满分9)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.17

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.13 – 1.21

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D10.是否独生子女
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.07

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.94 – 1.22

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.311

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.06

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.05 – 1.07

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">

Observations

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="3">

18073

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">

R<sup>2</sup>
Tjur

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="3">

0.127

</td>

</tr>

</table>

<table style="border-collapse:collapse; border:none;">

<tr>

<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">

 

</th>

<th colspan="3" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">

B<br>15.是否发生过偶遇性行为(约炮、一夜情、买春等)

</th>

</tr>

<tr>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">

Predictors

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

Odds
Ratios

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

CI

</td>

<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">

p

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

(Intercept)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.00

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.00 – 0.00

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校所在地域(东中西部)<br>\[高校所在地域(东中西部)2\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.89

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.72 – 1.09

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.255

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校所在地域(东中西部)<br>\[高校所在地域(东中西部)3\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.77

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.64 – 0.93

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>0.007</strong>

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

高校办学层次
\[本科\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.41

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.14 – 1.76

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>0.002</strong>

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

P3.是否本科生
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.51

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.41 – 0.65

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D4.过去12个月平均每月支出(元,不含学校规定缴费项目)<br>\[D4.过去12个月平均每月支出(元,不含学校规定缴费项目)1500~2500\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.73

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.40 – 2.15

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D4.过去12个月平均每月支出(元,不含学校规定缴费项目)<br>\[D4.过去12个月平均每月支出(元,不含学校规定缴费项目)\>=2500\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.94

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.35 – 3.70

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

B2.感情状况
\[有男/女朋友(及已婚)\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

5.94

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

4.27 – 8.53

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

B2.感情状况
\[目前单身(恋爱过)\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

7.09

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

5.09 – 10.17

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C7.吸烟情况
\[现在吸烟\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

5.98

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

4.86 – 7.35

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C7.吸烟情况
\[过去吸烟，但目前已不抽\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.81

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.31 – 3.42

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C6.是否饮酒
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

2.00

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.69 – 2.36

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

A16.性知识得分(满分9)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.35

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.30 – 1.41

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

D10.是否独生子女
\[1\]

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.12

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.97 – 1.30

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

0.132

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">

C10.抑郁量表CES-D-10总分(≥10可认为有抑郁症状)

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.05

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

1.04 – 1.07

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">

<strong>\<0.001

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">

Observations

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="3">

34864

</td>

</tr>

<tr>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">

R<sup>2</sup>
Tjur

</td>

<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="3">

0.133

</td>

</tr>

</table>

## 5\. further analysis

    ## Warning: package 'factoextra' was built under R version 3.6.2

    ## Welcome! Want to learn more? See two factoextra-related books at https://goo.gl/ve3WBa

    ##  [1] "id"                                                             
    ##  [2] "A4.曾经因为失恋(包括单相思)感到痛苦code"                        
    ##  [3] "A5.是否曾经主动上网搜索过性知识(包括避孕知识)"                  
    ##  [4] "A6.是否曾经主动上网寻找过色情信息(包括漫画、小说、图像、电影等)"
    ##  [5] "A7.(曾经阅读或观看过)色情书籍杂志code"                          
    ##  [6] "(曾经阅读或观看过)色情音像制品code"                             
    ##  [7] "(曾经阅读或观看过)在线色情文学(色情小说等)code"                 
    ##  [8] "(曾经阅读或观看过)在线色情图片code"                             
    ##  [9] "(曾经阅读或观看过)在线色情影片(包括小视频)code"                 
    ## [10] "A9.父亲能够解答有关“性”的问题code"                              
    ## [11] "A10.母亲能够解答有关“性”的问题code"                             
    ## [12] "A11.参加过学校开设的性教育、生殖健康教育或青春期教育课程code"   
    ## [13] "是否参加过学校开设的性教育、生殖健康教育或青春期教育课程"       
    ## [14] "最早参加性教育课程的时间"                                       
    ## [15] "(性教育课程是否讲授过以下知识)性侵害及预防"                     
    ## [16] "(性态度等)我能接受自己在大学时发生性行为_1"                     
    ## [17] "A17.(性态度等)进入性活跃期让我有罪恶感_1"                       
    ## [18] "(性态度等)性教育会导致【更早】发生性行为_1"                     
    ## [19] "(性态度等)性教育会导致【更多】发生性行为_1"                     
    ## [20] "(性态度等)婚前有性行为经验，往后婚姻生活会更美满_1"             
    ## [21] "(性态度等)网络使交友更加广泛而容易，也导致一夜情更普遍_1"       
    ## [22] "(性态度等)不一定每次都要带避孕套，因为不一定会“中”_1"           
    ## [23] "(性态度等)偶尔发生“一夜情”并不是对爱情的严重背叛_1"             
    ## [24] "(性态度等)同时有多个性伴侣这种现象是可以接受的_1"               
    ## [25] "(性态度等)现实社会中，男性仍旧有很重的“处女情结”_1"             
    ## [26] "(性态度等)同性恋是正常的_1"                                     
    ## [27] "(性态度等)我愿意和携带艾滋病病毒的同学一起上学_1"               
    ## [28] "B1.性取向code"                                                  
    ## [29] "B2.感情状况code"                                                
    ## [30] "B2.是否恋爱中"                                                  
    ## [31] "B2.是否恋爱过"                                                  
    ## [32] "B2-4.第一次谈恋爱年龄(周岁)"                                    
    ## [33] "B2-5.遭遇过男/女朋友出轨code"                                   
    ## [34] "B4.性需求情况code"                                              
    ## [35] "B5.性自慰情况code"                                              
    ## [36] "B6.(发生过亲密行为)牵手code"                                    
    ## [37] "(发生过亲密行为)拥抱code"                                       
    ## [38] "(发生过亲密行为)接吻code"                                       
    ## [39] "(发生过亲密行为)不触及性器官的爱抚code"                         
    ## [40] "(发生过亲密行为)口交code"                                       
    ## [41] "是否发生过口交"                                                 
    ## [42] "(发生过亲密行为)插入式性行为(阴道)code"                         
    ## [43] "是否发生过插入式性行为(阴道)"                                   
    ## [44] "(发生过亲密行为)插入式性行为(肛门)code"                         
    ## [45] "是否发生过插入式性行为(肛门)"                                   
    ## [46] "(发生过亲密行为)性行为时拍摄照片/视频code"                      
    ## [47] "(发生过亲密行为)多人性行为(3P、双飞)code"                       
    ## [48] "(发生过亲密行为)SM(带有性虐待行为的性行为)code"                 
    ## [49] "(发生过亲密行为)【性行为时】观看色情图片/视频code"              
    ## [50] "(发生过亲密行为)【性行为时】使用助性药物(如“壮阳药”)code"       
    ## [51] "(发生过亲密行为)【性行为时】使用情趣用品(如电动按摩棒)code"     
    ## [52] "B7.是否发生过插入式性行为(阴道/肛门)"                           
    ## [53] "B21.对婚前性行为的看法code"                                     
    ## [54] "B22.对“开房”或同居的看法code"                                   
    ## [55] "B23.对“一夜情”或“约炮”的看法code"                               
    ## [56] "C2.过去一周锻炼次数"                                            
    ## [57] "C5.(手机成瘾)最近一周无法控制不使用手机频率code"                
    ## [58] "C6.是否饮酒"                                                    
    ## [59] "C7.吸烟情况code"                                                
    ## [60] "C9.是否有过自杀行为"                                            
    ## [61] "D1.是否少数民族"                                                
    ## [62] "D2.宗教信仰code"                                                
    ## [63] "D6.城乡(指上大学前常住地区)code"                                
    ## [64] "D11.父亲受教育程度code"                                         
    ## [65] "D12.母亲受教育程度code"

![](report_EDA_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

    ## # A tibble: 4 x 2
    ##   cluster prevalence
    ##     <int>      <dbl>
    ## 1       1    0.00923
    ## 2       2    0.00209
    ## 3       3    0.0145 
    ## 4       4    0.142
