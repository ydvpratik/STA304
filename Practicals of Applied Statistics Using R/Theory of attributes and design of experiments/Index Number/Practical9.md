# Practical #9

##### Practical Title: Index Number

**Experiment:** The table below gives the wholesale price $(p)$ and quantity $(q)$ of number of commodities in DC. Calculate $(i)$ Laspeyre's $(ii)$ Paasche's $(iii)$ Edgeworth-Marshal  $(iv)$ Fisher's Ideal index no.

<table>
 <tr>
  <td rowspan="2">Commodity&nbsp;</td>
  <td style="text-align:center" colspan="2">1982&nbsp;</td>
  <td style="text-align:center" colspan="2">1985&nbsp;</td>
 </tr>
 <tr>
  <td>p<sub>0</sub>&nbsp;</td>
  <td>q<sub>0</sub>&nbsp;</td>
  <td>p<sub>1</sub>&nbsp;</td>
  <td>q<sub>1</sub>&nbsp;</td>
 </tr>
 <tr>
  <td>A&nbsp;</td>
  <td>277.92&nbsp;</td>
  <td>1.1&nbsp;</td>
  <td>366.67&nbsp;</td>
  <td>6.2&nbsp;</td>
 </tr>
 <tr>
  <td>B&nbsp;</td>
  <td>176.25&nbsp;</td>
  <td>106.0&nbsp;</td>
  <td>186.58&nbsp;</td>
  <td>116.9&nbsp;</td>
 </tr>
 <tr>
  <td>C&nbsp;</td>
  <td>151.00&nbsp;</td>
  <td>4.2&nbsp;</td>
  <td>182.57&nbsp;</td>
  <td>5.5&nbsp;</td>
 </tr>
 <tr>
  <td>D&nbsp;</td>
  <td>121.83&nbsp;</td>
  <td>2.4&nbsp;</td>
  <td>181.25&nbsp;</td>
  <td>1.0&nbsp;</td>
 </tr>
  <tr>
  <td>E&nbsp;</td>
  <td>156.75&nbsp;</td>
  <td>13.1&nbsp;</td>
  <td>155.75&nbsp;</td>
  <td>6.1&nbsp;</td>
 </tr>
  </tr>
  <tr>
  <td>F&nbsp;</td>
  <td>273.00&nbsp;</td>
  <td>1.0&nbsp;</td>
  <td>498.83&nbsp;</td>
  <td>0.6&nbsp;</td>
 </tr>
</table>


**Aim:** To find  $(i)$ Laspeyre's $(ii)$ Paasche's $(iii)$ Edgeworth-Marshal  $(iv)$ Fisher's Ideal index no.

**Procedure:**

$(i)$ Laspeyre's Index no:
$$
I^{La}= \frac{\sum_{j=1}^np_{ij}q_{0j}}{\sum_{j=i}^np_{0j}q_{0j}}\times100
$$


$(ii)$ Paasche's Index No:
$$
I^{Pa}=\frac{\sum_{j=1}^n p_{ij}q_{ij}}{\sum_{j=1}^np_{0i}q_{ij}}\times100
$$


$(iii)$ Marshal-Edgeworth Index no:
$$
I^{MR}=\frac{\sum_{j=1}^np_{ij}(q_{0j}+q_{ij})}{\sum_{j=1}^np_{0j}(q_{oj}+q_{ij})}\times100
$$
$(iv)$ Fisher's Ideal Index no. :
$$
I^{Fi}=\sqrt{I^{La}\times I^{Pa}}
$$

**R-code:**


```R
la=0
Pa=0
em=0
fi=0
p0=c(277.92,176.25,151.00,121.83,156.75,273.00)
q0=c(1.1,106.0,4.2,2.4,13.1,1.0)
p1=c(366.67,186.58,182.57,181.25,155.75,498.83)
q1=c(6.2,116.9,5.5,1.0,6.1,0.6)
la=(sum(p1*q0)/sum(p0*q0))*100
la
Pa=(sum(p1*q1)/sum(p0*q0))*100
Pa
em=(sum(p1*(q1+q0))/sum(p0*(q1+q0)))*100
em
fi=sqrt(la*Pa)
fi
```

**R-Output:** 



```R
> la=0
> Pa=0
> em=0
> fi=0
> p0=c(277.92,176.25,151.00,121.83,156.75,273.00)
> q0=c(1.1,106.0,4.2,2.4,13.1,1.0)
> p1=c(366.67,186.58,182.57,181.25,155.75,498.83)
> q1=c(6.2,116.9,5.5,1.0,6.1,0.6)
> la=(sum(p1*q0)/sum(p0*q0))*100
> la
[1] 107.556
> Pa=(sum(p1*q1)/sum(p0*q0))*100
> Pa
[1] 119.2349
> em=(sum(p1*(q1+q0))/sum(p0*(q1+q0)))*100
> em
[1] 108.1492
> fi=sqrt(la*Pa)
> fi
[1] 113.245
```

**Conclusion:** From above experiment we calculate $(i)$ Laspeyre's Index No.=107.556   $(ii)$ Paasche's  Index  No.=119.2349   $(iii)$ Edgeworth-Marshal Index No.=108.1492  $(iv)$ Fisher's Ideal  Index No.=113.245 
