# Practical #14

##### Practical Title: $3-\sigma$  Control Limits for p-chart

**Experiment:** From the following inspection results, construct $3-\sigma$  control limits for  $p$ chart:

| Date Sept. | No. of Defectives | Date Sept. | No. of Defectives | Date Sept. | No. of Defectives |
| ---------- | ----------------- | ---------- | ----------------- | ---------- | ----------------- |
| 1          | 22                | 11         | 70                | 21         | 66                |
| 2          | 40                | 12         | 80                | 22         | 50                |
| 3          | 36                | 13         | 40                | 23         | 46                |
| 4          | 32                | 14         | 22                | 24         | 32                |
| 5          | 42                | 15         | 32                | 25         | 42                |
| 6          | 40                | 16         | 42                | 26         | 46                |
| 7          | 30                | 17         | 20                | 27         | 30                |
| 8          | 44                | 18         | 46                | 28         | 38                |
| 9          | 42                | 19         | 28                | 29         | 40                |
| 10         | 38                | 20         | 36                | 30         | 24                |

​		The sub-groups, from which the defectives were taken out, were of the same size. i.e., 1,000 items each.

​		Without constructing the control chart, comment on the state of control of process. If the process is out of control, then suggest the revised control limits for future use.

**Aim:** To comment on the state of control process and if the process is out of control, then suggest the revised control limits for future use.

**Procedure:**  $\displaystyle \bar p=\frac{\sum d}{nk}$ ;   Where d is no. of defective , n is sample size.

​	$\displaystyle 3-\sigma \;Control\;Limits\;for\;p-chart\;is: \;CL_p=\bar p\;,\;UCL_p=\bar p+3\sqrt{\frac{\bar p(1-\bar p)}{n}}\;\;\;and \;LCL_p=\bar p-3\sqrt{\frac{\bar p(1-\bar p)}{n}}$  	 

**R-code:** 

```R
nod = c(22,40,36,32,42,40,30,44,42,38,70,80,44,22,32,42,20,46,28,36,66,50,46,32,42,46,30,38,40,24)
fd = nod/1000
Date=c(1:30)
cal_table=data.frame(Date,Number_of_def=nod,Fraction_def=fd);cal_table
sum_nod = sum(nod)
sum_fd = sum(fd);sum_fd
n = 1000
k = 30
p_bar = sum_nod/(n*k)
UCL_p = round(p_bar + 3*sqrt((p_bar*(1-p_bar))/n),4);UCL_p
CL_p = round(p_bar,4);CL_p
LCL_p = round(p_bar - 3*sqrt((p_bar*(1-p_bar))/n),4);LCL_p
Date[fd>UCL_p | fd<LCL_p]

#REVISED CONTROL LIMIT
new_cl_p = round((sum(nod)-sum(nod[fd>UCL_p | fd<LCL_p]))/((length(nod)-length(nod[fd>UCL_p | fd<LCL_p]))*n),4);new_cl_p
new_ucl_p = round(new_cl_p + 3*sqrt((new_cl_p*(1-new_cl_p)/n)),4);new_ucl_p
new_lcl_p = round(new_cl_p - 3*sqrt((new_cl_p*(1-new_cl_p)/n)),4);new_lcl_p
```

**R-Console(Output):** 

```R
> nod = c(22,40,36,32,42,40,30,44,42,38,70,80,44,22,32,42,20,46,28,36,66,50,46,32,42,46,30,38,40,24)
> fd = nod/1000
> Date=c(1:30)
> cal_table=data.frame(Date,Number_of_def=nod,Fraction_def=fd);cal_table
   Date Number_of_def Fraction_def
1     1            22        0.022
2     2            40        0.040
3     3            36        0.036
4     4            32        0.032
5     5            42        0.042
6     6            40        0.040
7     7            30        0.030
8     8            44        0.044
9     9            42        0.042
10   10            38        0.038
11   11            70        0.070
12   12            80        0.080
13   13            44        0.044
14   14            22        0.022
15   15            32        0.032
16   16            42        0.042
17   17            20        0.020
18   18            46        0.046
19   19            28        0.028
20   20            36        0.036
21   21            66        0.066
22   22            50        0.050
23   23            46        0.046
24   24            32        0.032
25   25            42        0.042
26   26            46        0.046
27   27            30        0.030
28   28            38        0.038
29   29            40        0.040
30   30            24        0.024
> sum_nod = sum(nod)
> sum_fd = sum(fd);sum_fd
[1] 1.2
> n = 1000
> k = 30
> p_bar = sum_nod/(n*k)
> UCL_p = round(p_bar + 3*sqrt((p_bar*(1-p_bar))/n),4);UCL_p
[1] 0.0586
> CL_p = round(p_bar,4);CL_p
[1] 0.04
> LCL_p = round(p_bar - 3*sqrt((p_bar*(1-p_bar))/n),4);LCL_p
[1] 0.0214
> Date[fd>UCL_p | fd<LCL_p]
[1] 11 12 17 21
> 
> #REVISED CONTROL LIMIT
> new_cl_p = round((sum(nod)-sum(nod[fd>UCL_p | fd<LCL_p]))/((length(nod)-length(nod[fd>UCL_p | fd<LCL_p]))*n),4);new_cl_p
[1] 0.0371
> new_ucl_p = round(new_cl_p + 3*sqrt((new_cl_p*(1-new_cl_p)/n)),4);new_ucl_p
[1] 0.055
> new_lcl_p = round(new_cl_p - 3*sqrt((new_cl_p*(1-new_cl_p)/n)),4);new_lcl_p
[1] 0.0192
```

**Conclusion:**  From the above experiment we observe that the fraction defectives on 11th, 12th, 17th, 21st September fall outside the control limit. And the Revised control limits are; $\displaystyle UCL_p=0.055$ ,  $CL_p=0.0371$  and $LCL_p=0.0192$ . 

