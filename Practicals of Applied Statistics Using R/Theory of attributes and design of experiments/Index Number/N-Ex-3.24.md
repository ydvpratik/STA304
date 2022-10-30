# Practical #10

##### Practical Topic: Consumer Price Index Number

**Experiment:** An enquiry into the budgets of the middle class families of a certain city revealed that on an average the percentage expenses on the different groups were food 45, Rent 15, Clothing 12, Fuel 8, Light 8 and Miscellaneous 20. The group index numbers for the current year as compared with a fixed base period were respectively 410, 150, 343, 248 and 285. Calculate the consumer price index number for the current year. Mr. X was getting Rs. 24,000 p.m. in base period and Rs. 43,000 in the current year. State how much he ought to have received as extra allowance to maintain his former standard of living (w.r.t change in prices).

**Aim:** To calculate consumer price index and hence find compensation to maintain former standard of living.

**Procedure:** Consumer Price Index Number is given by, $\displaystyle \frac{\sum Iw}{\sum w}$  ; where $I$ is Group Index and $w$ is % Expenses.

**R-code:** 

```R
base_inc=24000
current_inc=43000
I=c(410,150,343,248,285)
w=c(45,15,12,8,20)
Iw=I*w
cal_table=data.frame(Groups=c("Food","Rent","Clothing","Fuel and light","Miscellaneous"),Group_index=I,Expenses=w,Iw);cal_table
con_price_index_no=sum(Iw)/sum(w);con_price_index_no
X=(con_price_index_no/100)*base_inc;X
Y=X-current_inc;Y
paste0("The required extra Allowance to be granted to MR X to maintain the same standard of living as in the base year is:₹",Y)
```

**R-console (output):** 

```R
> base_inc=24000
> current_inc=43000
> I=c(410,150,343,248,285)
> w=c(45,15,12,8,20)
> Iw=I*w
> cal_table=data.frame(Groups=c("Food","Rent","Clothing","Fuel and light","Miscellaneous"),Group_index=I,Expenses=w,Iw);cal_table
          Groups Group_index Expenses    Iw
1           Food         410       45 18450
2           Rent         150       15  2250
3       Clothing         343       12  4116
4 Fuel and light         248        8  1984
5  Miscellaneous         285       20  5700
> con_price_index_no=sum(Iw)/sum(w);con_price_index_no
[1] 325
> X=(con_price_index_no/100)*base_inc;X
[1] 78000
> Y=X-current_inc;Y
[1] 35000
> paste0("The required extra Allowance to be granted to MR X to maintain the same standard of living as in the base year is:₹",Y)
[1] "The required extra Allowance to be granted to MR X to maintain the same standard of living as in the base year is:₹35000"
```

**Conclusion:** From the above experiment, we calculate consumer price index=325 and Mr X needs ₹35000 pm extra allowance to maintain standard of living in current year.