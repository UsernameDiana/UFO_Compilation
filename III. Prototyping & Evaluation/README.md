# III. Prototyping & Evaluation, Documentation

---
- **Title**: Prototyping & Evaluation, Documentation
- **Author**: Andreas Styltsvig (cph-as283) & Cherry Rose Semeña(cph-cs241)
- **Date**: 11/10/2018
- **Assignment reference**: https://datsoftlyngby.github.io/soft2018fall/UFO/03-Prototyping_and_Evaluation.html
---
> ## Exercise 1 

There are digital ocean droplets running in different parts of the world. The are all set up to respond to ping. Their addresses are the following:

- http://139.59.132.185:8080
- http://192.81.216.124:8080
- http://128.199.180.131:8080



## 1. Plan
*Formulate a hypothesis/problem statement about behavior of response times of these three servers.* 

The servers is located in different places in the world and we assume that the distance from the request-source to the location of the server will determine the response latency very visible.

Thence our hypothesis is : 

> "The distance to the location of the server will determine the response latency in MiliSeconds(MS), so we assume that the further distance is, the latency will increase."




## 2. Setup
*Plan an experiment, which measures response times of these three servers.*

We have to gain 3 given facts about the servers:

	1. The location of the ip
	2. The distance between the server and our request-source
	3. The response time for the server

1. **The locations**

