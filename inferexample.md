---
layout: default
title: InferExample
permalink: /inferexample/
---

An example code that contains no memory leak. 


```
#include<cstdio>
#include<cstdlib>
#include<vector>

using namespace std;

int main(){

    char *p = (char *)malloc(1);
    vector<char *> v;
    v.push_back(p);
    free(v[0]);  // no leak
  
    printf("test %s", p);
    return 1;
}


```

Infer reported "p is leaked". 
Console output: 

```
Found 1 source file to analyze in /home/XXXX/test_infer/infer-out
Starting analysis...

legend:
  "F" analyzing a file
  "." analyzing a procedure

F.
Found 1 issue

global2.cpp:16: error: MEMORY_LEAK
  memory dynamically allocated by call to `malloc()` at line 9, column 20 is not reachable after line 16, column 1.
  24.       return 1;
  25.   
  26. > }


Summary of the reports

  MEMORY_LEAK: 1
```