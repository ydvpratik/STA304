# Practical #3

##### Practical Title :  Mortality and Fertility Rate

**Experiment:** Compute G.F.R, S.F.R, T.F.R and the gross reproduction rate from the data given below:

| Age group of child <br />bearing females | 15-19 | 20-24 | 25-29 | 30-34 | 35-39 | 40-44 | 45-49 |
| ---------------------------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| Number of women ('000)                   | 16.0  | 16.4  | 15.8  | 15.2  | 14.8  | 15.0  | 14.5  |
| Total Births                             | 260   | 2244  | 1894  | 1320  | 916   | 280   | 145   |

**AIM:** To Compute G.F.R, S.F.R, T.F.R and the gross reproduction rate.

**Procedure:** 

*General Fertility Rate (G.F.R):* This consists in relating the total number of live births to the number of  females in the reproductive or child bearing ages and is given by:

$$
G.F.R=\frac{B^t}{\displaystyle\sum_{\lambda_1}^{\lambda_2}{^fP_x}}\times k
$$



*Specific Fertility Rate(S.F.R)*: Fertility rate computed w.r.t any specific factor is called S.F.R and defined as:

$$
S.F.R=\frac{Number\ of\ births \ to\ the\ female\ population\ of\ the\ specified\ section\ in\ a\ given\ period}{Total\ number\ of\ female\ population\ in\ the\ specified\ section}\times k
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
number_of_women_fPx=c(16.0,16.4,15.8,15.2,14.8,15.0,14.5)
Age_SFR_per_1000=c(98,169.6,158.2,139.7,98.6,42.8,16.9)
Number_of_Birth_nBx=c(260,2244,1894,1320,916,280,145)
age_S_F_R=((Number_of_Birth_nBx)/(number_of_women_fPx))*1000
Age_S_F_R=sum((age_S_F_R)/1000)
Age_S_F_R
G_F_R =(sum(Number_of_Birth_nBx)/(sum(number_of_women_fPx)*1000))*1000
G_F_R
T_F_R=5*sum(Age_S_F_R)
T_F_R
G_R_R=46.2/100*T_F_R
G_R_R
```

**R-Console (output):** 

```R
> rm(list=ls())
> number_of_women_fPx=c(16.0,16.4,15.8,15.2,14.8,15.0,14.5)
> Age_SFR_per_1000=c(98,169.6,158.2,139.7,98.6,42.8,16.9)
> Number_of_Birth_nBx=c(260,2244,1894,1320,916,280,145)
> age_S_F_R=((Number_of_Birth_nBx)/(number_of_women_fPx))*1000
> Age_S_F_R=sum((age_S_F_R)/1000)
> Age_S_F_R
[1] 450.3533
> G_F_R =(sum(Number_of_Birth_nBx)/(sum(number_of_women_fPx)*1000))*1000
> G_F_R
[1] 65.54318
> T_F_R=5*sum(Age_S_F_R)
> T_F_R
[1] 2251.767
> G_R_R=46.2/100*T_F_R
> G_R_R
[1] 1040.316
```

**Conclusion:**

From the above Experiment we conclude that:

$G.F.R=65.54318$

$T.F.R=2251.767$

$G.R.R= 1040.316$

$S.F.R=450.3533$
