# Practical #20

##### Practical Topic: Stratified Random Sampling

**Experiment:** Below Table present the summary of data for complete census of all the 2,010 farms in a region. the farms were stratified according to farm-size in acres into seven strata, as shown in Col. 2 of the table. The number of farms in the different strata $N_i$  are given in the Col.3. The population values of the strata means for the area under wheat $(\bar Y_{N_i})$ and those of strata standard deviation for the area under wheat $(S_i)$ are given in the subsequent columns.

| Stratum No. | Farm Size (In<br />Acres) | No. of<br />Farms $(N_i)$ | Average Area Under Wheat per Farm in<br />            Acres $(\bar Y_{N_i})$ | St. Deviations of Area under <br />Wheat per Farm in Acres $S_i$ |
| ----------- | :------------------------ | :-----------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| 1           | 0-40                      |            394            |                             5.4                              |                             8.3                              |
| 2           | 41-80                     |            461            |                             16.3                             |                             13.3                             |
| 3           | 81-120                    |            391            |                             24.3                             |                             15.1                             |
| 4           | 121-160                   |            334            |                             34.5                             |                             19.8                             |
| 5           | 161-200                   |            169            |                             42.1                             |                             24.5                             |
| 6           | 201-240                   |            113            |                             50.1                             |                             26.0                             |
| 7           | More than 240             |            148            |                             63.8                             |                             35.2                             |

Calculate the sampling variance of the estimated area under wheat for the region from a sample of 150 farms:

$(i)$ if the farms are selected by the method of srs without stratification.

$(ii)$ if the farms are selected by the method of srs within each stratum and allocated in proportion to $(a)$ the number of farms in each stratum $N_i$ , and $(b)$ the product $N_i S_i$ .

Also find the sample size of each stratum under $(a)$ and $(b)$. Also obtain the gain in efficiency resulting from the later two procedures of sampling as compared with unstratified simple random sampling.

**Aim:** To compute  the sampling variance of the estimated area under wheat for the region from a sample of 150 farms:

$(i)$ if the farms are selected by the method of srs without stratification.

$(ii)$ if the farms are selected by the method of srs within each stratum and allocated in proportion to:

​	 $(a)$ the number of farms in each stratum $N_i$ , and $(b)$ the product $N_i S_i$ .

Also find the sample size of each stratum under $(a)$ and $(b)$. Also obtain the gain in efficiency resulting from the later two procedures of sampling as compared with unstratified simple random sampling.

**Procedure:** If $Y_{ij}$ denote the area of the $j^{th}$ farm in the $i^{th}$ stratum,

then, Population mean is given by,

$$
\bar Y_N=\frac{\sum N_i \bar Y_{N_i}}{\sum{N_i}}
$$

and Population mean square error is given by,

$$
\begin{align*}
S^2 & =\frac{1}{N-1}\sum_i \sum_j (Y_{ij}-\bar Y_N )^2 \\
   & = \frac{1}{N-1}\bigg[\sum_i(N_i-1)S_i^2+\sum_iN_i \bar Y_{N_i}^2-N \bar Y_N^2\bigg]
\end{align*}
$$

Variance due to proportional allocation is given by,

$$
Var(\bar y_n)_R=\frac{N-n}{Nn}\times S^2
$$

Total estimated area under wheat is $\hat y=N\bar y_n$

$\therefore \ \ \ \ \ Var(\hat Y)=N^2 Var(\bar y_n)_R$  

Under proportional allocation   $n_i \propto N_i $

$\Rightarrow$            $n_i=\frac{n}{N}\times N_i$

Under Neyman's optimum Allocation $n_i \propto N_iS_i$   

$\Rightarrow$                $n_i=\frac{nN_iS_i}{\sum N_iS_i}$

Variance due to proportional allocation is given by,

$$
Var(\bar y_{st})_P=\bigg(\frac{1}{n}-\frac{1}{N}\bigg)\sum_ip_iS_i^2
$$

$\therefore$

$$
\begin{align*}
Var(\hat Y)_P & =N^2Var(\bar y_{st})_P \\
&=\frac{N-n}{n}\sum_i^kN_iS_i^2
\end{align*}
$$

Variance due to Neyman  allocation is given by,

