# Practical #15

##### Practical Title: x-bar and R-charts

**Experiment:** The following are the mean and ranges of 20 samples of size 5 each. The data pertain to the overall length of fragmentation bomb base manufactured during the war by the American store camp.

| Group No. | Mean   | Range | Group No. | Mean   | Range | Group No. | Mean   | Range |
| --------- | ------ | ----- | --------- | ------ | ----- | --------- | ------ | ----- |
| 1         | 0.8372 | 0.010 | 8         | 0.8344 | 0.003 | 15        | 0.8304 | 0.007 |
| 2         | 0.8324 | 0.009 | 9         | 0.8308 | 0.002 | 16        | 0.8372 | 0.011 |
| 3         | 0.8318 | 0.008 | 10        | 0.8350 | 0.006 | 17        | 0.8282 | 0.006 |
| 4         | 0.8344 | 0.004 | 11        | 0.8380 | 0.006 | 18        | 0.8346 | 0.006 |
| 5         | 0.8346 | 0.005 | 12        | 0.8322 | 0.002 | 19        | 0.8360 | 0.004 |
| 6         | 0.8332 | 0.011 | 13        | 0.8356 | 0.013 | 20        | 0.8374 | 0.006 |
| 7         | 0.8340 | 0.009 | 14        | 0.8322 | 0.005 |           |        |       |

$(a)$ From these data, obtain the control limits for $\bar X$ and  $R-Charts$ to control the length of bomb bases produced in the future.

$(b)$ The above samples were taken every 15 minutes in order of production. The production rate was 350 units per hour and tolerance were 0.820 and 0.840 inches.

On the assumption that the lengths of the bomb bases are normally distributed, what percentage of the bomb base would you estimate to have length outside the tolerance limits when the process is under control and the levels indicated by the above data?

​		[For $n=5,$ use $A_2=0.58, \ D_3=0, \ D_4=2.12, \ d_2=2.326$]

**Aim:** To compute $(a)$ control limits for $\bar X$ and $R-charts$ to control the length of bomb bases produced in the future and $(b)$ estimate percent of bomb base outside the of tolerance limit when process is under control.

**Procedure:** $\displaystyle \bar{\bar X}=\frac{1}{n}\sum_{i=1}^n \bar X_i$   and $\displaystyle \bar R=\frac{1}{n}\sum_{i=1}^nR_i$ 

Control limits on $\bar X -chart$ is given by:

$\displaystyle UCL_{\bar X}=\bar{\bar X}+A_2\bar R$ ,      $\displaystyle LCL_{\bar X}=\bar{\bar X}-A_2\bar R$  and  $CL_{\bar X}=\bar{\bar X}$  

Control limits on $R-chart$ is given by:

$\displaystyle UCL_R=D_4\bar R$ ,          $\displaystyle LCL_R=D_3\bar R$  and  $CL_R=\bar R$ 

In case when process is in control, estimate of population mean can be obtained as- $\displaystyle \hat{\mu}=\bar{\bar X}'$    and estimate of standard deviation can be obtained from R as-  $\displaystyle\hat\sigma=\frac{\bar R'}{d_2}$ 

**R-code:** 

```R
rm(list=ls())
M_ean=c(0.8372,0.8324,0.8318,0.8344,0.8346,0.8332,0.8340,0.8344,0.8308,0.8350,0.8380,0.8322,0.8356,0.8322,0.8304,0.8372,0.8282,0.8346,0.8360,0.8374)
R_ange=c(0.010,0.009,0.008,0.004,0.005,0.011,0.009,0.003,0.002,0.006,0.006,0.002,0.013,0.005,0.007,0.011,0.006,0.006,0.004,0.006)
n=5
A_2=0.58
D_3=0
D_4=2.12
d_2=2.326
UTL=0.840
LTL=0.820
X_2bar=mean(M_ean);X_2bar
R_mean=mean(R_ange);R_mean
UCL=X_2bar+(A_2*R_mean);UCL
CL=X_2bar;CL
LCL=X_2bar-(A_2*R_mean);LCL
X_2barUpdated=(sum(M_ean)-sum( M_ean[M_ean>UCL | M_ean<LCL]))/(length(M_ean)-length( M_ean[M_ean>UCL | M_ean<LCL]));X_2barUpdated
R_meanUpdated=round((sum(R_ange)-sum(R_ange[M_ean>UCL | M_ean<LCL]))/(length(R_ange)-length(R_ange[M_ean>UCL | M_ean<LCL])),5);R_meanUpdated
UCL_bar_chart=X_2barUpdated+A_2*R_meanUpdated;UCL_bar_chart
CL_bar_chart=X_2barUpdated;CL_bar_chart
LCL_bar_chart=X_2barUpdated-A_2*R_meanUpdated;LCL_bar_chart
UCL_R=D_4*R_mean;UCL_R
CL_R=R_mean;CL_R
LCL_R=D_3*R_mean;LCL_R
Mue_hat=X_2barUpdated;Mue_hat
Sigma_hat=round(R_meanUpdated/d_2,6);Sigma_hat
p=1- (pnorm(LTL,mean=Mue_hat,sd=Sigma_hat)+pnorm(UTL,mean=Mue_hat,sd=Sigma_hat));round(p,4)
Percnt_frc_def=100*round(p,4);Percnt_frc_def
```



