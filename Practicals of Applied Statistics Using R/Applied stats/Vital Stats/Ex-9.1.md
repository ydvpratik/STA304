# Practical #1

##### Practical Title:  Crude and Standardised death rates

**Experiment:** Compute the crude and Standardised death rates of the two population *A*  and *B* , Regarding *A* as standard population, from the given data:

<table>
 <tr>
  <td rowspan="2" style="text-align:center">Age-group<br>(Years)&nbsp;</td>
  <td colspan="2" style="text-align:center">A&nbsp;</td>
  <td colspan="2" style="text-align:center">B&nbsp;</td>
 </tr>
 <tr>
  <td style="text-align:center">Population&nbsp;</td>
  <td style="text-align:center">Deaths&nbsp;</td>
  <td style="text-align:center">Population&nbsp;</td>
  <td style="text-align:center">Deaths&nbsp;</td>
 </tr>
 <tr>
  <td>Under 10&nbsp;</td>
  <td>20,000&nbsp;</td>
  <td>600&nbsp;</td>
  <td>1200&nbsp;</td>
  <td>372&nbsp;</td>
 </tr>
 <tr>
  <td>10-20&nbsp;</td>
  <td>12,000&nbsp;</td>
  <td>240&nbsp;</td>
  <td>30,000&nbsp;</td>
  <td>660&nbsp;</td>
 </tr>
 <tr>
  <td>20-40&nbsp;</td>
  <td>50,000&nbsp;</td>
  <td>1250&nbsp;</td>
  <td>62,000&nbsp;</td>
  <td>1612&nbsp;</td>
 </tr>
 <tr>
  <td>40-60&nbsp;</td>
  <td>30,000&nbsp;</td>
  <td>1050&nbsp;</td>
  <td>15,000&nbsp;</td>
  <td>525&nbsp;</td>
 </tr>
 <tr>
  <td>Above 60&nbsp;</td>
  <td>10,000&nbsp;</td>
  <td>500&nbsp;</td>
  <td>3,000&nbsp;</td>
  <td>180&nbsp;</td>
 </tr>
</table>




**Aim:** To find Crude and Standardised death rates for the given data.

**Procedure:** 

 *Crude Death Rate (C.D.R)* is defined as the number of deaths (from all causes) per *k* persons in the population of any given region or community during a given period. Thus, in particular, the *annual crude death rate (C.D.R)* denoted by *m* for any given region or community is given by :

$$
m=\frac{Annual\ deaths}{Annual\ mean\ population}\times k   
$$

where *k*=1000, usually.

*Standardised Death Rates* of *A* and *B* are given respectively by :

$$
m^a=\frac{D^a}{P^a}\times1000 =\frac{\displaystyle \sum_xm_x^aP_x^a}{\displaystyle \sum_xp_x^a}
$$

$$
m^b=\frac{D^b}{P^b}\times1000=\frac{\displaystyle\sum_xm_x^bP_x^a}{\displaystyle\sum_xp_x^a}
$$

Where $m_x^a$ is death rate per 1000 for population A ; $m_x^b$ is death rate per 1000 for population B ;  $p_x^a$ is population of A.



**R code:**  



```r
rm(list=ls())
Pop_A_x=c(20000,12000,50000,30000,10000) #population of A
Dea_A_y=c(600,240,1250,1050,500) #Death of A
Pop_B_x=c(12000,30000,62000,15000,3000) #population of B
Dea_B_y=c(372,660,1612,525,180) #death of B
m_A=(Dea_A_y/Pop_A_x)*1000
m_A #death rate per 1000 of A
m_B=(Dea_B_y/Pop_B_x)*1000
m_B #death rate per 1000 of B
t_p_a=sum(Pop_A_x)
t_d_a=sum(Dea_A_y)
t_p_b=sum(Pop_B_x)
t_d_b=sum(Dea_B_y)
cdr_A=(t_d_a/t_p_a)*1000
cdr_A #crude dath rate for population A
cdr_B=(t_d_b/t_p_b)*1000
cdr_B #crude dath rate for population B
stdr_A=(sum(m_A *Pop_A_x))/t_p_a
stdr_A #standard death rate for A
stdr_B=(sum(m_B*Pop_A_x))/t_p_a
stdr_B #standard death rates for B
```

**R console (output):** 

```R
> rm(list=ls())
> Pop_A_x=c(20000,12000,50000,30000,10000) #population of A
> Dea_A_y=c(600,240,1250,1050,500) #Death of A
> Pop_B_x=c(12000,30000,62000,15000,3000) #population of B
> Dea_B_y=c(372,660,1612,525,180) #death of B
> m_A=(Dea_A_y/Pop_A_x)*1000
> m_A #death rate per 1000 of A
[1] 30 20 25 35 50
> m_B=(Dea_B_y/Pop_B_x)*1000
> m_B #death rate per 1000 of B
[1] 31 22 26 35 60
> t_p_a=sum(Pop_A_x)
> t_d_a=sum(Dea_A_y)
> t_p_b=sum(Pop_B_x)
> t_d_b=sum(Dea_B_y)
> cdr_A=(t_d_a/t_p_a)*1000
> cdr_A #crude dath rate for population A
[1] 29.83607
> cdr_B=(t_d_b/t_p_b)*1000
> cdr_B #crude dath rate for population B
[1] 27.45082
> stdr_A=(sum(m_A *Pop_A_x))/t_p_a
> stdr_A #standard death rate for A
[1] 29.83607
> stdr_B=(sum(m_B*Pop_A_x))/t_p_a
> stdr_B #standard death rates for B
[1] 31.42623
```



**Conclusion:**

From the above data we conclude that,

$C.D.R \ of \ A=29.83607$

$C.D.R\ of \ B=27.45082$

$(STDR)_A=29.83607$ 

$(STDR)_B=31.42623$ 