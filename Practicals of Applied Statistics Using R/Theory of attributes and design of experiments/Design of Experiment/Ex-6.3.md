# Practical #23

##### Practical Topic: Analysis of Variance(ANOVA)

**Experiment:** The given Table shows some of the results of an experiment on the effect of applications of Sulphur in reducing scale disease of potatoes. The object in applying Sulphur is to increase the acidity of the soil since scale does not thrive in very acid soil. In addition to untreated plots which serve as control 3 amounts of dressing are compared 300,600 and 1,200 lbs per acre. Both a spring and fall application of each treatment was seven distinct treatments. The quantity to be analysed is the scale index. This is roughly speaking, the scale index. This is roughly speaking, the percentage of the surface area of the potato that is infected with scab. [F = Fall, S = Spring application, O = Control  ]

​	The numbers 3,6,12 are the amounts of Sulphur in 100 lb. per acer. Analyse the experiment and give your conclusion.

| $F_3$  <br />9 |   $O$<br />12   |  $S_6$ <br />18  | $F_{12}$<br />10 | $S_6$<br />24 | $S_{12}$<br />17 | $S_3$<br />30 |  $F_6$<br />16  |
| :------------: | :-------------: | :--------------: | :--------------: | :-----------: | :--------------: | :-----------: | :-------------: |
|  $O$<br />10   |  $S_3$<br />7   | $F_{12}$<br />4  |  $F_6$<br />10   | $S_3$<br />24 |   $O$<br />24    |  $O$<br />29  |  $S_6$<br />12  |
|  $F_3$<br />9  | $S_{12}$<br />7 |  $F_5$<br />18   |   $O$<br />30    | $F_6$<br />18 | $S_{12}$<br />16 | $F_3$<br />16 | $F_{12}$<br />4 |
|  $S_3$<br />9  |   $O$<br />18   | $S_{12}$<br />17 |  $S_6$<br />19   |  $O$<br />12  | $F_{12}$<br />5  |  $O$<br />26  |  $F_3$ <br />4  |

**Aim:** To analyze the randomized experiment on potato to find effectiveness of application of Sulphur to reduce scale of disease of potato.

**Procedure:** Correction factor is given by; $C.F=\displaystyle \frac{G^2}{N}$  

Total S.S. = $\displaystyle \sum_i\sum_j{y_{ij}}^2-C.F.$ ,  Treatment S.S = $\displaystyle\sum\frac{T_i^2}{r_t}-C.F$ , Error S.S  = $Total \,S.S-Treatment\,S.S$ and  M.S.S=$\displaystyle \frac{S.S.}{d.f.}$ .

**R-Code:**  

```R

```

**R-console (output):** 

```R

```

**Conclusion:** From the above experiment we conclude that the application of Sulphur produced a significant decrease in the scale index. There is no indication that highest level of dressing were effective than the lowest levels.

