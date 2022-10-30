# Practical #22

##### Practical Topic : Analysis of Variance for $2^2$ - Experiment

**Experiment:** An experiment was planned to study the effect of sulphate of potash and super phosphate on the yield of potatoes. All the combinations of 2 levels of super phosphate [0 cent $(p_0)$ and 5 cent $(p_1/acre)$] and two levels of sulphate of potash [o cent $(k_0)$ and 5 cent $(k_1/acre)$ ]   were studied in a randomized block design with 4 replications for each. The $(1/70)$ yields [ lb. per plot = $(1/70)$ ] acre obtained are given in below table.

<table>
    <tr class="ab">
        <td style="text-align:center" class="ab">Block </td>
        <td style="text-align:center" colspan="4">Yeilds (lbs per plot)</td>
    </tr>
    <tr>
        <td style="text-align:center" rowspan="2" class="ab">I</td>
        <td style="text-align:center">(1)</td>
        <td style="text-align:center">k</td>
        <td style="text-align:center">p</td>
        <td style="text-align:center">kp</td>
    </tr>
    <tr>
        <td style="text-align:center">23</td>
        <td style="text-align:center">25</td>
        <td style="text-align:center">22</td>
        <td style="text-align:center">38</td>     
    </tr>
    <tr>
        <td style="text-align:center" rowspan="2" class="ab">II</td>
        <td style="text-align:center">p</td>
        <td style="text-align:center">(1)</td>
        <td style="text-align:center">k</td>
        <td style="text-align:center">kp</td>
    </tr>
    <tr><td style="text-align:center">40</td>
        <td style="text-align:center">26</td>
        <td style="text-align:center">36</td>
        <td style="text-align:center">38</td>
    </tr>   
    <tr>
        <td style="text-align:center" rowspan="2" class="ab">III</td>
        <td style="text-align:center">(1)</td>
        <td style="text-align:center">k</td>
        <td style="text-align:center">pk</td>
        <td style="text-align:center">p</td>
    </tr>
    <tr>
        <td style="text-align:center">29</td>
        <td style="text-align:center">20</td>
        <td style="text-align:center">30</td>
        <td style="text-align:center">20</td>   
    </tr>
    <tr> 
        <td style="text-align:center" rowspan="2" class="ab">IV</td>
        <td style="text-align:center">kp</td>
        <td style="text-align:center">k</td>
        <td style="text-align:center">kp</td>
        <td style="text-align:center">(1)</td>  
    </tr>
    <tr>
       <td style="text-align:center">34</td>
       <td style="text-align:center">31</td>
       <td style="text-align:center">24</td>
       <td style="text-align:center">28</td>   
    </tr>
</table>

  Analyse the data and give your conclusions.

**Aim:** To study the effect of sulphate of potash and super phosphate on the yield of potatoes . 

**Procedure:** $\displaystyle R.S.S=\sum_i\sum_j{y_{ij}}^2$ ;   Correction Factor = $\displaystyle \frac{Total}{N}$ ; M.S.S = $\displaystyle\frac{S.S}{d.f}$ 

Total S.S =  $\displaystyle RSS-C.F.$  ;   Block S.S= $\displaystyle \frac{1}{n}\sum_iB_j^2-C.F$  ;  Treatment S.S = $\displaystyle \frac{1}{n}\sum_iT_i^2-C.F$ ;  

Error S.S= $\displaystyle Total\,S.S-(Block ~~ S.S+Treatment ~~ S.S)$ 

YATES' Method for $2^2$ - Experiment:

| Treatment <br />       Combination<br />(1) | Total Yield from<br />all replicates<br />(2) |   (3)    |       (4)        | Effect<br />Totals |
| :-----------------------------------------: | :-------------------------------------------: | :------: | :--------------: | :----------------: |
|                     '1'                     |                      [1]                      | [1]+[a]  | [1]+[a]+[b]+[ab] |    Grand Total     |
|                      a                      |                      [a]                      | [b]+[ab] | [ab]-[b]+[a]-[1] |        [A]         |
|                      b                      |                      [b]                      | [a]-[1]  | [ab]+[b]-[a]-[1] |        [B]         |
|                     ab                      |                     [ab]                      | [ab]-[b] | [ab]-[b]-[a]+[1] |        [AB]        |

**R-Code:** 

