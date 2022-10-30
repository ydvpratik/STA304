# Practical #8

##### Practical Title: Moving Average

**Experiment:** Calculate 5-yearly and 7-yearly moving average of the data given below to obtain trend values and given their graphic representation:

<table>  
  <tr>  
    <th>Year:</th>  
    <th>1</th>  
    <th>2</th>
    <th>3</th>  
    <th>4</th>  
    <th>5</th>
    <th>6</th>  
    <th>7</th>  
    <th>8</th>
    <th>9</th>  
    <th>10</th>  
    <th>11</th>
    <th>12</th>  
    <th>13</th>  
    <th>14</th>  
    <th>15</th>
  </tr>  
  <tr>  
    <td>Values:</td>
    <td>220</td>  
    <td>208</td>  
    <td>156</td>  
    <td>210</td>  
    <td>218</td>  
    <td>240</td>  
    <td>230</td>  
    <td>220</td>  
    <td>228</td>  
    <td>244</td>  
    <td>260</td>  
    <td>254</td>  
    <td>244</td>  
    <td>236</td>  
    <td>250</td>  
  </tr>  
  <tr> 
    <td>Year:</td> 
    <td>16</td>  
    <td>17</td>  
    <td>18</td> 
    <td>19</td>  
    <td>20</td>  
    <td>21</td> 
    <td>22</td>  
    <td>23</td>  
    <td>24</td> 
    <td>25</td>  
    <td>26</td>  
    <td>27</td> 
    <td>28</td>  
    <td>29</td>  
    <td>30</td>  
  </tr>  
  <tr> 
    <td>Values:</td>
    <td>280</td>  
    <td>270</td>  
    <td>260</td> 
    <td>254</td>  
    <td>270</td>  
    <td>292</td> 
    <td>284</td>  
    <td>276</td>  
    <td>270</td> 
    <td>290</td>  
    <td>310</td>  
    <td>300</td> 
    <td>296</td>  
    <td>286</td>  
    <td>312</td>  
  </tr>  
</table>

**Aim:** To calculate 5-yearly and 7-yearly moving average of the given data. Plotting  the graph of trend values.

**Procedure:** To calculate the 5-year moving average, we have to compute the mean of the first 5-year and place it for the $3^{rd}$  year, similarly we compute for $4^{th}$ year and so on. 

To calculate the 7-year moving average, we have to compute the mean of the first 7-year and place it for the $4^{th}$  year, similarly we compute for $5^{th}$ year.

**R-Code:** 

```R
yr=c(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30);
yr2=c(3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28);
yr3=c(4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27);
v1=c(220,208,156,210,218,240,230,220,228,244,260,254,244,236,260,280,270,260,254,270,292,284,276,270,290,310,300,296,286,312);
av5=c();
av7=c()
for (i in 1:26) {
    av5[i]=(v1[i]+v1[i+1]+v1[i+2]+v1[i+3]+v1[i+4])/5;

};
for (i in 1:24) {
    av7[i]=(v1[i]+v1[i+1]+v1[i+2]+v1[i+3]+v1[i+4]+v1[i+5]+v1[i+6])/7;
};
av5;
av7;
plot(yr,v1,"o",lty=1,xlab="year",ylab="annual figures");
lines(yr2,av5,"o",lty=5,col="blue");
lines(yr3,av7,"o",lty=3,col="red");
```

**R-Console:** 

```R
> yr3=c(4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27);
> v1=c(220,208,156,210,218,240,230,220,228,244,260,254,244,236,260,280,270,260,254,270,292,284,276,270,290,310,300,296,286,312);
> av5=c();
> av7=c()
> for (i in 1:26) {
+     av5[i]=(v1[i]+v1[i+1]+v1[i+2]+v1[i+3]+v1[i+4])/5;
+ 
+ };
> for (i in 1:24) {
+     av7[i]=(v1[i]+v1[i+1]+v1[i+2]+v1[i+3]+v1[i+4]+v1[i+5]+v1[i+6])/7;
+ };
> av5;
 [1] 202.4 206.4 210.8 223.6 227.2 232.4 236.4 241.2 246.0 247.6 250.8 254.8
[13] 258.0 261.2 264.8 266.8 269.2 272.0 275.2 278.4 282.4 286.0 289.2 293.2
[25] 296.4 300.8
> av7;
 [1] 211.7143 211.7143 214.5714 227.1429 234.2857 239.4286 240.0000 240.8571
 [9] 246.5714 254.0000 257.7143 257.7143 257.7143 261.4286 269.4286 272.8571
[17] 272.2857 272.2857 276.5714 284.5714 288.8571 289.4286 289.7143 294.8571
> plot(yr,v1,"o",lty=1,xlab="year",ylab="annual figures");
> lines(yr2,av5,"o",lty=5,col="blue");
> lines(yr3,av7,"o",lty=3,col="red");
> 
```

**R-Graphics:**

![image-20220901223248620](C:\Users\Pranav\AppData\Roaming\Typora\typora-user-images\image-20220901223248620.png)

**Conclusion:** From the graph we notice that after thae $6^{th}$ year the trend curve of 5 yearly moving avg. is almost is a straight line. But the graph of 7 yearly moving avg. is a wavelike line. Thus it is quit clear that after  the $6^{th}$ year, data follows regular cycle of length 5 years. Also when the actual data has peaks the seven years moving avg. has depressions.