# Practical #17 #

##### Practical Topic: SQC

**Experiment:**  From a lot consisting of 2,200 items, a sample of size 225 is taken. If it contains 14 or less defectives, the lot is accepted otherwise rejected. Plot the OC,ATI and AOQ curves. Also obtain the value of AOQL.

**Aim:** To plot OC,ATI and AOQ curve. Also to find the value of AOQL.

**Procedure:** Using Poisson approximation to hyper-geometric distribution, the OC curve, i.e., the probability of acceptance L(p) or $P_a$  is given by;
$$
P_a=\sum_{x=0}^c\frac{e^{-np}(np)^x}{x!}=\sum_{x=0}^c\frac{e^{-\lambda}\lambda^x}{x!}
$$
$\displaystyle ATI=n+(N-n)(1-P_a)\; \;and\;AOQ=p.P_a$ .

**R-code**

```R
N<- 2200;n<-225;c=14
p<-c(0.01,0.02,0.03,0.04,0.05,0.06,0.08,0.10,0.30,0.80)
lembda<-n*p
P_a=round(ppois(c,lembda),5)

plot(p[c(-9:-10)],P_a[c(-9:-10)],type = "l",main="The OC Curve of Single Sampling Plan",xlab="p",ylab="L(p)=Pa(p)")

ATI<-round((n+(N-n)*(1-P_a)),3)
plot(p[-10],ATI[-10],type = "o",main="The ATI Curve",xlab="p",ylab="ATI")

AOQ<-p*P_a
AOQL=max(AOQ);AOQL
plot(p[-10],AOQ[-10],type = "o" ,main = "The AOQ Curve",xlab="p",ylab="A.O.Q.")

#Computing ATI and AOQ Values
ATI_AOQ_table=data.frame(p,lembda,P_a,AOQ,ATI)
ATI_AOQ_table
```

**R-Output:**

```R
> N<- 2200;n<-225;c=14
> p<-c(0.01,0.02,0.03,0.04,0.05,0.06,0.08,0.10,0.30,0.80)
> lembda<-n*p
> P_a=round(ppois(c,lembda),5)
> 
> plot(p[c(-9:-10)],P_a[c(-9:-10)],type = "l",main="The OC Curve of Single Sampling Plan",xlab="p",ylab="L(p)=Pa(p)")
> 
> ATI<-round((n+(N-n)*(1-P_a)),3)
> plot(p[-10],ATI[-10],type = "o",main="The ATI Curve",xlab="p",ylab="ATI")
> 
> AOQ<-p*P_a
> AOQL=max(AOQ);AOQL
[1] 0.041762
> plot(p[-10],AOQ[-10],type = "o" ,main = "The AOQ Curve",xlab="p",ylab="A.O.Q.")
> 
> #Computing ATI and AOQ Values
> ATI_AOQ_table=data.frame(p,lembda,P_a,AOQ,ATI)
> ATI_AOQ_table
      p lembda     P_a       AOQ      ATI
1  0.01   2.25 1.00000 0.0100000  225.000
2  0.02   4.50 0.99993 0.0199986  225.138
3  0.03   6.75 0.99585 0.0298755  233.196
4  0.04   9.00 0.95853 0.0383412  306.903
5  0.05  11.25 0.83524 0.0417620  550.401
6  0.06  13.50 0.62327 0.0373962  969.042
7  0.08  18.00 0.20808 0.0166464 1789.042
8  0.10  22.50 0.03860 0.0038600 2123.765
9  0.30  67.50 0.00000 0.0000000 2200.000
10 0.80 180.00 0.00000 0.0000000 2200.000
```

**R-Graphics:**

![image-20220922002436322](https://raw.githubusercontent.com/ydvpratik/img/master/2022/09/upgit_20220922_1663786479.png)

![image-20220922002522204](https://raw.githubusercontent.com/ydvpratik/img/master/2022/09/upgit_20220922_1663786525.png)

![image-20220922002618436](https://raw.githubusercontent.com/ydvpratik/img/master/2022/09/upgit_20220922_1663786580.png)

**Conclusion:** From the above experiment we compute AOQL value, which is maximum of AOQ i.e. 0.041762. 