```R
I <- c(23,26,29,28)
k <- c(25,36,20,31)
p <- c(22,40,20,24)
kp <- c(38,38,30,34)
Mat <- rbind( I,k,p,kp)
Ti <- rowSums(Mat)
Bj <- colSums(Mat)
G <- sum(Ti)
RSS <- sum(as.vector(Mat)^2)
CF <- G^2/16
TSS <- RSS -CF
BSS <- sum(Bj^2)/4-CF
SST <- sum(Ti^2)/4-CF
ESS <- TSS-BSS-SST
TSS
BSS
SST
ESS

#Yates' method for 2^2 experiment 
T.3=c(Ti[1]+Ti[2],Ti[3]+Ti[4],-Ti[1]+Ti[2],-Ti[3]+Ti[4])
T.4=c(T.3[1]+T.3[2],T.3[3]+T.3[4],-T.3[1]+T.3[2],-T.3[3]+T.3[4])
SS=T.4^2/16

table.yates <- cbind(Ti,T.3,T.4,SS)
colnames(table.yates)=c("Total Yeilds (2)","(3)","Factorial Effect Total(4)","SS")
table.yates
r=4
df=c(r-1,r-1,1,1,1,3*(r-1),4*(r-1))
S.S.=c(BSS,SST,SS[-1],ESS,TSS)
M.S.S=S.S./df
M.S.S[7]=NA
Var_Ratio=c(M.S.S[1:5]/M.S.S[6],NA,NA)
Tab_F_5=c(qf(0.95,df[1:5],rep(df[6],5)),NA,NA)
Tab_F_1=c(qf(0.99,df[1:5],rep(df[6],5)),NA,NA)
anova.yates=cbind(df,S.S.,M.S.S,Var_Ratio,Tab_F_5,Tab_F_1)
rownames(anova.yates)=c("Block","Treatments","k","p","kp","Errors","Total")
anova.yates
```

**R-console(Output):**

```R
> I <- c(23,26,29,28)
> k <- c(25,36,20,31)
> p <- c(22,40,20,24)
> kp <- c(38,38,30,34)
> Mat <- rbind( I,k,p,kp)
> Ti <- rowSums(Mat)
> Bj <- colSums(Mat)
> G <- sum(Ti)
> RSS <- sum(as.vector(Mat)^2)
> CF <- G^2/16
> TSS <- RSS -CF
> BSS <- sum(Bj^2)/4-CF
> SST <- sum(Ti^2)/4-CF
> ESS <- TSS-BSS-SST
> TSS
[1] 660
> BSS
[1] 232.5
> SST
[1] 198
> ESS
[1] 229.5
> 
> #Yates' method for 2^2 experiment 
> T.3=c(Ti[1]+Ti[2],Ti[3]+Ti[4],-Ti[1]+Ti[2],-Ti[3]+Ti[4])
> T.4=c(T.3[1]+T.3[2],T.3[3]+T.3[4],-T.3[1]+T.3[2],-T.3[3]+T.3[4])
> SS=T.4^2/16
> 
> table.yates <- cbind(Ti,T.3,T.4,SS)
> colnames(table.yates)=c("Total Yeilds (2)","(3)","Factorial Effect Total(4)","SS")
> table.yates
   Total Yeilds (2) (3) Factorial Effect Total(4)    SS
I               106 218                       464 13456
k               112 246                        40   100
p               106   6                        28    49
kp              140  34                        28    49
> r=4
> df=c(r-1,r-1,1,1,1,3*(r-1),4*(r-1))
> S.S.=c(BSS,SST,SS[-1],ESS,TSS)
> M.S.S=S.S./df
> M.S.S[7]=NA
> Var_Ratio=c(M.S.S[1:5]/M.S.S[6],NA,NA)
> Tab_F_5=c(qf(0.95,df[1:5],rep(df[6],5)),NA,NA)
> Tab_F_1=c(qf(0.99,df[1:5],rep(df[6],5)),NA,NA)
> anova.yates=cbind(df,S.S.,M.S.S,Var_Ratio,Tab_F_5,Tab_F_1)
> rownames(anova.yates)=c("Block","Treatments","k","p","kp","Errors","Total")
> anova.yates
           df  S.S. M.S.S Var_Ratio  Tab_F_5   Tab_F_1
Block       3 232.5  77.5  3.039216 3.862548  6.991917
Treatments  3 198.0  66.0  2.588235 3.862548  6.991917
k           1 100.0 100.0  3.921569 5.117355 10.561431
p           1  49.0  49.0  1.921569 5.117355 10.561431
kp          1  49.0  49.0  1.921569 5.117355 10.561431
Errors      9 229.5  25.5        NA       NA        NA
Total      12 660.0    NA        NA       NA        NA
```

**Conclusion:** From the above data we conclude that,as in each of the cases the computed value of F is less than the corresponding tabulated value, there are no significant main or interaction effects present in the experiment. Since the block do not differ significantly, there is no special contribution from fluctuations in soil fertility and thus the division of the whole experimental area into blocks does not result in any gain accuracy. 
