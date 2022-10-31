# Practical #23

##### Practical Topic: Analysis of Variance(ANOVA)

**Experiment:** The given Table shows some of the results of an experiment on the effect of applications of Sulphur in reducing scale disease of potatoes. The object in applying Sulphur is to increase the acidity of the soil since scale does not thrive in very acid soil. In addition to untreated plots which serve as control 3 amounts of dressing are compared 300,600 and 1,200 lbs per acre. Both a spring and fall application of each treatment was seven distinct treatments. The quantity to be analysed is the scale index. This is roughly speaking, the scale index. This is roughly speaking, the percentage of the surface area of the potato that is infected with scab. [F = Fall, S = Spring application, O = Control  ]

​	The numbers 3,6,12 are the amounts of Sulphur in 100 lb. per acer. Analyse the experiment and give your conclusion.

| $F_3$  <br />9 |   $O$<br />12   |  $S_6$ <br />18  | $F_{12}$<br />10 | $S_6$<br />24 | $S_{12}$<br />17 | $S_3$<br />30 |  $F_6$<br />16  |
| :------------: | :-------------: | :--------------: | :--------------: | :-----------: | :--------------: | :-----------: | :-------------: |
|  $O$<br />10   |  $S_3$<br />7   | $F_{12}$<br />4  |  $F_6$<br />10   | $S_3$<br />24 |   $O$<br />24    |  $O$<br />29  |  $S_6$<br />12  |
|  $F_3$<br />9  | $S_{12}$<br />7 |  $F_6$<br />18   |   $O$<br />30    | $F_6$<br />18 | $S_{12}$<br />16 | $F_3$<br />16 | $F_{12}$<br />4 |
|  $S_3$<br />9  |   $O$<br />18   | $S_{12}$<br />17 |  $S_6$<br />19   |  $O$<br />12  | $F_{12}$<br />5  |  $O$<br />26  |  $F_3$ <br />4  |

**Aim:** To analyze the randomized experiment on potato to find effectiveness of application of Sulphur to reduce scale of disease of potato.

**Procedure:** Correction factor is given by; $C.F=\displaystyle \frac{G^2}{N}$  

Total S.S. = $\displaystyle \sum_i\sum_j{y_{ij}}^2-C.F.$ ,  Treatment S.S = $\displaystyle\sum\frac{T_i^2}{r_t}-C.F$ , Error S.S  = $Total ~~ S.S-Treatment ~~ S.S$ and  M.S.S= $\displaystyle \frac{S.S.}{d.f.}$ .

**R-Code:**  

