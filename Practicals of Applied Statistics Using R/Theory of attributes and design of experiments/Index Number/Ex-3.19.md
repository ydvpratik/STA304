# Practical #13

##### Practical Title: Price and Quantity Index Number

**Experiment:** Prepare price and quantity index numbers for 2005 with 2002 as base year from the following data by using:

$(i)$ Laspeyre's    $(ii)$ Paasche's     $(iii)$ Marshall-Edgeworth  and  $(iv)$ Fisher's Method.

<table>
 <tr>
  <td rowspan="2" style="text-align:center">Year &nbsp;</td>
  <td colspan="2" style="text-align:center">Article I &nbsp;</td>
  <td colspan="2" style="text-align:center">Article II &nbsp;</td>
  <td colspan="2" style="text-align:center">Article III &nbsp;</td>
  <td colspan="2"style="text-align:center">Article IV &nbsp;</td>
 </tr>
 <tr>
  <td style="text-align:center">Price &nbsp;</td>
  <td style="text-align:center">Qty&nbsp;</td>
  <td style="text-align:center">Price&nbsp;</td>
  <td style="text-align:center">Qty&nbsp;</td>
  <td style="text-align:center">Price&nbsp;</td>
  <td style="text-align:center">Qty&nbsp;</td>
  <td style="text-align:center">Price&nbsp;</td>
  <td style="text-align:center">Qty&nbsp;</td>
 </tr>
 <tr>
  <td>2002&nbsp;</td>
  <td>5.00&nbsp;</td>
  <td>5&nbsp;</td>
  <td>7.75&nbsp;</td>
  <td>6&nbsp;</td>
  <td>9.63&nbsp;</td>
  <td>4&nbsp;</td>
  <td>12.50&nbsp;</td>
  <td>9&nbsp;</td>
</tr>
  <td>2005&nbsp;</td>
  <td>6.50&nbsp;</td>
  <td>7&nbsp;</td>
  <td>8.80&nbsp;</td>
  <td>10&nbsp;</td>
  <td>7.75&nbsp;</td>
  <td>6&nbsp;</td>
  <td>12.75&nbsp;</td>
  <td>9&nbsp;</td>
</tr>
</table>
With reference to the above, verify that the Factor Reversal Test and Time Reversal Test are satisfied by Fisher's formula. 



**Aim:** To Prepare price and quantity index numbers for 2005 with 2002 as base year from the following data by using:

$(i)$ Laspeyre's    $(ii)$ Paasche's     $(iii)$ Marshall-Edgeworth  and  $(iv)$ Fisher's Method.

Also, to check whether Factor Reversal Test and Time Reversal Test are satisfied by Fisher's formula.



**Procedure:** $\displaystyle P_{oi}^{La}=\displaystyle \frac{\sum p_{ij}q_{oj}}{\sum p_{oj}q_{oj}}\times100$   ;   $\displaystyle Q_{oi}^{La}=\frac{\sum q_{ij}p_{oj}}{\sum q_{oj}p_{oj}}\times 100$

​					$\displaystyle P_{oi}^{Pa}=\frac{\sum p_{ij}q_{ij}}{\sum p_{oj}q_{ij}}\times 100$    ;   $\displaystyle Q_{oi}^{Pa}=\frac{\sum q_{ij}p_{ij}}{\sum p_{oj}p_{ij}}\times 100$

​					$\displaystyle P_{oi}^{ME}=\frac{1}{2}\bigg(P_{oi}^{La}+P_{oi}^{Pa}\bigg)$  ;   $\displaystyle Q_{oi}^{ME}=\frac{1}{2}\bigg(Q_{oi}^{La}+Q_{oi}^{Pa}\bigg)$

​					$P_{oi}^F=\bigg(P_{oi}^{La}\times P_{oi}^{Pa}\bigg)^{1/2}$

​					$Q_{oi}^F=\bigg(Q_{oi}^{La}\times Q_{oi}^{Pa}\bigg)^{1/2}$           

For Time Reversal Test $\displaystyle P_{oi}^F\times P_{io}^F=1$    and for Factor Reversal Test  $\displaystyle P_{oi}^F\times Q_{oi}^F=\frac{\sum p_{ij}q_{ij}}{\sum p_{oj}q_{oj}}$ .

