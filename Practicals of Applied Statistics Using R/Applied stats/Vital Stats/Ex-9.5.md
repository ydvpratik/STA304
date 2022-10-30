# Practical #5

##### Practical Title: Life Table

**Experiment:** Given the following table for $l_x$, the number of rabbits living at age $x$ complete the life table for rabbits.

|  $x...$  |  0   |  1   |  2   |  3   |  4   |  5   |  6   |
| :------: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| $l_x...$ | 100  |  90  |  80  |  75  |  60  |  30  |  0   |

$X,Y,Z$ are three rabbits of age 1,2 and 3 years respectively. Find the probability that:

$(i)$ at least one of rabbit will be alive for one year more,

$(ii)$ X,Y,Z will be alive for two years time,

(iii) exactly one of the three is alive in two years, and

(iv) all will be dead in two years time.



**AIM:** To find probability that,

$(i)$ at least one of rabbit  will be alive for one year more,

$(ii)$ $X,Y,Z$ will be alive for two years time,

$(iii)$ exactly one of the three is alive in two years, and

$(iv)$ all will be dead in two years time.



**Procedure:**

Probability of death in next $d$ years of life aged x is given by $({l_x-l_{(x+d)}})/l_x$

For life aged $x$ probability of survival of $d$ more years will be given by $l_{(x+d)}/l_x$

For of Survival of at least one, probability will be $(1-p(survival\ of\ none))$ 

For two independent event with probability p and q respectively, the probability will be given by $pq$.



**R-Code:**

```r
#Given rabbit X,Y,Z aged 1,2,3 respectively 
rm(list=ls())
x=c(0:6)
lx<-c(100,90,80,75,60,30,0)
dx<- lx[-7]-lx[-1]
qx<- dx/lx[-7]
#I) Probability that one won't survive to next year is given by qx 
P_none=qx[2]*qx[3]*qx[4]#Proability that none of X,Y,Z Survive to next year
P_none
P_atleastone=1-P_none; P_atleastone # Probability that atleast one survive next year

#II) 2year time 
P_s=lx[4:6]/lx[2:4]
P_all_Survive=P_s[1]*P_s[2]*P_s[3];P_all_Survive

#III) 
P_alive_onlyone=P_s[1]*(1-P_s[2])*(1-P_s[3])+P_s[2]*(1-P_s[1])*(1-P_s[3])+P_s[3]*(1-P_s[2])*(1-P_s[1])
P_alive_onlyone
#IV)
P_alldead=(1-P_s[1])*(1-P_s[2])*(1-P_s[3]);P_alldead
Lx=(lx[-7]+lx[-1])/2
Tx=c()
for(i in 1:6) {
  Tx[i]=sum(Lx[i:6])
}
Tx
e_x_not=Tx/lx[1:6]
Life_Table=data.frame(Age_x=x,lx,dx=c(dx,rep(NA,length(lx)-length(dx))),
                      qx=c(round(qx,2),rep(NA,length(lx)-length(qx))),
                      Lx=c(Lx,rep(NA,length(lx)-length(Lx))),
                      Tx=c(Tx,rep(NA,length(lx)-length(Tx))),
                      e_x_not=c(round(e_x_not,2),rep(NA,length(lx)-length(e_x_not))))
Life_Table

```



**R-Console:**

```R
> #Given rabbit X,Y,Z aged 1,2,3 respectively 
> rm(list=ls())
> x=c(0:6)
> lx<-c(100,90,80,75,60,30,0)
> dx<- lx[-7]-lx[-1]
> qx<- dx/lx[-7]
> #I) Probability that one won't survive to next year is given by qx 
> P_none=qx[2]*qx[3]*qx[4]#Proability that none of X,Y,Z Survive to next year
> P_none
[1] 0.001388889
> P_atleastone=1-P_none; P_atleastone # Probability that atleast one survive next year
[1] 0.9986111
> 
> #II) 2year time 
> P_s=lx[4:6]/lx[2:4]
> P_all_Survive=P_s[1]*P_s[2]*P_s[3];P_all_Survive
[1] 0.25
> 
> #III) 
> P_alive_onlyone=P_s[1]*(1-P_s[2])*(1-P_s[3])+P_s[2]*(1-P_s[1])*(1-P_s[3])+P_s[3]*(1-P_s[2])*(1-P_s[1])
> P_alive_onlyone
[1] 0.2166667
> #IV)
> P_alldead=(1-P_s[1])*(1-P_s[2])*(1-P_s[3]);P_alldead
[1] 0.025
> Lx=(lx[-7]+lx[-1])/2
> Tx=c()
> for(i in 1:6) {
+   Tx[i]=sum(Lx[i:6])
+ }
> Tx
[1] 385.0 290.0 205.0 127.5  60.0  15.0
> e_x_not=Tx/lx[1:6]
> Life_Table=data.frame(Age_x=x,lx,dx=c(dx,rep(NA,length(lx)-length(dx))),
+                       qx=c(round(qx,2),rep(NA,length(lx)-length(qx))),
+                       Lx=c(Lx,rep(NA,length(lx)-length(Lx))),
+                       Tx=c(Tx,rep(NA,length(lx)-length(Tx))),
+                       e_x_not=c(round(e_x_not,2),rep(NA,length(lx)-length(e_x_not))))
> Life_Table
  Age_x  lx dx   qx   Lx    Tx e_x_not
1     0 100 10 0.10 95.0 385.0    3.85
2     1  90 10 0.11 85.0 290.0    3.22
3     2  80  5 0.06 77.5 205.0    2.56
4     3  75 15 0.20 67.5 127.5    1.70
5     4  60 30 0.50 45.0  60.0    1.00
6     5  30 30 1.00 15.0  15.0    0.50
7     6   0 NA   NA   NA    NA      NA
```

**Conclusion:**

The probability that, at least one of rabbit will be alive for one year more $=0.9986111$ ,

 $X,Y,Z$ will be alive for two years time $=0.25$ ,

Exactly one of the three is alive in two years $=0.2166667$ and

All will be dead in two years time $=0.025$. 

