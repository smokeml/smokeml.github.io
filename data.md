---
layout: default
title: Data
permalink: /data/
---


## Time & No of Paths distribution for two phases
![Two Stage Data](/assets/images/twostage_data.png)

```wrap
! We have constructed a graphic datastructure for both the pointer 
analysis and the path path-condition collection. 

However, when generating this table, we included the time of graph 
construction in the 2nd phase, which is inaccurate. 

This leads to an abnormal data for **Caffe** that even though it 
has no memory leak candidate, the analysis still spent 29s on the 
"2nd Phase". 

We'll make it more clear in the revised version. 
```

*********************************************


## Detailed report classification

We have an app to visualize the bug reports, which will be revealed after the review process.  
![Quality Data](/assets/images/quality_data.png)