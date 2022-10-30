# Practical #4

##### Practical Title: Mortality and Fertility Rate


**Experiment:** Calculate the general fertility rate, total fertility rate and the gross reproduction rate from the following data,assume that for every 100 girls 106 boys are born.

| Age of Women        | 15-19   | 20-24   | 25-29   | 30-34   | 35-39   | 40-44   | 45-49  |
| ------------------- | ------- | ------- | ------- | ------- | ------- | ------- | ------ |
| Number of women     | 212,619 | 198,732 | 162,800 | 145,362 | 128,109 | 106,211 | 86,753 |
| Age S.F.R(per 1000) | 98      | 169.6   | 158.2   | 139.7   | 98.6    | 42.8    | 16.9   |

**AIM:** To calculate general fertility rate, total fertility rate and the gross reproduction rate.
**Procedure:**

*General Fertility Rate (G.F.R):* This consists in relating the total number of live births to the number of females in the reproductive or child bearing ages and is given by:

$$
G.F.R=\frac{B^t}{\displaystyle\sum_{\lambda_1}^{\lambda_2}{^fP_x}}\times k
$$

*Total Fertility Rate (T.F.R):* It is Obtained on adding the annual age-specific fertility rates and given by:

$$
T.F.R=\sum_{\lambda_1}^{\lambda_2}i_x=\sum_{\lambda_1}^{\lambda_2}\frac{B_x}{^fP_x}\times k
$$

*Gross Reproduction Rate(G.R.R):* It is defined as the sum of age-specific fertility rate calculated from female births for each year of reproductive period and given by:

$$
G.R.R=\sum_{\lambda_1}^{\lambda_2}\frac{^fB_x}{^fP_x}\times k=\sum_{\lambda_1}^{\lambda_2}{^fi_x}
$$



**R-Code:**

```r
rm(list=ls())
number_of_women_fPx=c(212619,198732,162800,145362,128109,106211,86753)
Age_SFR_per_1000=c(98,169.6,158.2,139.7,98.6,42.8,16.9)
number_of_births_B=(number_of_women_fPx)*(Age_SFR_per_1000)/1000
abs(number_of_births_B)
sum(number_of_births_B)
G_F_R=(sum(number_of_births_B)/sum(number_of_women_fPx))*1000
G_F_R
T_F_R=5*sum(Age_SFR_per_1000)
T_F_R
G_R_R=(100/(100+106))*T_F_R
G_R_R
```

**R-Console:** 

```R
> rm(list=ls())
> number_of_women_fPx=c(212619,198732,162800,145362,128109,106211,86753)
> Age_SFR_per_1000=c(98,169.6,158.2,139.7,98.6,42.8,16.9)
> number_of_births_B=(number_of_women_fPx)*(Age_SFR_per_1000)/1000
> abs(number_of_births_B)
[1] 20836.662 33704.947 25754.960 20307.071 12631.547  4545.831  1466.126
> sum(number_of_births_B)
[1] 119247.1
> G_F_R=(sum(number_of_births_B)/sum(number_of_women_fPx))*1000
> G_F_R
[1] 114.5961
> T_F_R=5*sum(Age_SFR_per_1000)
> T_F_R
[1] 3619
> G_R_R=(100/(100+106))*T_F_R
> G_R_R
[1] 1756.796
```

**Conclusion:**

From the above Experiment we conclude that:

$G.F.R=114.5961$

$T.F.R=3619$

$G.R.R= 1756.796$ 