```R

rm(list=ls())
O1=c(12,10,24,29)
O2=c(30,18,12,26)
F3=c(9,9,16,4)
S3=c(30,7,21,9)
F6=c(16,10,18,18)
S6=c(18,24,12,19)
F12=c(10,4,4,5)
S12=c(17,7,16,17)
N=32
d=data.frame(O1,O2,F3,S3,F6,S6,F12,S12);d
F=c(O1,O2,F3,S3,F6,S6,F12,S12)
total_O=sum(O1,O2)
total_F3=sum(F3)
total_S3=sum(S3)
total_F6=sum(F6)
total_S6=sum(S6)
total_F12=sum(F12)
total_S12=sum(S12)
D=c(total_F3,total_S3,total_F6,total_S6,total_F12,total_S12)
X=c(total_F3,total_F6,total_F12)
Y=c(total_S3,total_S6,total_S12)
O=c(O1,O2)
mean_O=total_O/length(O);mean_O
mean_F3=total_F3/length(F3);mean_F3
mean_S3=total_S3/length(S3);mean_S3
mean_F6=total_F6/length(F6);mean_F6
mean_S6=total_S6/length(S6);mean_S6
mean_F12=total_F12/length(F12);mean_F12
mean_S12=total_S12/length(S12);mean_S12
G=sum(total_O,total_F3,total_S3,total_F6,total_S6,total_F12,total_S12);G
CF=(G^2)/N;CF
TSS=(sum((F^2)))-CF;TSS
tSS=((total_O^2)/length(O))+((sum(D^2))/length(F3))-CF;tSS
ESS=TSS-tSS;ESS
source_of_variation=c('Treatments','Error')
SS=c(tSS,ESS)
total_SS=sum(SS);total_SS
df=c(6,25)
total_df=sum(df);total_df
MSS=SS/df;MSS
VR=MSS[1]/MSS[2];VR
if(VR>qf(0.95,df[1],df[2]))
{
  paste0("V.R. is significant at 5% level")
}else
{
  paste0("V.R. is not significant at 5% level")
}
d1=data.frame(source_of_variation,SS,df,MSS);d1
d2=sum(d1['SS']);d2
d3=sum(d1['df']);d3

avrage_effect_of_sulphur=3*(total_O)-sum(D);avrage_effect_of_sulphur
contribution_to_SS_sulpher=avrage_effect_of_sulphur^2/96
fal_versus_spring_application=sum(X)-sum(Y);fal_versus_spring_application
contributor_to_SS_fall_spr=(fal_versus_spring_application^2/24);contributor_to_SS_fall_spr
sourc_of_variation=c('Treatments','control_vs_sulphur','fal_versus_spring_application','comparison_among_levels')
d_f=c(6,1,1,4)
S_S=c(tSS,contribution_to_SS_sulpher,contributor_to_SS_fall_spr,tSS-contribution_to_SS_sulpher-contributor_to_SS_fall_spr);S_S
M_S_S=S_S/d_f;M_S_S
V_R=M_S_S/MSS[2];V_R
f_tab_5=qf(0.95,d_f,rep(df[2],4));f_tab_5 
f_tab_1=qf(0.99,d_f,rep(df[2],4));f_tab_1
data=data.frame(sourc_of_variation,d_f,S_S,M_S_S,V_R,f_tab_5,f_tab_1);data
paste0("We see that at 5% sign. control v/s sulpher and fall v/s spring but comperision among level is not significant")
paste0("at 1% significant level we see that all are not significant")
```

**R-console (output):** 