**R-output:**

```R
> rm(list=ls())
>M_ean=c(0.8372,0.8324,0.8318,0.8344,0.8346,0.8332,0.8340,0.8344,0.8308,0.8350,0.8380,0.8322,0.8356,0.8322,0.8304,0.8372,0.8282,0.8346,0.8360,0.8374)
>R_ange=c(0.010,0.009,0.008,0.004,0.005,0.011,0.009,0.003,0.002,0.006,0.006,0.002,0.013,0.005,0.007,0.011,0.006,0.006,0.004,0.006)
> n=5
> A_2=0.58
> D_3=0
> D_4=2.12
> d_2=2.326
> UTL=0.840
> LTL=0.820
> X_2bar=mean(M_ean);X_2bar
[1] 0.83398
> R_mean=mean(R_ange);R_mean
[1] 0.00665
> UCL=X_2bar+(A_2*R_mean);UCL
[1] 0.837837
> CL=X_2bar;CL
[1] 0.83398
> LCL=X_2bar-(A_2*R_mean);LCL
[1] 0.830123
> X_2barUpdated=(sum(M_ean)-sum( M_ean[M_ean>UCL | M_ean<LCL]))/(length(M_ean)-length( M_ean[M_ean>UCL | M_ean<LCL]));X_2barUpdated
[1] 0.8340778
> R_meanUpdated=round((sum(R_ange)-sum(R_ange[M_ean>UCL | M_ean<LCL]))/(length(R_ange)-length(R_ange[M_ean>UCL | M_ean<LCL])),5);R_meanUpdated
[1] 0.00672
> UCL_bar_chart=X_2barUpdated+A_2*R_meanUpdated;UCL_bar_chart
[1] 0.8379754
> CL_bar_chart=X_2barUpdated;CL_bar_chart
[1] 0.8340778
> LCL_bar_chart=X_2barUpdated-A_2*R_meanUpdated;LCL_bar_chart
[1] 0.8301802
> UCL_R=D_4*R_mean;UCL_R
[1] 0.014098
> CL_R=R_mean;CL_R
[1] 0.00665
> LCL_R=D_3*R_mean;LCL_R
[1] 0
> Mue_hat=X_2barUpdated;Mue_hat
[1] 0.8340778
> Sigma_hat=round(R_meanUpdated/d_2,6);Sigma_hat
[1] 0.002889
> p=1- (pnorm(LTL,mean=Mue_hat,sd=Sigma_hat)+pnorm(UTL,mean=Mue_hat,sd=Sigma_hat));round(p,4)
[1] 0.0202
> Percnt_frc_def=100*round(p,4);Percnt_frc_def
[1] 2.02
```

**Conclusion:**   From the above experiment we conclude;

- Control limit for $\bar X$ charts are  $\displaystyle UCL_{\bar X}=0.8379754, \\ CL_\bar X=0.8340778 \\ and \\ LCL_\bar X=0.8301802$

- Control limits for R-charts are $\displaystyle UCL_R=0.014098,\\ CL_R=0.00665 \\ and \\ LCL_R=0$ .

- Percent of bomb base outside the of tolerance limit when process is under control is $2.02$ .
