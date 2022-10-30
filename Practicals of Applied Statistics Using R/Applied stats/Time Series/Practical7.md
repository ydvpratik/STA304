# Practical #7

##### Practical Title: Moving Average 

**Experiment:** Apply 3-year moving average to the following data on production of cements . Plot the data and the trend values on the same graph.

| Year            | 1992 | 1993 | 1994 | 1995 | 1996 | 1997 | 1998 | 1999 |
| --------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Output(in 1000) | 1542 | 1447 | 1552 | 2102 | 2612 | 3195 | 3537 | 3567 |

**Aim:** To find the 3-year moving average of the data on production of cement. Plotting of the graph of trend value for the given data.

**Methodology:** We would apply moving average to the above data and find the trend values. To calculate the 3-year moving average, we have to compute the mean of the first 3-year and place it for the $2^{nd}$  year, similarly we compute for $3^{rd}$ year.

**R-Command:** 

```R
year=c(1992,1993,1994,1995,1996,1997,1998,1999);
trend_year=c(1993,1994,1995,1996,1997,1998);
production=c(1542,1447,1552,2102,2612,3195,3537,3567);
mov=c()
for (i in 1:6) {
    mov[i]=production[i]+production[i+1]+production[i+2];
};mov;
movavg=mov/3;
movavg;
plot(year,production,"o",lty=1,pch=2,xlab="years",ylab="production and moving average");
lines(trend_year,movavg,"o",lty=2,pch=1);
```

**R-Console:** 

```R
> year=c(1992,1993,1994,1995,1996,1997,1998,1999);
> trend_year=c(1993,1994,1995,1996,1997,1998);
> production=c(1542,1447,1552,2102,2612,3195,3537,3567);
> mov=c()
> for (i in 1:6) {
+     mov[i]=production[i]+production[i+1]+production[i+2];
+ 
+ };mov;
[1]  4541  5101  6266  7909  9344 10299
> movavg=mov/3;
> movavg;
[1] 1513.667 1700.333 2088.667 2636.333 3114.667 3433.000
> plot(year,production,"o",lty=1,pch=2,xlab="years",ylab="production and moving average");
> lines(trend_year,movavg,"o",lty=2,pch=1);
> 
```

**R-Graphics:** 
![image-20220901213948430](https://raw.githubusercontent.com/ydvpratik/img/master/2022/09/upgit_20220916_1663341095.png)