```R

> rm(list=ls())
> O1=c(12,10,24,29)
> O2=c(30,18,12,26)
> F3=c(9,9,16,4)
> S3=c(30,7,21,9)
> F6=c(16,10,18,18)
> S6=c(18,24,12,19)
> F12=c(10,4,4,5)
> S12=c(17,7,16,17)
> N=32
> d=data.frame(O1,O2,F3,S3,F6,S6,F12,S12);d
  O1 O2 F3 S3 F6 S6 F12 S12
1 12 30  9 30 16 18  10  17
2 10 18  9  7 10 24   4   7
3 24 12 16 21 18 12   4  16
4 29 26  4  9 18 19   5  17
> F=c(O1,O2,F3,S3,F6,S6,F12,S12)
> total_O=sum(O1,O2)
> total_F3=sum(F3)
> total_S3=sum(S3)
> total_F6=sum(F6)
> total_S6=sum(S6)
> total_F12=sum(F12)
> total_S12=sum(S12)
> D=c(total_F3,total_S3,total_F6,total_S6,total_F12,total_S12)
> X=c(total_F3,total_F6,total_F12)
> Y=c(total_S3,total_S6,total_S12)
> O=c(O1,O2)
> mean_O=total_O/length(O);mean_O
[1] 20.125
> mean_F3=total_F3/length(F3);mean_F3
[1] 9.5
> mean_S3=total_S3/length(S3);mean_S3
[1] 16.75
> mean_F6=total_F6/length(F6);mean_F6
[1] 15.5
> mean_S6=total_S6/length(S6);mean_S6
[1] 18.25
> mean_F12=total_F12/length(F12);mean_F12
[1] 5.75
> mean_S12=total_S12/length(S12);mean_S12
[1] 14.25
> G=sum(total_O,total_F3,total_S3,total_F6,total_S6,total_F12,total_S12);G
[1] 481
> CF=(G^2)/N;CF
[1] 7230.031
> TSS=(sum((F^2)))-CF;TSS
[1] 1828.969
> tSS=((total_O^2)/length(O))+((sum(D^2))/length(F3))-CF;tSS
[1] 731.0938
> ESS=TSS-tSS;ESS
[1] 1097.875
> source_of_variation=c('Treatments','Error')
> SS=c(tSS,ESS)
> total_SS=sum(SS);total_SS
[1] 1828.969
> df=c(6,25)
> total_df=sum(df);total_df
[1] 31
> MSS=SS/df;MSS
[1] 121.849  43.915
> VR=MSS[1]/MSS[2];VR
[1] 2.774655
> if(VR>qf(0.95,df[1],df[2]))
+ {
+   paste0("V.R. is significant at 5% level")
+ }else
+ {
+   paste0("V.R. is not significant at 5% level")
+ }
[1] "V.R. is significant at 5% level"
> d1=data.frame(source_of_variation,SS,df,MSS);d1
  source_of_variation        SS df     MSS
1          Treatments  731.0938  6 121.849
2               Error 1097.8750 25  43.915
> d2=sum(d1['SS']);d2
[1] 1828.969
> d3=sum(d1['df']);d3
[1] 31
> 
> avrage_effect_of_sulphur=3*(total_O)-sum(D);avrage_effect_of_sulphur
[1] 163
> contribution_to_SS_sulpher=avrage_effect_of_sulphur^2/96
> fal_versus_spring_application=sum(X)-sum(Y);fal_versus_spring_application
[1] -74
> contributor_to_SS_fall_spr=(fal_versus_spring_application^2/24);contributor_to_SS_fall_spr
[1] 228.1667
> sourc_of_variation=c('Treatments','control_vs_sulphur','fal_versus_spring_application','comparison_among_levels')
> d_f=c(6,1,1,4)
> S_S=c(tSS,contribution_to_SS_sulpher,contributor_to_SS_fall_spr,tSS-contribution_to_SS_sulpher-contributor_to_SS_fall_spr);S_S
[1] 731.0938 276.7604 228.1667 226.1667
> M_S_S=S_S/d_f;M_S_S
[1] 121.84896 276.76042 228.16667  56.54167
> V_R=M_S_S/MSS[2];V_R
[1] 2.774655 6.302184 5.195643 1.287525
> f_tab_5=qf(0.95,d_f,rep(df[2],4));f_tab_5 
[1] 2.490410 4.241699 4.241699 2.758710
> f_tab_1=qf(0.99,d_f,rep(df[2],4));f_tab_1
[1] 3.627174 7.769798 7.769798 4.177420
> data=data.frame(sourc_of_variation,d_f,S_S,M_S_S,V_R,f_tab_5,f_tab_1);data
             sourc_of_variation d_f      S_S     M_S_S      V_R  f_tab_5  f_tab_1
1                    Treatments   6 731.0938 121.84896 2.774655 2.490410 3.627174
2            control_vs_sulphur   1 276.7604 276.76042 6.302184 4.241699 7.769798
3 fal_versus_spring_application   1 228.1667 228.16667 5.195643 4.241699 7.769798
4       comparison_among_levels   4 226.1667  56.54167 1.287525 2.758710 4.177420
> paste0("We see that at 5% sign. control v/s sulpher and fall v/s spring but comperision among level is not significant")
[1] "We see that at 5% sign. control v/s sulpher and fall v/s spring but comperision among level is not significant"
> paste0("at 1% significant level we see that all are not significant")
[1] "at 1% significant level we see that all are not significant"

```

**Conclusion:** From the above experiment we conclude that the application of Sulphur produced a significant decrease in the scale index. There is no indication that highest level of dressing were effective than the lowest levels.

