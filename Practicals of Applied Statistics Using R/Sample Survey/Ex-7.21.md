# Practical #18 

##### Practical Topic: Systematic Sampling 

**Experiment:** The data given in below table are for small artificial population which exhibits a fairly steady rising trend. Each column represents a systematic sample and the rows are the strata. Compare the precision of  systematic sampling, random sampling and stratified sampling.

​	Data for 10 systematic samples with $n=4,k=10,N=nk=40$ .

| Strata | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   |
| ------ | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| $I$    | 0    | 1    | 1    | 2    | 5    | 4    | 7    | 7    | 8    | 6    |
| $II$   | 6    | 8    | 9    | 10   | 13   | 12   | 15   | 16   | 16   | 17   |
| $III$  | 18   | 19   | 20   | 20   | 24   | 23   | 25   | 28   | 29   | 27   |
| $IV$   | 26   | 30   | 31   | 31   | 33   | 32   | 35   | 37   | 38   | 38   |



**Aim:** To compare  the precision of  systematic sampling, random sampling and stratified sampling from above data.

**Procedure:** 

$$
\begin{align*}
Var(y_{sys}) &=\frac{1}{k}\sum_{i=1}^{k}(\bar y_{i.}-\bar y_{..})^2=\frac{1}{k}
\bigg[\sum_{i=1}^k(n\bar y_{i.})^2-n^2k\bar y^2\bigg] \\
&=\frac{1}{n^2k}\bigg[\sum_{i=1}^k(n\bar y_{i.})^2-n^2k\bar {y_{..}}^2\bigg]
\end{align*}
$$

$$
Var(\bar y_{st})^2=\frac{k-1}{nk}\times {S_{swt}}^2
$$

where $\displaystyle {S_{wst}}^2=\frac{1}{n(k-1)}\sum_i\sum_j(y_{ij}-\bar y_{i.})^2$ is the within (stratum) mean sum of squares.

$$
Var(\bar y_n)_R=\bigg(\frac{1}{n}-\frac{1}{N}\bigg)S^2
$$

Where $S^2=\frac{1}{N-1}\displaystyle\sum_i\sum_j(y_{ij}-\bar y_{..})^2$ is the total mean S.S

Total S.S = $\displaystyle\sum \sum {y_{ij}}^2-Correction \ factor$

Between Strata S.S= $\displaystyle\sum_{j=1}^n\frac{{T_{.j}}^2}{k}-C.F.$

Within Strata S.S= Total S.S - Between Strata S.S

$\displaystyle{S_{wst}}^2=\frac{Within \ Strata \ S.S}{n(k-1)}$

$\displaystyle S^2=\frac{Total \ S.S}{N-1} $



**R-Code:**  

```R
rm(list=ls())
n=4
k=10
N=40
X_1=c(0,1,1,2,5,4,7,7,8,6)
X_2=c(6,8,9,10,13,12,15,16,16,17)
X_3=c(18,19,20,20,24,23,25,28,29,27)
X_4=c(26,30,31,31,33,32,35,37,38,38)
T_dot_j=c(sum(X_1),sum(X_2),sum(X_3),sum(X_4))
sum_of_rows_colm_sq=sum(X_1*X_1)+sum(X_2*X_2)+sum(X_3*X_3)+sum(X_4*X_4)
Correcn_factor=(sum(T_dot_j))^2/N ;Correcn_factor
Total_SS=sum_of_rows_colm_sq-Correcn_factor;Total_SS
Btbn_Strata_SS=sum(T_dot_j^2)/10-Correcn_factor;Btbn_Strata_SS
within_strata_ss = Total_SS - Btbn_Strata_SS;within_strata_ss
S_wst_sq = (within_strata_ss)/((k-1)*n);S_wst_sq
S_sq = Total_SS / (N-1);S_sq
Anova_table=data.frame(Source_of_variation=c("Between Strata","Within Strata","Total"),
                       df=c(n-1,n*(k-1),N-1),
                       SS=c(Btbn_Strata_SS,within_strata_ss,within_strata_ss+Btbn_Strata_SS),
                       MSS=c((rep((within_strata_ss)/((k-1)*n),2)),Total_SS /(N-1)));Anova_table
n_y_bar_i_dot=X_1+X_2+X_3+X_4
sq_n_y_bar_i_dot=n_y_bar_i_dot*n_y_bar_i_dot
sum_sq_n_y_bar_i_dot=sum(sq_n_y_bar_i_dot)
Var_y_bar_sys=(1/(N*n))*(sum_sq_n_y_bar_i_dot-(N*n)*(sum(T_dot_j)/N)^2);Var_y_bar_sys
Var_y_bar_st=(1/n-1/N)*S_wst_sq;Var_y_bar_st
Var_y_bar_n_R=(1/n-1/N)*S_sq;Var_y_bar_n_R
l=c(Var_y_bar_sys,Var_y_bar_st,Var_y_bar_n_R)
names(l)=c("Systematic","Stratified","Random Sampaling")
order=names(sort(l))
paste0("We observe that variance of ",order[1],"<",order[2],"<",order[3])
```

