# Practical #12

##### Practical Title:  Cost of Living Index

**Experiment:** For the data in below table, construct the cost of living index for the year 2005 (base 2001=100) using method of weighted price relatives.

<table>
 <tr>
  <td rowspan="2" style="text-align:center">Item&nbsp;</td>
  <td rowspan="2" style="text-align:center">Unit&nbsp;</td>
  <td colspan="2" style="text-align:center">Pice (in Rs.)&nbsp;</td>
  <td rowspan="2" style="text-align:center">Weight&nbsp;</td>
 </tr>
 <tr>
  <td style="text-align:center">2001&nbsp;</td>
  <td style="text-align:center">2005&nbsp;</td>
 </tr>
 <tr>
  <td>A&nbsp;</td>
  <td>Kg.&nbsp;</td>
  <td>50&nbsp;</td>
  <td>75&nbsp;</td>
  <td>10%&nbsp;</td>
 </tr>
 <tr>
  <td>B&nbsp;</td>
  <td>Litre&nbsp;</td>
  <td>60&nbsp;</td>
  <td>75&nbsp;</td>
  <td>25%&nbsp;</td>
 </tr>
 <tr>
  <td>C&nbsp;</td>
  <td>Dozen&nbsp;</td>
  <td>200&nbsp;</td>
  <td>240&nbsp;</td>
  <td>20%&nbsp;</td>
 </tr>
 <tr>
  <td>D&nbsp;</td>
  <td>Kg.&nbsp;</td>
  <td>80&nbsp;</td>
  <td>100&nbsp;</td>
  <td>40%&nbsp;</td>
 </tr>
 <tr>
  <td>E&nbsp;</td>
  <td>One pair&nbsp;</td>
  <td>160&nbsp;</td>
  <td>200&nbsp;</td>
  <td>5%&nbsp;</td>
 </tr>
</table>

**Aim:** To construct the cost of living index for the year 2005 (base 2001=100) using method of weighted price relatives.

**Formulas:** Cost of living index = $\displaystyle \frac{\sum Pw}{\sum w}$   

$\displaystyle P=(p_i/p_o)*100$ ; Where, $p_i$ is price of current year and $p_o$ is price of Base year and $w$ is the Weight .

**R-code:**

```R
p_o=c(50,60,200,80,160)
p_1=c(75,75,240,100,200)
weight=c(10,25,20,40,5)
P=(p_1/p_o)*100
p_w=P*weight
cal_table=data.frame(Item=c('A','B','C','D','E'),po=p_o,pi=p_1,P,weight,Pw=p_w);cal_table
cost_of_liv_index=sum(p_w)/sum(weight);cost_of_liv_index
```

**R-console (output):**

```R
> p_o=c(50,60,200,80,160)
> p_1=c(75,75,240,100,200)
> weight=c(10,25,20,40,5)
> P=(p_1/p_o)*100
> p_w=P*weight
> cal_table=data.frame(Item=c('A','B','C','D','E'),po=p_o,pi=p_1,P,weight,Pw=p_w);cal_table
  Item  po  pi   P weight   Pw
1    A  50  75 150     10 1500
2    B  60  75 125     25 3125
3    C 200 240 120     20 2400
4    D  80 100 125     40 5000
5    E 160 200 125      5  625
> cost_of_liv_index=sum(p_w)/sum(weight);cost_of_liv_index
[1] 126.5
```

**Conclusion:**  From the above experiment we calculate Cost of living index is=126.5 