There are many places where we can get information about the location of the ip. As start we will be using a iplocation lookup provider (https://www.iplocation.net/).

The results are listed here: 


```
IP: 139.59.132.185
Location: Germany
``` 
https://i.gyazo.com/f4e2615c4960c316b86c17722058de6a.png
```
IP: 192.81.216.124
Location: USA
```
https://gyazo.com/5a36cdb7606e492645bc1847eacd448e.png

```
IP: 128.199.180.131
Location: Singapore
```
https://gyazo.com/f336814a849e51cddc23cf47a9e5b811.png


2. **The distance between the server and our request-source**

We will test from 3 different locations.

Location 1 : The school located in CPH-business, Lyngby, Denmark
Location 2 : Home located in Vanløse, Copenhagen, Denmark
Location 3 : A digital droplet located in ??

**Location 1** 
```
IP: 5.179.80.204
Location: Denmark (Lyngby)
```

**Location 2** 
```
IP: x.x.x.x.x
Location: Denmark (Copenhagen)
```

**Location 3** 
```
IP: 104.248.238.12
Location: Usa (New Jersey)
```

Distance between locations using a distance calculator 
https://www.distancecalculator.net/

```
**Location 1**
- Lyngby -> Germany (Frankfurt am main) 679 km.
- Lyngby -> USA (North Bergen) 6179.90 km.
- Lyngby -> Germany (Singapore) 9977.28 km.

**Location 2**
- Copenhagen -> Germany (Frankfurt am main) 671 km.
- Copenhagen -> USA (North Bergen) 6188.02 km.
- Copenhagen -> Germany (Singapore) 9972.99 km.

**Location 3**
- New Jersey -> Germany (Frankfurt am main) 6282.38 km.
- New Jersey -> USA (North Bergen) 89.48 km.
- New Jersey -> Germany (Singapore) 15424.19 km.
``` 

3. **The response time for the server**

We have to measure the response time from the server, and collect the data. So we need to setup an experiment that will provide data about latency between location and the server.

**To do that, we would do something like this:**
1. Coding a bash script that pings the server and measure response time
2. Store the result in a txt file
3. Visualize the result


So I spent some moment to make a bash script that pings the server and save the result into a text file.

**pingBot.sh**
```sh

echo "Pinging Germany"
ping 139.59.132.185 -n 10 -l 32 >> ping_germany.txt
echo "Pinging USA"
ping 192.81.216.124 -n 10 -l 32 >> ping_USA.txt
echo "Pinging Singapore"
ping 128.199.180.131 -n 10 -l 32 >> ping_singapore.txt
echo "Finish & exiting"
```




## 3. Execute
*Execute the experiment, which measures response times of these three servers.*

Do following steps to start the `pingBot.sh`

1. Create a new file, and call it `pingBot.sh`
It should contains following code: 
```
echo "Pinging Germany"
ping 139.59.132.185 -n 10 -l 32 >> ping_germany.txt
echo "Pinging USA"
ping 192.81.216.124 -n 10 -l 32 >> ping_USA.txt
echo "Pinging Singapore"
ping 128.199.180.131 -n 10 -l 32 >> ping_singapore.txt
echo "Finish & exiting"
```
2. Open a cmd terminal and execute the program by calling `sh pingBot.sh`
3. You should now see 3 new files in same directory you have `pingBot.sh`, these 3 files contains result from pinging.
4. Use the result to whatever you want (Analyze, visualization, discussion)
5. Profit




## 4. Evaluate
*Evaluate your experiment and interpret the measurements and results.*


### Results

### **From Lyngby**

**Germany** 
```txt

Pinging 139.59.132.185 with 32 bytes of data:
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52
Reply from 139.59.132.185: bytes=32 time=15ms TTL=52
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52
Reply from 139.59.132.185: bytes=32 time=15ms TTL=52
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52
Reply from 139.59.132.185: bytes=32 time=16ms TTL=52

Ping statistics for 139.59.132.185:
    Packets: Sent = 10, Received = 10, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 15ms, Maximum = 16ms, Average = 15ms

```

**USA**
```

Pinging 192.81.216.124 with 32 bytes of data:
Reply from 192.81.216.124: bytes=32 time=88ms TTL=54
Reply from 192.81.216.124: bytes=32 time=88ms TTL=54
Reply from 192.81.216.124: bytes=32 time=88ms TTL=54
Reply from 192.81.216.124: bytes=32 time=87ms TTL=54
Reply from 192.81.216.124: bytes=32 time=87ms TTL=54
Reply from 192.81.216.124: bytes=32 time=92ms TTL=54
Reply from 192.81.216.124: bytes=32 time=87ms TTL=54
Reply from 192.81.216.124: bytes=32 time=88ms TTL=54
Reply from 192.81.216.124: bytes=32 time=87ms TTL=54
Reply from 192.81.216.124: bytes=32 time=93ms TTL=54

Ping statistics for 192.81.216.124:
    Packets: Sent = 10, Received = 10, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 87ms, Maximum = 93ms, Average = 88ms

```

**Singapore**
```

Pinging 128.199.180.131 with 32 bytes of data:
Reply from 128.199.180.131: bytes=32 time=198ms TTL=51
Reply from 128.199.180.131: bytes=32 time=198ms TTL=51
Reply from 128.199.180.131: bytes=32 time=197ms TTL=51
Reply from 128.199.180.131: bytes=32 time=200ms TTL=51
Reply from 128.199.180.131: bytes=32 time=198ms TTL=51
Reply from 128.199.180.131: bytes=32 time=197ms TTL=51
Reply from 128.199.180.131: bytes=32 time=197ms TTL=51
Reply from 128.199.180.131: bytes=32 time=198ms TTL=51
Reply from 128.199.180.131: bytes=32 time=198ms TTL=51
Reply from 128.199.180.131: bytes=32 time=198ms TTL=51

Ping statistics for 128.199.180.131:
    Packets: Sent = 10, Received = 10, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 197ms, Maximum = 200ms, Average = 197ms

```
---


### **From my home in Copenhagen**

**Germany**
```txt

Pinging 139.59.132.185 with 32 bytes of data:
Reply from 139.59.132.185: bytes=32 time=25ms TTL=48
Reply from 139.59.132.185: bytes=32 time=24ms TTL=48
Reply from 139.59.132.185: bytes=32 time=32ms TTL=48
Reply from 139.59.132.185: bytes=32 time=23ms TTL=48
Reply from 139.59.132.185: bytes=32 time=24ms TTL=48
Reply from 139.59.132.185: bytes=32 time=30ms TTL=48
Reply from 139.59.132.185: bytes=32 time=28ms TTL=48
Reply from 139.59.132.185: bytes=32 time=30ms TTL=48
Reply from 139.59.132.185: bytes=32 time=34ms TTL=48
Reply from 139.59.132.185: bytes=32 time=26ms TTL=48

Ping statistics for 139.59.132.185:
    Packets: Sent = 10, Received = 10, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 23ms, Maximum = 34ms, Average = 27ms


```

**USA**
```txt

Pinging 192.81.216.124 with 32 bytes of data:
Reply from 192.81.216.124: bytes=32 time=97ms TTL=53
Reply from 192.81.216.124: bytes=32 time=95ms TTL=53
Reply from 192.81.216.124: bytes=32 time=95ms TTL=53
Reply from 192.81.216.124: bytes=32 time=94ms TTL=53
Reply from 192.81.216.124: bytes=32 time=96ms TTL=53
Reply from 192.81.216.124: bytes=32 time=97ms TTL=53
Reply from 192.81.216.124: bytes=32 time=94ms TTL=53
Reply from 192.81.216.124: bytes=32 time=99ms TTL=53
Reply from 192.81.216.124: bytes=32 time=96ms TTL=53
Reply from 192.81.216.124: bytes=32 time=99ms TTL=53

Ping statistics for 192.81.216.124:
    Packets: Sent = 10, Received = 10, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 94ms, Maximum = 99ms, Average = 96ms

```

**Singapore**
```txt

Pinging 128.199.180.131 with 32 bytes of data:
Reply from 128.199.180.131: bytes=32 time=188ms TTL=48
Reply from 128.199.180.131: bytes=32 time=188ms TTL=48
Reply from 128.199.180.131: bytes=32 time=186ms TTL=48
Reply from 128.199.180.131: bytes=32 time=190ms TTL=48
Reply from 128.199.180.131: bytes=32 time=187ms TTL=48
Reply from 128.199.180.131: bytes=32 time=193ms TTL=48
Reply from 128.199.180.131: bytes=32 time=193ms TTL=48
Reply from 128.199.180.131: bytes=32 time=191ms TTL=48
Reply from 128.199.180.131: bytes=32 time=189ms TTL=48
Reply from 128.199.180.131: bytes=32 time=189ms TTL=48

Ping statistics for 128.199.180.131:
    Packets: Sent = 10, Received = 10, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 186ms, Maximum = 193ms, Average = 189ms

```
---


### **From a digital droplet in New Jersay USA**

**Germany**

![alt text](./images/ping_germany.png)

**USA**

![alt text](./images/ping_usa.png)

**Singapore**

![alt text](./images/ping_singapore.png)
---


### Summary

#### Average latency in MS

|  | Germany | Usa | Singapore |
| ------------- | ------------- | ------------- | ------------- | 
| Location 1 (Lyngby)  | 15ms  | 88ms  | 197ms  |
| Location 2 (Copenhagen) | 27ms | 96ms  | 189ms  |
| Location 3 (Digital droplet in USA) | 83ms  | 2ms  | 268ms |

![alt text](./images/chart_latency.png)

#### Distance in KM

|  | Germany | Usa | Singapore |
| ------------- | ------------- | ------------- |  ------------- | 
| Location 1 (Lyngby)  | 679km  | 6179km  | 9977km  |
| Location 2 (Copenhagen) | 679km | 6188km  | 9972km  |
| Location 3 (Digital droplet in USA) | 6282km  | 89km  | 15424km |


![alt text](./images/chart_distance.png)


## 4.1 Analyze and Conclusion

The data is now collected and presented.

As we can monitor, that the distacne between the host and server have a heavily influence on latency.

As per example showed here:

Location 1 -> Server in Singapore, you will have reponse time on 197 ms while location 1 -> In Germany, you will have response time on 15 ms. And the distance is 9977 km to Singapore while you have 679 km to Germany. 

The scatter plotter here shows the plots where distance is labelled in x - axis and latency labelled in y axis. You will see a trendline for latency with r^2 value on 0.90. You will use r^2 as a statistical measurement of how close the data are to the fitted regression line.

Citation from www.blog.minitab.com

```
The definition of R-squared is fairly straight-forward; it is the percentage of the response variable variation that is explained by a linear model. Or:

R-squared = Explained variation / Total variation

R-squared is always between 0 and 100%:

0% indicates that the model explains none of the variability of the response data around its mean.
100% indicates that the model explains all the variability of the response data around its mean.
In general, the higher the R-squared, the better the model fits your data. 
```

![alt text](./images/trendline.png)

So with the r^2 result, you can say that the hypothesis on this case is deviant by 0,1 r^2. So we can conclude that our hypothesis is close to the absolute truth.