$$
Var(\bar y_{st})_N=\frac{1}{nN^2}\bigg(\sum _iN_iS_i\bigg)^2-\frac{1}{N^2}\bigg(\sum N_iS_i^2\bigg
)
$$

$\therefore $ 

$$
Var(\hat Y)_{Ney}=N^2Var(\bar y_{st})_{Ney}=\frac{1}{n}\bigg(\sum_iN_iS_i^2 \bigg)^2-\sum_iN_iS_i^2
$$

Gain in Efficiency in stratification random sampling over simple random sampling without replacement:

$(a)$ Due to Proportional allocation is 

$$
\frac{Var(\bar y_n)_R-Var(\bar y_{st})_p}{Var(\bar y_{st})_{P}}
$$

$(b)$ Due to Neyman's optimum allocation is:

$$
\frac{Var(\bar y_n)_R-Var(\bar y_{st})_{Ney}}{Var(\bar y_{st})_N}
$$

**R-Code:** 

```R
rm(list=ls())
N=2010
n=150
N_i=c(394,461,391,334,169,113,148)
Y_bar_N_i=c(5.4,16.3,24.3,34.5,42.1,50.1,63.8)
S_i=c(8.3,13.3,15.1,19.8,24.5,26.0,35.2)
Y_bar_N=sum(N_i*Y_bar_N_i)/sum(N_i);Y_bar_N
S_sq=(1/(N-1))*(sum((N_i-1)*S_i*S_i)+sum(N_i*Y_bar_N_i*Y_bar_N_i)-N*Y_bar_N*Y_bar_N);S_sq
tab_cal=data.frame(S_No=c(1:7),N_i,Y_bar_N_i,
			 Y_bar_N_i_sq=Y_bar_N_i*Y_bar_N_i,
			N_i_Y_bar_N_i=N_i*Y_bar_N_i,
			N_i_Y_bar_N_i_Sq=N_i*Y_bar_N_i*Y_bar_N_i,S_i,
			S_i_sq=S_i*S_i,N_i_S_i=N_i*S_i,N_i_S_i_Sq=N_i*S_i*S_i,
			N_i_min_One_S_i_Sq=(N_i-1)*S_i*S_i)
tab_cal
Var_y_bar_n_R=round(((N-n)/(N*n)*S_sq),4);Var_y_bar_n_R
Var_Y_cap=N*N*Var_y_bar_n_R;Var_Y_cap
# Under Proportional allocation n_i is proportion to N_i
n_i_Prop=(n/N)*N_i
sum(n_i_Prop);
N_i_S_i=N_i*S_i
#Under Nayman Optimam n_i is proportional to N_i_S_i
n_i_Nayman=(n*N_i*S_i)/sum(N_i*S_i)
sum(n_i_Nayman);
Var_Y_hat_p=((N-n)/n)*sum(N_i*S_i*S_i);Var_Y_hat_p

Var_Y_hat_Ney=1/n*((sum(N_i*S_i))*(sum(N_i*S_i)))-sum(N_i*S_i*S_i);Var_Y_hat_Ney

Var_y_bar_st_P=Var_Y_hat_p/(N*N);Var_y_bar_st_P
Var_y_bar_st_Ney=Var_Y_hat_Ney/(N*N);Var_y_bar_st_Ney
Due_to_prop_allocat=(Var_y_bar_n_R-Var_y_bar_st_P)/Var_y_bar_st_P;Due_to_prop_allocat
Due_to_Ney_allocat=(Var_y_bar_n_R-Var_y_bar_st_Ney)/Var_y_bar_st_Ney;Due_to_Ney_allocat
if (Due_to_prop_allocat<Due_to_Ney_allocat) {
paste0("This implies that Neyman's optimum allocation provides better estimates as compared to proportional allocation ")
} else
{
paste0("This implies that proportional allocation provides better estimates as compared to  Neyman's optimum allocation ")
}
```

**R-Console(Output):** 

