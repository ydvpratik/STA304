# Practical #2

##### Practical Title: Standardised death rates

**Experiment:**  Estimate the standardised death rates for the two countries from the given data.

<table>
 <tr>
  <td style="text-align: center" rowspan="2"> Age group (in years)&nbsp;</td>
  <td style="text-align: center" colspan="2">Death Rate per 1000&nbsp;</td>
  <td style="text-align: center" rowspan="2">Standardised<br>population (in lakhs)&nbsp;</td>
 </tr>
 <tr>
  <td>Country A&nbsp;</td>
  <td>Country B&nbsp;</td>
 </tr>
 <tr>
  <td>0-4&nbsp;</td>
  <td>20.00&nbsp;</td>
  <td>5.00&nbsp;</td>
  <td>100&nbsp;</td>
 </tr>
  <tr>
  <td>5-14&nbsp;</td>
  <td>1.00&nbsp;</td>
  <td>0.50&nbsp;</td>
  <td>200&nbsp;</td>
 </tr>
 <tr>
  <td>15-24&nbsp;</td>
  <td>1.40&nbsp;</td>
  <td>1.00&nbsp;</td>
  <td>190&nbsp;</td>
 </tr>
 <tr>
  <td>25-34&nbsp;</td>
  <td>2.00&nbsp;</td>
  <td>1.00&nbsp;</td>
  <td>180&nbsp;</td>
 </tr>
 <tr>
  <td>35-44&nbsp;</td>
  <td>3.30&nbsp;</td>
  <td>2.00&nbsp;</td>
  <td>120&nbsp;</td>
 </tr>
 <tr>
  <td>45-54&nbsp;</td>
  <td>7.00&nbsp;</td>
  <td>5.00&nbsp;</td>
  <td>100&nbsp;</td>
 </tr>
 <tr>
  <td>55-64&nbsp;</td>
  <td>15.00&nbsp;</td>
  <td>12.00&nbsp;</td>
  <td>70&nbsp;</td>
 </tr>
 <tr>
  <td>65-74&nbsp;</td>
  <td>40.00&nbsp;</td>
  <td>35.00&nbsp;</td>
  <td>30&nbsp;</td>
 </tr>
 <tr>
  <td>75 and above&nbsp;</td>
  <td>120.00&nbsp;</td>
  <td>110.00&nbsp;</td>
  <td>10&nbsp;</td>
 </tr>
</table>

**Aim:** To calculate standardised death rate from the above data.

**Procedure:** *Standardised Death Rates* of *A* and *B* are given respectively by :

$$
(STDR)_A=\frac{\displaystyle\sum_xm_x^aP_x^s}{\displaystyle\sum_xP_x^s}
$$

$$
(STDR)_B=\frac{\displaystyle\sum_xm_x^bP_x^s}{\displaystyle\sum_xP_x^s}
$$

Where $m_x^a$  is Death rate per 1000 for Country A ; $m_x^b$ is Death rate per 1000 for country B ; $P_x^s$ is Standardised population 

**R code:** 

```r
rm(list=ls())
m_a=c(20.0,1.0,1.4,2.0,3.3,7.0,15.0,40.0,120.0)
m_b=c(5.0,0.5,1.0,1.0,2.0,5.0,12.0,35.0,110.0)
P_s=c(100,200,190,180,120,100,70,30,10)
L_a=m_a *P_s
L_b=m_b *P_s
STDR_A=sum(L_a)/sum(P_s)
STDR_A
STDR_B=sum(L_b)/sum(P_s)
STDR_B
```

**R console:** 

``` R
> rm(list=ls())
> m_a=c(20.0,1.0,1.4,2.0,3.3,7.0,15.0,40.0,120.0)
> m_b=c(5.0,0.5,1.0,1.0,2.0,5.0,12.0,35.0,110.0)
> P_s=c(100,200,190,180,120,100,70,30,10)
> L_a=m_a *P_s
> L_b=m_b *P_s
> STDR_A=sum(L_a)/sum(P_s)
> STDR_A
[1] 7.372
> STDR_B=sum(L_b)/sum(P_s)
> STDR_B
[1] 4.7
```

**CONCLUSION:**

From the above Experiment we conclude that:

$(STDR)_A=7.372$

$(STDR)_B=4.7$ 
