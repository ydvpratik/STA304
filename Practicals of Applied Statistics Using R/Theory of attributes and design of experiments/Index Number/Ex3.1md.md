# Practical #11

##### Practical Topic: Price Index Number

**Experiment:** $(a)$ From the following data calculate price index numbers for 2005 with 1995 as base by : $(i)$ Laspeyer's  $(ii)$ Paasche's  $(iii)$ Marshall-Edgeworth  and $(iv)$ Fisher's formulae:

<table>
 <tr>
  <td style="text-align:center" rowspan="2">Commodities&nbsp;</td>
  <td style="text-align:center" colspan="2">1995&nbsp;</td>
  <td style="text-align:center" colspan="2">2005&nbsp;</td>
 </tr>
 <tr>
  <td style="text-align:center">Price&nbsp;</td>
  <td style="text-align:center">Quantity&nbsp;</td>
  <td style="text-align:center">Price&nbsp;</td>
  <td style="text-align:center">Quantity&nbsp;</td>
 </tr>
 <tr>
  <td style="text-align:center">A&nbsp;</td>
  <td style="text-align:center">20&nbsp;</td>
  <td style="text-align:center">8&nbsp;</td>
  <td style="text-align:center">40&nbsp;</td> 
  <td style="text-align:center">6&nbsp;</td>
 </tr>
 <tr>
  <td style="text-align:center">B&nbsp;</td>
  <td style="text-align:center">50&nbsp;</td>
  <td style="text-align:center">10&nbsp;</td>
  <td style="text-align:center">60&nbsp;</td>
  <td style="text-align:center">5&nbsp;</td>
 </tr>
 <tr>
  <td style="text-align:center">C&nbsp;</td>
  <td style="text-align:center">40&nbsp;</td>
  <td style="text-align:center">15&nbsp;</td>
  <td style="text-align:center">50&nbsp;</td>
  <td style="text-align:center">15&nbsp;</td>
 </tr>
  <tr>
  <td style="text-align:center">D&nbsp;</td>
  <td style="text-align:center">20&nbsp;</td>
  <td style="text-align:center">20&nbsp;</td>
  <td style="text-align:center">20&nbsp;</td>
  <td style="text-align:center">25&nbsp;</td>
 </tr>
</table>

$(b)$ It is stated that Marshall-Edgeworth index number is a good approximation to Fisher's ideal index number. Verify this for data in part $(a)$ .

**Aim:** To calculate price index numbers for 2005 with 1995 as base by : $(i)$ Laspeyer's  $(ii)$ Paasche's  $(iii)$ Marshall-Edgeworth  and $(iv)$ Fisher's formulae from the above data. Also to verify if Marshall-Edgeworth index number is a good approximation to Fisher's ideal index number.

**Procedure:**  Laspeyre's Price Index is given by: $\displaystyle P_{0i}^{La}=\frac{\sum p_iq_0}{\sum p_0q_0}\times 100$ 

​					Paasche's Price Index is given by: $\displaystyle P_{0i}^{Pa}=\frac{\sum p_iq_i}{\sum p_0q_i}\times 100$ 

​					Marshall-Edgeworth Price Index is given by: $\displaystyle P_{0i}^{ME}=\bigg(\frac{\sum p_iq_0+\sum p_iq_i}{\sum p_0q_0+\sum p_0q_i}\bigg)\times 100$ 

​					Fisher's Price Index is given by:  $\displaystyle P_{0i}^{F}=\sqrt{\frac{\sum p_iq_0}{\sum p_0q_0}\times \frac{\sum p_iq_i}{\sum p_0q_i}}\times 100$  

**R-code:** 

```R
po=c(20,50,40,20)
qo=c(8,10,15,20)
pi=c(40,60,50,20)
qi=c(6,5,15,25)
poqo=po*qo
poqi=po*qi
piqo=pi*qo
piqi=pi*qi
cal_table=data.frame(commodities=c('A','B','C','D'),po,qo,pi,qi,poqo,poqi,piqo,piqi);cal_table
P_la=(sum(piqo)/sum(poqo))*100;P_la
P_pa=(sum(piqi)/sum(poqi))*100;P_pa
P_me=((sum(piqo)+sum(piqi))/(sum(poqo)+sum(poqi)))*100;P_me
P_f=sqrt(P_la*P_pa);P_f
if(P_me>P_f){
    paste0("Marshall-edgeworth index number is a good approximation to Fishers ideal index number")
}else
{
    paste0("Fisher index number is a good approximation to Marshall-Edgeworth index number")
}
```

**R-console (output):** 

```R
> po=c(20,50,40,20)
> qo=c(8,10,15,20)
> pi=c(40,60,50,20)
> qi=c(6,5,15,25)
> poqo=po*qo
> poqi=po*qi
> piqo=pi*qo
> piqi=pi*qi
> cal_table=data.frame(commodities=c('A','B','C','D'),po,qo,pi,qi,poqo,poqi,piqo,piqi);cal_table
  commodities po qo pi qi poqo poqi piqo piqi
1           A 20  8 40  6  160  120  320  240
2           B 50 10 60  5  500  250  600  300
3           C 40 15 50 15  600  600  750  750
4           D 20 20 20 25  400  500  400  500
> P_la=(sum(piqo)/sum(poqo))*100;P_la
[1] 124.6988
> P_pa=(sum(piqi)/sum(poqi))*100;P_pa
[1] 121.7687
> P_me=((sum(piqo)+sum(piqi))/(sum(poqo)+sum(poqi)))*100;P_me
[1] 123.3227
> P_f=sqrt(P_la*P_pa);P_f
[1] 123.225
> if(P_me>P_f){
+     paste0("Marshall-edgeworth index number is a good approximation to Fishers ideal index number")
+ }else
+ {
+     paste0("Fisher index number is a good approximation to Marshall-Edgeworth index number")
+ }
[1] "Marshall-edgeworth index number is a good approximation to Fishers ideal index number"
```

**Conclusion:** From the above experiment we calculate;

-  Laspeyre's Price Index=124.6988 
- Paasche's Price Index= 121.7687
- Marshall-Edgeworth Price Index= 123.3227
- Fisher's Price Index= 123.225

And also concluded that Marshall-Edgeworth index number is a good approximation to Fisher's ideal index number in this given case.