**R-Console(Output):** 

```R
> rm(list=ls())
> n=4
> k=10
> N=40
> X_1=c(0,1,1,2,5,4,7,7,8,6)
> X_2=c(6,8,9,10,13,12,15,16,16,17)
> X_3=c(18,19,20,20,24,23,25,28,29,27)
> X_4=c(26,30,31,31,33,32,35,37,38,38)
> T_dot_j=c(sum(X_1),sum(X_2),sum(X_3),sum(X_4))
> sum_of_rows_colm_sq=sum(X_1*X_1)+sum(X_2*X_2)+sum(X_3*X_3)+sum(X_4*X_4)
> Correcn_factor=(sum(T_dot_j))^2/N ;Correcn_factor
[1] 13213.23
> Total_SS=sum_of_rows_colm_sq-Correcn_factor;Total_SS
[1] 5313.775
> Btbn_Strata_SS=sum(T_dot_j^2)/10-Correcn_factor;Btbn_Strata_SS
[1] 4828.275
> within_strata_ss = Total_SS - Btbn_Strata_SS;within_strata_ss
[1] 485.5
> S_wst_sq = (within_strata_ss)/((k-1)*n);S_wst_sq
[1] 13.48611
> S_sq = Total_SS / (N-1);S_sq
[1] 136.2506
> Anova_table=data.frame(Source_of_variation=c("Between Strata","Within Strata","Total"),
+                        df=c(n-1,n*(k-1),N-1),
+                        SS=c(Btbn_Strata_SS,within_strata_ss,within_strata_ss+Btbn_Strata_SS),
+                        MSS=c((rep((within_strata_ss)/((k-1)*n),2)),Total_SS /(N-1)));Anova_table
  Source_of_variation df       SS       MSS
1      Between Strata  3 4828.275  13.48611
2       Within Strata 36  485.500  13.48611
3               Total 39 5313.775 136.25064
> n_y_bar_i_dot=X_1+X_2+X_3+X_4
> sq_n_y_bar_i_dot=n_y_bar_i_dot*n_y_bar_i_dot
> sum_sq_n_y_bar_i_dot=sum(sq_n_y_bar_i_dot)
> Var_y_bar_sys=(1/(N*n))*(sum_sq_n_y_bar_i_dot-(N*n)*(sum(T_dot_j)/N)^2);Var_y_bar_sys
[1] 11.62562
> Var_y_bar_st=(1/n-1/N)*S_wst_sq;Var_y_bar_st
[1] 3.034375
> Var_y_bar_n_R=(1/n-1/N)*S_sq;Var_y_bar_n_R
[1] 30.65639
> l=c(Var_y_bar_sys,Var_y_bar_st,Var_y_bar_n_R)
> names(l)=c("Systematic","Stratified","Random Sampaling")
> order=names(sort(l))
> paste0("We observe that variance of ",order[1],"<",order[2],"<",order[3])
[1] "We observe that variance of Stratified<Systematic<Random Sampaling"
```

**Conclusion:** From the above experiment we conclude that,

$\displaystyle Var(\bar y_{st}) < Var(\bar y_{sys}) < Var(\bar y_{n})_R$ .

 
