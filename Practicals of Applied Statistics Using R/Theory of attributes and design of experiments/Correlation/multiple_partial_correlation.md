# Practical #24

##### Practical Topic: Partial and Multiple Correlation Coefficient

**Experiment:** From the data relating to the yield of dry bark $(X_1)$, height $(X_2)$ and girth $(X_3)$ for 18 cinchona plants, the following correlation coefficient were obtained:

​						$r_{12}=0.77,\ r_{13}=0.72,\ and \ r_{23}=0.52.$ 

Find the partial correlation coefficient $r_{12.3}$ and multiple correlation coefficient $R_{1.23}.$  

**Aim:** To compute partial correlation coefficient $r_{12.3}$  and multiple correlation coefficient $R_{1.23}$ .

**Procedure:** Partial correlation coefficient $r_{12.3}$ is given by, 

$$
r_{12.3}=\frac{r_{12}-r_{13}r_{23}}{\sqrt{(1-r_{13}^2)(1-r_{23}^2)}}
$$

and, Multiple correlation coefficient $R_{1.23}$is given by,

$$
R_{1.23}^2=\frac{r_{12}^2+r_{13}^2-2r_{12}r_{13}r_{23}}{1-r_{23}^2}
$$

**R-Code:** 

```R
rm(list=ls())
corr_coeff=c(0.77,0.72,0.52)
r12.3=(corr_coeff[1]-(corr_coeff[2]*corr_coeff[3]))/sqrt((1-corr_coeff[2]^2)*(1-corr_coeff[3]^2));r12.3
R1.23=sqrt((corr_coeff[1]^2+corr_coeff[2]^2-(2*corr_coeff[1]*corr_coeff[2]*corr_coeff[3]))/(1-corr_coeff[3]^2));R1.23
```

**R-Console(output):** 

```R
> rm(list=ls())
> corr_coeff=c(0.77,0.72,0.52)
> r12.3=(corr_coeff[1]-(corr_coeff[2]*corr_coeff[3]))/sqrt((1-corr_coeff[2]^2)*(1-corr_coeff[3]^2));r12.3
[1] 0.6673761
> R1.23=sqrt((corr_coeff[1]^2+corr_coeff[2]^2-(2*corr_coeff[1]*corr_coeff[2]*corr_coeff[3]))/(1-corr_coeff[3]^2));R1.23
[1] 0.8560959
```

**Conclusion:**  From the above data we find that value of $r_{12.3}=0.6673761$   and $R_{1.23}=0.8560959$ .
