# Practical #6

##### Practical Title: Association of Attributes

**Experiment:** Show as briefly as possible, whether  $A$ and $B$ are independent, positively associated or negatively associated  in each case:

| (a)  | N=5000   | (A)=2350         | (B)=3100       | (AB)=1600            |
| ---- | -------- | ---------------- | -------------- | -------------------- |
| (b)  | (A)=490  | (AB)=294         | ( $\alpha$ )=570 | ( $\alpha B$ )=380     |
| (c)  | (AB)=256 | ( $\alpha B$ )=768 | ( $A\beta$ )=48  | ( $\alpha \beta$ )=144 |

**AIM:** To show whether two numbers are independent, positively associated or negatively associated .

**Procedure:** 

If $(AB) > (A)(B)/N$, then $A, B$ are positive associated.
If $ (AB)<(A)(B)/N,$ then $A, B$ are negative associated.
If $(AB)=(A)(B),$ then $A,B$ are independent.

**R-Command:** 

```r
rm(list=ls())
N=5000
A=2350
B=3100
AB=1600
q=(A*B)/N
q
if(AB>q)
{
print("positively associated")
}else if(AB<q){
print("negatively associated")
}else{
print("independent")
}
A=490
AB=294
a=570
aB=380
B=aB+AB
B
N=A+a
N
q=(A*B)/N
if(AB>q){
print("positively associated")
}else if(AB<q){
print ("negatively associated")
}else{
print("independent")
}
AB=256
aB=768
Ab=48
ab=144
a=aB+ab
A=AB+Ab
N=A+a
B=AB+aB
q=(A*B)/N
if(AB>q){
print("positvely associated")
}else if(AB<q){
print("negatively associated")
}else{
print("independent")
}
```



**R-Console:**

```R
> rm(list=ls())
> N=5000
> A=2350
> B=3100
> AB=1600
> q=(A*B)/N
> q
[1] 1457
> if(AB>q)
+ {
+ print("positively associated")
+ }else if(AB<q){
+ print("negatively associated")
+ }else{
+ print("independent")
+ }
[1] "positively associated"
> A=490
> AB=294
> a=570
> aB=380
> B=aB+AB
> B
[1] 674
> N=A+a
> N
[1] 1060
> q=(A*B)/N
> if(AB>q){
+ print("positively associated")
+ }else if(AB<q){
+ print ("negatively associated")
+ }else{
+ print("independent")
+ }
[1] "negatively associated"
> AB=256
> aB=768
> Ab=48
> ab=144
> a=aB+ab
> A=AB+Ab
> N=A+a
> B=AB+aB
> q=(A*B)/N
> if(AB>q){
+ print("positvely associated")
+ }else if(AB<q){
+ print("negatively associated")
+ }else{
+ print("independent")
+ }
[1] "independent"
```

**Conclusion:** 

From the above experiment we conclude that, In first case $A$ and $B$ are Positively associated, in second case $A$ and $B $ are negatively associated and in third case $A$ and $B$ are Independent.
