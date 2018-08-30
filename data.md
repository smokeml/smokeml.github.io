---
layout: default
title: Data
permalink: /data/
---


## Memory Leak Reports

Thanks to [Github Educate program](https://www.awseducate.com/), we have set up an online report system to host the leak reports together with our manual classification. 

Thanks to [Sourcebrella Inc](https://www.sourcebrella.com/), we borrowed their bug report system to help us speed up the whole process. 
We use their free version for academic use [LINK](https://www.sourcebrella.com/online-showcase) 

The method is to convert all bug reports (SMOKE, Saber, CSA, INFER) to Pinpoint's JSON format and upload them to the server. 

The address is [SMOKE/Saber/CSA/Pinpoint/Infer Reports](http://18.237.84.207:40080/online_report)

Username/pass :  testtest/testtest 

```
Confirmed = True Positive
False Positive = False Positive.

SSU =  SMOKE  
PSA =  PINPOINT  (Pinpoint Static Analyzer) 
CSA =  CSA       (Clang Static Analyzer)
Saber = Saber
Infer = Infer 

```

Note: When collecting the statistics information, we use the default "Cluster" feature provided by Pinpoint. 

Reports are merged if they share the same start points. 



## Time & No of Paths distribution for two phases
![Two Stage Data](/assets/images/twostage_data.png)

```wrap
! We have constructed a graphic data structure for both the pointer 
analysis and the path path-condition collection. 

However, when generating this table, we included the time of graph 
construction in the 2nd phase, which is inaccurate. 

This leads to an abnormal data for **Caffe** that even though it 
has no memory leak candidate, the analysis still spent 29s on the 
"2nd Phase". 

We will make it more evident in the revised version. 
```

*********************************************


## Detailed report classification

We have an app to visualize the bug reports, which will be revealed after the review process.  
![Quality Data](/assets/images/quality_data.png)
