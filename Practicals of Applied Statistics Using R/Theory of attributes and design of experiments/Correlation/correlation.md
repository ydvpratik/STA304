# Practical #25

##### Practical Topic: Correlation

**Experiment:** Five hundred students were examination in three subjects $I,II \ and \ III$, each subject carrying 100 marks. A student getting 120 or more but less than 150 marks was put in pass class. A student getting 150 or more but less than 180 marks was put in second class and a student getting 180 or more marks was put in the first class. The following marks were obtained:

|              | $I$          | $II$         | $III$        |
| ------------ | ------------ | ------------ | ------------ |
| Means:       | $35.8$       | $52.4$       | $48.8$       |
| S.D.:        | $4.2$        | $5.3$        | $6.1$        |
| Correlation: | $r_{12}=0.6$ | $r_{13}=0.7$ | $r_{23}=0.8$ |

Assuming that the marks are normally distributed,

​	$(i)$ Find the number of students in each of the three classes.

​	$(ii)$ Find the total number of students with total marks lying between 120 and 190.

​	$(iii)$ Find the probability that a students gets more than 240 marks.

​	$(iv)$ What should be the correlation between marks in subjects I and II among students who scored equal marks in subject III ?

​	$(v)$ If $r_{23}$ was not known, obtain the limits within which it may lie from the values of $r_{12}$ and $r_{13}$ (ignoring sampling error)

**Aim:** To ;

​	$(i)$ Find the number of students in each of the three classes.

​	$(ii)$ Find the total number of students with total marks lying between 120 and 190.

​	$(iii)$ Find the probability that a students gets more than 240 marks.

​	$(iv)$ What should be the correlation between marks in subjects I and II among students who scored equal marks in subject III ?

​	$(v)$ If $r_{23}$ was not known, obtain the limits within which it may lie from the values of $r_{12}$ and $r_{13}$ 

**Procedure:** If $Z=X_1+X_2+X_3$   $\Rightarrow$    $E(Z)=E(X_1)+E(X_2)+E(X_3)$ 

$V(Z)=V(X_1)+V(X_2)+V(X_3)+2[Cov(X_1,X_2)+Cov(X_2,X_3)+Cov(X_3,X_1)]$

​                         $[using \ Cov(X_i,X_j)=r_{ij}\sigma_i\sigma_J]$

$\displaystyle\xi=\frac{Z-E[z]}{\sigma_z}\textasciitilde N(0,1)$



**R-Code:** 

```R
rm(list=ls())
T=500
Z=c(120,150,180,190,240)
Mean=c(35.8,52.4,48.8)
SD=c(4.2,5.3,6.1)
Correlation=c(0.6,0.7,0.8)
var_z=sum(SD*SD)+2*(Correlation[1]*SD[1]*SD[2]+Correlation[2]*SD[1]*SD[3]+Correlation[3]*SD[3]*SD[2])
var_z
sigma_z=sqrt(var_z)
sigma_z
Xi=round(((Z-sum(Mean))/sigma_z),5);Xi
p=pnorm(Xi,0,1);p
area_under_curve=c(p[2]-p[1],p[3]-p[2],1-p[3],p[4]-p[1],1-p[5])
round(area_under_curve,5)
Frequency=round((T*area_under_curve),4)
class=c("120-150","150-180","180 and above","120-190","240 and over")
Cal_table=data.frame(Z,Xi,p,class,area_under_curve=round(area_under_curve,5),Frequency);Cal_table
r12.3=(Correlation[1]-Correlation[2]*Correlation[3])/(sqrt((1-Correlation[2]^2)*(1-Correlation[3]^2)));r12.3
r.23_limits=polyroot(c(-0.15,-0.84,1));Re(round(r.23_limits,2))
```

**R-Console(output):** 

```R
> rm(list=ls())
> T=500
> Z=c(120,150,180,190,240)
> Mean=c(35.8,52.4,48.8)
> SD=c(4.2,5.3,6.1)
> Correlation=c(0.6,0.7,0.8)
> var_z=sum(SD*SD)+2*(Correlation[1]*SD[1]*SD[2]+Correlation[2]*SD[1]*SD[3]+Correlation[3]*SD[3]*SD[2])
> var_z
[1] 197.248
> sigma_z=sqrt(var_z)
> sigma_z
[1] 14.0445
> Xi=round(((Z-sum(Mean))/sigma_z),5);Xi
[1] -1.21044  0.92563  3.06170  3.77372  7.33383
> p=pnorm(Xi,0,1);p
[1] 0.1130551 0.8226809 0.9988996 0.9999196 1.0000000
> area_under_curve=c(p[2]-p[1],p[3]-p[2],1-p[3],p[4]-p[1],1-p[5])
> round(area_under_curve,5)
[1] 0.70963 0.17622 0.00110 0.88686 0.00000
> Frequency=round((T*area_under_curve),4)
> class=c("120-150","150-180","180 and above","120-190","240 and over")
> Cal_table=data.frame(Z,Xi,p,class,area_under_curve=round(area_under_curve,5),Frequency);Cal_table
    Z       Xi         p         class area_under_curve Frequency
1 120 -1.21044 0.1130551       120-150          0.70963  354.8129
2 150  0.92563 0.8226809       150-180          0.17622   88.1094
3 180  3.06170 0.9988996 180 and above          0.00110    0.5502
4 190  3.77372 0.9999196       120-190          0.88686  443.4323
5 240  7.33383 1.0000000  240 and over          0.00000    0.0000
> r12.3=(Correlation[1]-Correlation[2]*Correlation[3])/(sqrt((1-Correlation[2]^2)*(1-Correlation[3]^2)));r12.3
[1] 0.09335201
> r.23_limits=polyroot(c(-0.15,-0.84,1));Re(round(r.23_limits,2))
[1] -0.15  0.99
```

**Conclusion:** From the above experiment we conclude that:

(i)  The number of students in pass, second and first class respectively are 355, 88 and 0 (appx.)

(ii)  Total No. of students with total marks between 120 and 190 is 443.

(iii)  Probability that a student gets more than 240 marks is 0.

(iv)  The correlation coefficient between marks in subject I and II of the students who secured equal marks in subject III is $r_{12.3}=$ 0.09335201

(v) The limits in which $r_{23}$  should lie, when $r_{23}$ values is unknown, is  -0.15  and   0.99

