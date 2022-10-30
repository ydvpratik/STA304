# Practical #21

##### Practical Topic: Simple Random Sampling 

**Experiment:** Consider a population of 6 units with values 1,2,3,4,5,6. Write down all possible samples of 2 (without replacement) from this population and verify that sample mean is an unbiased estimate of the population mean. Also calculate its sampling variance and verify that-

​	$(i)$ it agree with the formula for the variance of the sample mean, and

​	$(ii)$ this variance is less than the variance obtained from sampling with replacement.

**Aim:** To write all the possible sample of 2 using SRSWOR and verify that sample mean is an unbiased estimator of population mean  

**Processor:** 

Population mean $\displaystyle \bar Y=\frac{1}{N}\sum Y$

Population mean square error, $\displaystyle S^2=\frac{1}{N-1}\sum (Y-\bar Y)^2=\frac{1}{N-1}\left[\sum Y^2-N\bar Y^2\right]$ 

Population Variance, $\displaystyle \sigma^2=\frac{N-1}{N}S^2$

 Expected value of sample mean , $\displaystyle E[\bar Y]=\left[{\sum_{i=1}\bar y_i}/{^NC_n}\right]$ 

In SRSWOR, the variance is given by the formula: $\displaystyle Var(\bar y)=\frac{N-n}{Nn}S^2$  

in SRSWR, Variance is given by $\displaystyle Var(\bar y)\ in \ srswr= \frac{\sigma^2}{n}$

**R-Code:** 

```R
rm(list=ls())
N=6
n=2
Y=c(1:6)
x=c()
y=c()
count <- 0
for(i in 1:5)
{
  for( j in (i+1):6)
  {
    
    count <- count+1
    x[count]=i
    y[count]=j
  }
}
mean.sample=(x+y)/2
Y_sq=Y*Y
Y_bar=mean(Y);Y_bar
S_sq=var(Y);S_sq
Sigma_sq=((N-1)/N)*S_sq;Sigma_sq
sample=data.frame(sample.x=x,sample.y=y,mean.sample);sample
y_bar=mean.sample
Exp_y_bar=mean(y_bar);Exp_y_bar
if(Y_bar==Exp_y_bar) {
  paste0("Sample mean is an unbiased estimator of the population mean")
} else
{
  paste0("Sample mean is an unbiased estimator of the population mean")
}
Var_y_bar=(1/15)*(sum((y_bar-Y_bar)*(y_bar-Y_bar)));Var_y_bar
Var_srswor=((N-n)/(N*n))*S_sq;Var_srswor
Var_srswr=Sigma_sq/n ;Var_srswr
round(Var_y_bar,4)==round(Var_srswor,4)
Var_srswr>Var_srswor
```

**R-Console(Output):** 

```R
> rm(list=ls())
> N=6
> n=2
> Y=c(1:6)
> x=c()
> y=c()
> count <- 0
> for(i in 1:5)
+ {
+   for( j in (i+1):6)
+   {
+     
+     count <- count+1
+     x[count]=i
+     y[count]=j
+   }
+ }
> mean.sample=(x+y)/2
> Y_sq=Y*Y
> Y_bar=mean(Y);Y_bar
[1] 3.5
> S_sq=var(Y);S_sq
[1] 3.5
> Sigma_sq=((N-1)/N)*S_sq;Sigma_sq
[1] 2.916667
> sample=data.frame(sample.x=x,sample.y=y,mean.sample);sample
   sample.x sample.y mean.sample
1         1        2         1.5
2         1        3         2.0
3         1        4         2.5
4         1        5         3.0
5         1        6         3.5
6         2        3         2.5
7         2        4         3.0
8         2        5         3.5
9         2        6         4.0
10        3        4         3.5
11        3        5         4.0
12        3        6         4.5
13        4        5         4.5
14        4        6         5.0
15        5        6         5.5
> y_bar=mean.sample
> Exp_y_bar=mean(y_bar);Exp_y_bar
[1] 3.5
> if(Y_bar==Exp_y_bar) {
+   paste0("Sample mean is an unbiased estimator of the population mean")
+ } else
+ {
+   paste0("Sample mean is an unbiased estimator of the population mean")
+ }
[1] "Sample mean is an unbiased estimator of the population mean"
> Var_y_bar=(1/15)*(sum((y_bar-Y_bar)*(y_bar-Y_bar)));Var_y_bar
[1] 1.166667
> Var_srswor=((N-n)/(N*n))*S_sq;Var_srswor
[1] 1.166667
> Var_srswr=Sigma_sq/n ;Var_srswr
[1] 1.458333
> round(Var_y_bar,4)==round(Var_srswor,4)
[1] TRUE
> Var_srswr>Var_srswor
[1] TRUE
```

**Conclusion:** From the above experiment,  we conclude that sample mean is an unbiased estimator of the population mean. The calculated sampling variance is equal to variance of sample mean using SRSWOR, which is  equals to 1.166667. And $\displaystyle Var(\bar y)\,in\,srswr>Var(\bar y)\, in\,srswor$ . 
