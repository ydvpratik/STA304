# Practical #16

##### Practical Topic: Number of defectives(np) charts

**Experiment:** 20 samples each of size 10 were inspected. The number of defectives detected in each of them is given below:

| Samples No.       |  1   |  2   |  3   |  4   |  5   |  6   |  7   |  8   |  9   |  10  |
| :---------------- | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| No. of defectives |  0   |  1   |  0   |  3   |  9   |  2   |  0   |  7   |  0   |  1   |
| Samples No.       |  11  |  12  |  13  |  14  |  15  |  16  |  17  |  18  |  19  |  20  |
| No. of defectives |  1   |  0   |  0   |  3   |  1   |  0   |  0   |  2   |  1   |  0   |

Construct the 'number of defectives' chart and establish quality standard for the future.

**Aim:** To Construct the 'number of defectives' chart and establish quality standard for the future.

**Procedure:** Estimate of the process fraction defective is given by $\displaystyle \bar p=\frac{\sum d}{nk}$  ; where d is no. of defectives and n is sample size.

$\displaystyle 3-\sigma $  control limits for np-chart are given by; $CL_{np}=n\bar p\;,\;UCL_{np}=n\bar p+3\sqrt{n\bar p(1-\bar p)}\;and\;LCL_{np}=n\bar p-3\sqrt{n\bar p(1-\bar p)}$ 

**R-Code:** 

```R
rm(list=ls())
n=10
Sample=c(1:20)
nod = c(0,1,0,3,9,2,0,7,0,1,1,0,0,3,1,0,0,2,1,0)
sum_nod = sum(nod);sum_nod
p_bar = sum_nod/(length(nod)*n);p_bar
q_bar = 1-p_bar;q_bar
CL_np = n*p_bar;CL_np
UCL_np = round(CL_np + 3*sqrt(CL_np*(1-p_bar)),2);UCL_np
LCL_np = round(max(0,CL_np - 3*sqrt(CL_np*(1-p_bar))),2);LCL_np
Sample[nod>UCL_np | nod<LCL_np]

#Revised np Control Chart
new_pbar = round((sum_nod-sum((nod[nod>UCL_np | nod<LCL_np])))/(n*(length(nod)-length(nod[nod>UCL_np | nod<LCL_np]))),3);new_pbar
new_qbar =round(1 - new_pbar,3);new_qbar
new_CL_np =round(10*new_pbar,2);new_CL_np
new_UCL_np =round(new_CL_np + 3*sqrt(new_CL_np*new_qbar),2);new_UCL_np
new_LCL_np = max(0,new_CL_np - 3*sqrt(new_CL_np*new_qbar));new_LCL_np
```

**R-Console(Output):** 

```R
> rm(list=ls())
> n=10
> Sample=c(1:20)
> nod = c(0,1,0,3,9,2,0,7,0,1,1,0,0,3,1,0,0,2,1,0)
> sum_nod = sum(nod);sum_nod
[1] 31
> p_bar = sum_nod/(length(nod)*n);p_bar
[1] 0.155
> q_bar = 1-p_bar;q_bar
[1] 0.845
> CL_np = n*p_bar;CL_np
[1] 1.55
> UCL_np = round(CL_np + 3*sqrt(CL_np*(1-p_bar)),2);UCL_np
[1] 4.98
> LCL_np = round(max(0,CL_np - 3*sqrt(CL_np*(1-p_bar))),2);LCL_np
[1] 0
> Sample[nod>UCL_np | nod<LCL_np]
[1] 5 8
> 
> #Revised np Control Chart
> new_pbar = round((sum_nod-sum((nod[nod>UCL_np | nod<LCL_np])))/(n*(length(nod)-length(nod[nod>UCL_np | nod<LCL_np]))),3);new_pbar
[1] 0.083
> new_qbar =round(1 - new_pbar,3);new_qbar
[1] 0.917
> new_CL_np =round(10*new_pbar,2);new_CL_np
[1] 0.83
> new_UCL_np =round(new_CL_np + 3*sqrt(new_CL_np*new_qbar),2);new_UCL_np
[1] 3.45
> new_LCL_np = max(0,new_CL_np - 3*sqrt(new_CL_np*new_qbar));new_LCL_np
[1] 0
```

**Conclusion: ** From the above experiment we conclude that two point corresponding to 5th and 8th samples lies outside the control limit, so the process is not in the state of statistical control. After deleting these sample, revised control limits are CL = 0.83, UCL = 3.45 and LCL = 0.