```R
> rm(list=ls())
> N=2010
> n=150
> N_i=c(394,461,391,334,169,113,148)
> Y_bar_N_i=c(5.4,16.3,24.3,34.5,42.1,50.1,63.8)
> S_i=c(8.3,13.3,15.1,19.8,24.5,26.0,35.2)
> Y_bar_N=sum(N_i*Y_bar_N_i)/sum(N_i);Y_bar_N
[1] 26.31085
> S_sq=(1/(N-1))*(sum((N_i-1)*S_i*S_i)+sum(N_i*Y_bar_N_i*Y_bar_N_i)-N*Y_bar_N*Y_bar_N);S_sq
[1] 618.7935
> tab_cal=data.frame(S_No=c(1:7),N_i,Y_bar_N_i,
+  Y_bar_N_i_sq=Y_bar_N_i*Y_bar_N_i,
+ N_i_Y_bar_N_i=N_i*Y_bar_N_i,
+ N_i_Y_bar_N_i_Sq=N_i*Y_bar_N_i*Y_bar_N_i,S_i,
+ S_i_sq=S_i*S_i,N_i_S_i=N_i*S_i,N_i_S_i_Sq=N_i*S_i*S_i,
+ N_i_min_One_S_i_Sq=(N_i-1)*S_i*S_i)
> tab_cal
  S_No N_i Y_bar_N_i Y_bar_N_i_sq N_i_Y_bar_N_i N_i_Y_bar_N_i_Sq  S_i  S_i_sq N_i_S_i N_i_S_i_Sq N_i_min_One_S_i_Sq
1    1 394       5.4        29.16        2127.6         11489.04  8.3   68.89  3270.2   27142.66           27073.77
2    2 461      16.3       265.69        7514.3        122483.09 13.3  176.89  6131.3   81546.29           81369.40
3    3 391      24.3       590.49        9501.3        230881.59 15.1  228.01  5904.1   89151.91           88923.90
4    4 334      34.5      1190.25       11523.0        397543.50 19.8  392.04  6613.2  130941.36          130549.32
5    5 169      42.1      1772.41        7114.9        299537.29 24.5  600.25  4140.5  101442.25          100842.00
6    6 113      50.1      2510.01        5661.3        283631.13 26.0  676.00  2938.0   76388.00           75712.00
7    7 148      63.8      4070.44        9442.4        602425.12 35.2 1239.04  5209.6  183377.92          182138.88
> Var_y_bar_n_R=round(((N-n)/(N*n)*S_sq),4);Var_y_bar_n_R
[1] 3.8174
> Var_Y_cap=N*N*Var_y_bar_n_R;Var_Y_cap
[1] 15422678
> # Under Proportional allocation n_i is proportion to N_i
> n_i_Prop=(n/N)*N_i
> sum(n_i_Prop);
[1] 150
> N_i_S_i=N_i*S_i
> #Under Nayman Optimam n_i is proportional to N_i_S_i
> n_i_Nayman=(n*N_i*S_i)/sum(N_i*S_i)
> sum(n_i_Nayman);
[1] 150
> Var_Y_hat_p=((N-n)/n)*sum(N_i*S_i*S_i);Var_Y_hat_p
[1] 8555881
> 
> Var_Y_hat_Ney=1/n*((sum(N_i*S_i))*(sum(N_i*S_i)))-sum(N_i*S_i*S_i);Var_Y_hat_Ney
[1] 7110756
> 
> Var_y_bar_st_P=Var_Y_hat_p/(N*N);Var_y_bar_st_P
[1] 2.11774
> Var_y_bar_st_Ney=Var_Y_hat_Ney/(N*N);Var_y_bar_st_Ney
[1] 1.760045
> Due_to_prop_allocat=(Var_y_bar_n_R-Var_y_bar_st_P)/Var_y_bar_st_P;Due_to_prop_allocat
[1] 0.8025821
> Due_to_Ney_allocat=(Var_y_bar_n_R-Var_y_bar_st_Ney)/Var_y_bar_st_Ney;Due_to_Ney_allocat
[1] 1.168922
> if (Due_to_prop_allocat<Due_to_Ney_allocat) {
+ paste0("This implies that Neyman's optimum allocation provides better estimates as compared to proportional allocation ")
+ } else
+ {
+ paste0("This implies that proportional allocation provides better estimates as compared to  Neyman's optimum allocation ")
+ }
[1] "This implies that Neyman's optimum allocation provides better estimates as compared to proportional allocation "
```

**Conclusion:**  From the above experiment we conclude that,
$\displaystyle Var(\hat Y)_R=15422678$ , 

$\displaystyle Var(\hat Y)_P=8555881$  and  

$Var(\hat Y)_{Ney}=7110756$. 
Also observed that Neyman's optimum allocation provides better estimates as compared to proportional allocation.