**R-code:**  

```R
rm(list=ls())
po=c(5.00,7.75,9.63,12.50)
qo=c(5,6,4,9)
p1=c(6.50,8.80,7.75,12.75)
q1=c(7,10,6,9)
p1qo=p1*qo
poqo=po*qo
p1q1=p1*q1
poq1=po*q1
p_la=(sum(p1qo)/sum(poqo))*100;p_la
q_la=(sum(poq1)/sum(poqo))*100;q_la
p_pa=(sum(p1q1)/sum(poq1))*100;p_pa
q_pa=(sum(p1q1)/sum(p1qo))*100;q_pa
p_me=(1/2)*(p_la+p_pa);p_me
q_me=(1/2)*(q_la+q_pa);q_me
p_f=(p_la*p_pa)^(1/2);p_f
q_f=(q_la*q_pa)^(1/2);q_f
p_io_f=(sum(poq1)/sum(p1q1)*sum(poqo)/sum(p1qo))^(1/2)
TRT=(p_f)/100*p_io_f;TRT
if(round(TRT)==1)
{
    paste0("Fisher's index satisfies Time Reversal Test")
}else
{
    paste0("Fisher's index does not satisfies Time Reversal Test")
}
V_oi=(sum(p1q1)/sum(poqo))
FRT=p_f/100*q_f/100;FRT
if(round(V_oi,4)==round(FRT,4))
{
    paste0("Fisher's index satisfies Factor Reversal Test")
}else
{
    paste0("Fisher's index doesn't satisfies Factor Reversal Test")
}
```

**R-console (output):** 

```R
> rm(list=ls())
> po=c(5.00,7.75,9.63,12.50)
> qo=c(5,6,4,9)
> p1=c(6.50,8.80,7.75,12.75)
> q1=c(7,10,6,9)
> p1qo=p1*qo
> poqo=po*qo
> p1q1=p1*q1
> poq1=po*q1
> p_la=(sum(p1qo)/sum(poqo))*100;p_la
[1] 103.8334
> q_la=(sum(poq1)/sum(poqo))*100;q_la
[1] 127.0807
> p_pa=(sum(p1q1)/sum(poq1))*100;p_pa
[1] 104.233
> q_pa=(sum(p1q1)/sum(p1qo))*100;q_pa
[1] 127.5698
> p_me=(1/2)*(p_la+p_pa);p_me
[1] 104.0332
> q_me=(1/2)*(q_la+q_pa);q_me
[1] 127.3253
> p_f=(p_la*p_pa)^(1/2);p_f
[1] 104.033
> q_f=(q_la*q_pa)^(1/2);q_f
[1] 127.325
> p_io_f=(sum(poq1)/sum(p1q1)*sum(poqo)/sum(p1qo))^(1/2)
> TRT=(p_f)/100*p_io_f;TRT
[1] 1
> if(round(TRT)==1)
+ {
+     paste0("Fisher's index satisfies Time Reversal Test")
+ }else
+ {
+     paste0("Fisher's index does not satisfies Time Reversal Test")
+ }
[1] "Fisher's index satisfies Time Reversal Test"
> V_oi=(sum(p1q1)/sum(poqo))
> FRT=p_f/100*q_f/100;FRT
[1] 1.3246
> if(round(V_oi,4)==round(FRT,4))
+ {
+     paste0("Fisher's index satisfies Factor Reversal Test")
+ }else
+ {
+     paste0("Fisher's index doesn't satisfies Factor Reversal Test")
+ }
[1] "Fisher's index satisfies Factor Reversal Test"
```

**Conclusion:** From the above experiment we calculate that 

- Laspeyre's Price index = 103.8334                     and       Laspeyre's Quantity index=127.0807
- Paasche's Price index = 104.233                       and       Paasche's Quantity index =127.5698
- Marshall-Edgeworth Price index = 104.0332       and        Marshall-Edgeworth Quantity index = 127.3253
-   Fisher's  Price index = 104.033                      and         Fisher's Quantity index =127.325

Factor Reversal Test and Time Reversal Test both are satisfied by Fisher's formula.
