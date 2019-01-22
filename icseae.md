---
layout: default
title: ICSE 2019 Artifact Evaluation for SMOKE
permalink: /icseae/
---




## Preliminaries 
SMOKE is built on LLVM 3.6. It analyzes the Bitcode files (.bc files) of software projects to check vulnerabilities. A Bitcode file is a kind of intermediate representation of the source code. We have prepared all Bitcode files of 29 projects for evaluation.

## Evaluation Host

We prepared a ubuntu server for the artifact evaluation. Reviewers can access the server via ssh (the password is given in the INSTALL file):

``ssh icse2019ae@chcpu12h.cse.ust.hk``

NOTE: when running large benchmark programs (>0.5MLoC), the computation resource in the server may be used up if multiple users use the server at the same time. Thus, we recommend running small benchmark programs to verify our idea.

In the server, we have installed all necessary binaries for evaluation:


* **pp-smoke** the script to run SMOKE
* **pp-pinpoint** the script to run PINPOINT
* **saber** the binary of saber
* **pp-capture** our wrapper of clang static analyzer
* **infer** the facebook infer analyzer

In the home directory, there are several folders, including three groups of benchmarks and other folders:

* **bench36** The LLVM Bitcode (ver 3.6) files for each project (29 in total). 
* **bench40** The LLVM Bitcode (ver 4.0) files for each project (29 in total). Saber uses LLVM Bitcode files of version 4.0. 
* **srcs** Source code of the Tmux project. CSA and Facebook Infer relies on the presence of the compilation database. 
* **bin** Bin contains links to analyzers.
* **pinpoint** where Pinpoint package is installed
* **installs** where facebook infer is installed

## All results:

Since we have a large set of benchmarks (29 projects) and five different tools to evaluate (SMOKE/Pinpoint/Saber/CSA/Infer). It takes a significantly large amount of time to evaluate and to collect the results. To better replicate the results within limited evaluation time, we have converted all reports to Pinpoint bug report format and made the reports and our inspection results available on the bug reporting system (Pinpoint Report System). 
Here is how to access them: 

The address is [SMOKE/Saber/CSA/Pinpoint/Infer Reports](http://ec2-54-185-211-230.us-west-2.compute.amazonaws.com:40080/online_report)

Username/pass :  testtest/testtest 

Mapping:
```
Confirmed = True Positive
False Positive = False Positive.

SSU =  SMOKE  
PSA =  PINPOINT  (Pinpoint Static Analyzer) 
CSA =  CSA       (Clang Static Analyzer)
Saber = Saber
Infer = Infer 

```

Note: When collecting the statistics information, we use the default "Cluster" feature provided by Pinpoint. Reports are merged if they share the same root cause. 

## Inputs


For readers who are interested in how to generate Bitcode files and compilation databases, please refer to [PP-Capture](/producebc)


To evaluate SMOKE and PINPOINT, we need to know the location of the Bitcode files of version LLVM3.6. The Bitcode file for project **[Proj Name]** is located at:

```/home/icse2019ae/bench36/[Proj Name]/```

To evaluate Saber, we need to know the location of the Bitcode files of version LLVM4.0. The Bitcode file for project **[Proj Name]** is located at:

```/home/icse2019ae/bench40/[Proj Name]/```

For Infer and CSA, we need to know the **[Source Dir]** for a project **[Proj Name]**, which is specified in the following table:

! /home/fangang and /bigdata/fangang are accessible for user icse2019ae. 


| **[Proj Name]**     | **[Source Dir]** (a path that contains .piggy folder)                                               |
|-------------|---------------------------------------------------------------------------------------------|
| 164.gzip    | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/164.gzip/src</sub>            |
| 175.vpr     | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/175.vpr/src</sub>             |
| 176.gcc     | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/176.gcc/src</sub>             |
| 181.mcf     | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/181.mcf/src</sub>             |
| 186.crafty  | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/186.crafty/src</sub>          |
| 197.parser  | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/197.parser/src</sub>          |
| 252.eon     | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/252.eon/src</sub>             |
| 253.perlbmk | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/253.perlbmk/src</sub>         |
| 254.gap     | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/254.gap/src</sub>             |
| 255.vortex  | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/255.vortex/src</sub>          |
| 256.bzip2   | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/256.bzip2/src</sub>           |
| 300.twolf   | <sub>/home/fangang/cases/researchbench/spec2000/benchspec/CINT2000/300.twolf/src</sub>           |
| bftpd       | <sub>/home/fangang/cases/researchbench/bftpd/bftpd</sub>                                         |
| htop        | <sub>/home/fangang/cases/researchbench/htop/</sub>                                               |
| caffe       | <sub>/home/fangang/cases/researchbench/caffe/build</sub>                                         |
| memcached   | <sub>/home/fangang/cases/researchbench/memcached/memcached-master</sub>                          |
| lame        | <sub>/bigdata/fangang/cases/lame/lame-3.100</sub>                                                |
| zlib        | <sub>/home/fangang/cases/researchbench/zlib/zlib</sub>                                           |
| tmux        | <sub>/bigdata/fangang/cases/tmux/tmux-2.5</sub>                                                  |
| httpd       | <sub>/home/fangang/cases/researchbench/apache2/httpd-2.4.29</sub>                                |
| openssl     | <sub>/home/fangang/cases/researchbench/openssl</sub>                                             |
| ffmpeg      | <sub>/home/fangang/benchmarks/FFmpeg/buildssu</sub>                                              |
| godot       | <sub>/bigdata/fangang/cases/superlarge/godot/godot</sub>                                         |
| mysql       | <sub>/home/fangang/cases/researchbench/mysql/mysql-server-mysql-5.5.51/build</sub>               |
| v8          | <sub>/home/fangang/cases/researchbench/v8/v8</sub>                                               |
| skia        | <sub>/home/fangang/cases/superlarge/skia/skia-master</sub>                                       |
| blender     | <sub>/bigdata/fangang/cases/superlarge/blender/blender</sub>                                     |
| wine        | <sub>/bigdata/fangang/cases/superlarge/wine/wine/build</sub>                                     |
| firefox     | <sub>/bigdata/fangang/cases/superlarge/firefox/src/mozilla-unified/obj-x86_64-pc-linux-gnu</sub> |



*********************************************

## Artifact Evaluation Steps

We use [Tmux](https://github.com/tmux/tmux) as an example to illustrate the evaluation process. To evaluate a project, we need to run five tools to collect their running time and bug reports. We manually inspect the bug reports to classify them into **False Positives** and **True Positives**. 

Note that the analysis time can be slightly different from the time reported in the paper. It is affected by the configurations of the running machine and the workload of that machine when running the analysis. 

### SMOKE

Commands: 

```bash
pp-smoke  -report=tmux_smoke.json bench36/tmux/tmux.bc

```

Program output:
```bash
icse2019ae@ubuntu:~$ pp-smoke  -report=tmux_smoke.json bench36/tmux/tmux.bc
=== Glancing Mode : A quick glance of the project, not deep but fast ===

                                       Code Metrics
------------------------------------------------------------------------------------------
Total Number of Functions: 1483
         Number of Implemented Functions: 1293
         Number of External Functions: 190
         External Functions Ratio: 12.81%
Instruction Count: 138155 (Avg: 106.85 per function)
Function With Most Instructions: 1480 (Function: window_copy_command)
Average Cyclomatic Complexity: 7.49
Max Cyclomatic Complexity: 151 (Function: window_copy_command)
------------------------------------------------------------------------------------------

                                    Analyzer Execution
------------------------------------------------------------------------------------------
Kept function size 542
VFG_Slicing Time:       22296us
Code preprocessing ........Done!
Constructing call graph ........Done!
Before CDG Time:        1303793us
CDG-Construction Time:  23382us
CDG-Construction Memory:        0KB
DomTreePass Construction Time:  157502us
DomTreePass Construction Memory:        0KB
[Falcon] [################################################################################] 100%
[SPEG] [################################################################################] 100%
SEG-Building Time:      2082713us
SEG-Building Memory:    245M 360KB
SVFG-Global-Building Time:      2341851us
SVFG-Global-Building Memory:    347M 144KB
SVFG-Building Time:     2360265us
SVFG-Building Memory:   347M 144KB
[PSA Checking] [################################################################################] 100%
PPMaster Time Time:     5847us


SSUMemoryLeakChecker Find Candidate Traces Time Time:   25822us
Peak Memory:    1G 565M 784KB


SSUMemoryLeakChecker Post Verification Time Time:       1267382us
Peak Memory:    1G 573M 236KB
[SSU Checking] [################################################################################] 100%

SSUMemoryLeakChecker Time Time:         1293500us
Peak Memory:    1G 573M 236KB

Parallel Scheduler Time Time:   1299422us
------------------------------------------------------------------------------------------


                             Bug reports summary per checker:
------------------------------------------------------------------------------------------
Checker Name                                          Total bugs valid/qualified/found
------------------------------------------------------------------------------------------
SSU Memory Leak Checker                               13/13/19


                             Bug reports summary per bug type
------------------------------------------------------------------------------------------
Bug type                                              Number of reports
------------------------------------------------------------------------------------------
Memory Leak : CWE-401                                 13


Total Time:     7516350us
Peak Memory:    1G 573M 236KB


```

The report file, (You can refer to [ReportFileFormat](/assets/pdfs/bugreport.pdf) for the format of this report file):

[tmux_smoke.json](/assets/text/tmux_smoke.json) 

Also, you can visit the following url for a visualized bug report (Username/pass :  testtest/testtest ):
[tmux-smoke-pinpoint-report](http://ec2-54-185-211-230.us-west-2.compute.amazonaws.com:40080/online_report/#5abc934afc7ce6d46bf202df)

It takes several 7516350us (**7.52 seconds**) for analyzing tmux.bc. After it finished, you will see the time and memory usage on the screen. SMOKE reports 19 bugs in total and marks 13 of them as valid. Those six invalid reports are identified in the **"path-sensitive verification"** phase we described in the paper. 

In SMOKE, we treat different reports of the same root cause as one. So that we report nine memory leak reports in the paper and two of them are false positives. 

### Saber
Commands:

```bash
time saber -leak bench40/tmux/tmux.bc

```

Output
```bash
AvgIndOutDeg        3
MaxIndInDeg         896
MaxIndOutDeg        225
#######################################################
         PartialLeak : memory allocation at : (ln: 70 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/imsg.c)
                 conditional free path:
                  --> (ln: 70 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/imsg.c)
                  --> (ln: 74 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/imsg.c)
                  --> (ln: 82 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/imsg.c)

         PartialLeak : memory allocation at : (ln: 145 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/imsg.c)
                 conditional free path:
                  --> (ln: 27 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/freezero.c)
                  --> (ln: 68 fl: /bigdata/fangang/cases/tmux/tmux-2.5/proc.c)
                  --> (ln: 72 fl: /bigdata/fangang/cases/tmux/tmux-2.5/proc.c)

         PartialLeak : memory allocation at : (ln: 215 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/vis.c)
                 conditional free path:
                  --> (ln: 101 fl: /bigdata/fangang/cases/tmux/tmux-2.5/log.c)
                  --> (ln: 105 fl: /bigdata/fangang/cases/tmux/tmux-2.5/log.c)
                  --> (ln: 216 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/vis.c)
                  --> (ln: 221 fl: /bigdata/fangang/cases/tmux/tmux-2.5/compat/vis.c)

         PartialLeak : memory allocation at : (ln: 342 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                 conditional free path:
                  --> (ln: 275 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 402 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 404 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 410 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 412 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 414 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 425 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)

         PartialLeak : memory allocation at : (ln: 236 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                 conditional free path:
                  --> (ln: 1510 fl: /bigdata/fangang/cases/tmux/tmux-2.5/server-client.c)
                  --> (ln: 239 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 240 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)
                  --> (ln: 275 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)

         PartialLeak : memory allocation at : (ln: 1517 fl: /bigdata/fangang/cases/tmux/tmux-2.5/server-client.c)
                 conditional free path:
                  --> (ln: 275 fl: /bigdata/fangang/cases/tmux/tmux-2.5/cmd.c)


real    1m6.410s
user    1m3.516s
sys     0m2.892s

```

From the output screen, you can find that Saber takes around **63.5** seconds for analyzing Tmux. 
It reports six memory leaks and all of them are false positives after a closely inspection. 

For a visualized bug report:
[tmux-saber-pinpoint-report](http://ec2-54-185-211-230.us-west-2.compute.amazonaws.com:40080/online_report/#5a71a071fc7ce622fb0f1173)


### Clang Static Analyzer (CSA)

Commands. We run the CSA in single thread mode:

```bash

cd ~/srcs/tmux/tmux-2.5 
time ~/pinpoint/bin/pp-capture --run-csa --thread-pool=1 -- make -j4

```

Output:

```bash
icse2019ae@ubuntu:~/srcs/tmux/tmux-2.5$ time ~/pinpoint/bin/pp-capture --run-csa --thread-pool=1 -- make -j4
Current pp-capture version: 01.04.374
Caching compile commands ...

Running symbolic executor ...
Analyzed [############################################################] 100%

Total files: 136, analyzed 131 files, found 40 bugs(redundantly).

real    2m49.957s
user    2m44.072s
sys     0m4.868s

```


The report file is located in .piggy/reports/csa_report0.json, for the format of this report file please refer to [ReportFileFormat](/assets/pdfs/bugreport.pdf). 

The report file: [csa_report0.json](/assets/text/csa_report0.json) 

CSA reports no memory leak for Tmux. (Note that there are two "Logic Error" bugs reported by the "cplusplus.NewDeleteLeaks" checker. They are not memory leaks). 

For a visualized report (this report contains other types of bugs, no memory leak has been reported):
[tmux-csa-pinpoint-report](http://ec2-54-185-211-230.us-west-2.compute.amazonaws.com:40080/online_report/#5b72c9c9fc7ce67ad38f2720)


### Facebook Infer

Commands. Infer can take a compilation database file as input. 

```bash
cd ~/srcs/tmux/tmux-2.5
time infer -a infer -j 1 --biabduction-only --keep-going --compilation-database .piggy/compile_commands.json

```

Output:
```bash

icse2019ae@ubuntu:~$ cd ~/srcs/tmux/tmux-2.5
icse2019ae@ubuntu:~/srcs/tmux/tmux-2.5$ time infer -a infer -j 1 --biabduction-only --keep-going --compilation-database .piggy/compile_commands.json
Capturing using compilation database...
Starting translating 136 files
....................cmd-if-shell.c:150:7: ERROR translating statement 'InitListExpr'
cmd-if-shell.c:150:7: ERROR translating statement 'CompoundLiteralExpr'
cmd-if-shell.c:150:7: ERROR translating statement 'ParenExpr'
cmd-if-shell.c:150:7: ERROR translating statement 'MemberExpr'
cmd-if-shell.c:150:7: ERROR translating statement 'ParenExpr'

.................
Found 136 source files to analyze in /home/icse2019ae/srcs/tmux/tmux-2.5/infer-out
Starting analysis...

legend:
  "F" analyzing a file
  "." analyzing a procedure

F...........F........F..................................................................................................................................................
..FF....F.....
Analysis finished in 9min5ss

Found 76 issues
key-bindings.c:27: error: NULL_DEREFERENCE
  pointer `tmp` last assigned on line 27 could be null and is dereferenced at line 27, column 1.
  25.   #include "tmux.h"
  26.
  27. > RB_GENERATE(key_bindings, key_binding, entry, key_bindings_cmp);
  28.   RB_GENERATE(key_tables, key_table, entry, key_table_cmp);
  29.   struct key_tables key_tables = RB_INITIALIZER(&key_tables);

...too many issues to display (limit=10 exceeded), please see /home/icse2019ae/srcs/tmux/tmux-2.5/infer-out/bugs.txt or run `infer-explore` for the remaining issues.


Summary of the reports

  NULL_DEREFERENCE: 38
       MEMORY_LEAK: 38

real    9m6.837s
user    8m20.956s
sys     0m9.948s

```
Infer takes around 8m20.956s (**501.0 seconds**) for checking Tmux. 
Since it detects many bugs, the final report is located in "/home/icse2019ae/srcs/tmux/tmux-2.5/infer-out/bugs.txt". Here is the link to it:

The report file: [bugs.txt](/assets/text/bugs.txt)

Visualized report: [tmux-infer-pinpoint-report](http://ec2-54-185-211-230.us-west-2.compute.amazonaws.com:40080/online_report/#5b73e955fc7ce67ad38f2ff5)

At the end of this file, Infer reports 38 memory leaks, which becomes 18 after clustering. After close inspection, only 1 of 18 is True Positive. 

```bash
Summary of the reports

  NULL_DEREFERENCE: 38
       MEMORY_LEAK: 38
```



### Pinpoint

Commands:
```bash
pp-pinpoint -report=tmux_pinpoint.json bench36/tmux/tmux.bc

```

Output:
```bash
                                         Settings
------------------------------------------------------------------------------------------
Execution Mode: Normal. Typical balanced settings for finding software vulnerabilities.
------------------------------------------------------------------------------------------

                                       Code Metrics
------------------------------------------------------------------------------------------
Total Number of Functions: 1483
         Number of Implemented Functions: 1293
         Number of External Functions: 190
         External Functions Ratio: 12.81%
Instruction Count: 138155 (Avg: 106.85 per function)
Function With Most Instructions: 1480 (Function: window_copy_command)
Average Cyclomatic Complexity: 7.49
Max Cyclomatic Complexity: 151 (Function: window_copy_command)
------------------------------------------------------------------------------------------

                                    Analyzer Execution
------------------------------------------------------------------------------------------
Code preprocessing ........Done!
Constructing call graph ........Done!
Before CDG Time:        1691310us
CDG-Construction Time:  67364us
CDG-Construction Memory:        0KB
[Falcon] [################################################################################] 100%
Resolving indirect calls ........Done
[SPEG] [################################################################################] 100%
SEG-Building Time:      14317544us
SEG-Building Memory:    987M 952KB
[Canary] [################################################################################] 100%
[PSA Checking] [################################################################################] 100%
PPMaster Time Time:     28484658us
[Post-processing] [################################################################################] 100%

PSA Memory Leak Checker Time Time:      95588us
Peak Memory:    2G 952M 816KB

------------------------------------------------------------------------------------------


                             Bug reports summary per bug type
------------------------------------------------------------------------------------------
Bug type                                              Number of reports
------------------------------------------------------------------------------------------
Memory Leak : CWE-401                                 10


Total Time:     47946278us
Peak Memory:    2G 952M 816KB

```
Report file: [tmux_pinpoint.json](/assets/text/tmux_pinpoint.json) 

Visualized report: [tmux-pinpoint-pinpoint-report](http://ec2-54-185-211-230.us-west-2.compute.amazonaws.com:40080/online_report/#5b72bf75fc7ce67ad38f21f5)


Pinpoint takes 47946278us (**47.9 seconds**) for analyzing Tmux. 
Pinpoint initially reports ten bugs being found. Same as SMOKE, we clustered them according to their root causes, which are two (xmalloc.c:33 and xmalloc.c:47). After inspection, one bug report is true positive, and another one is a false positive. 


### Summary 

Here is the summary for this evaluation: 

Performance (in seconds):

| Project | SMOKE | Pinpoint | Saber | CSA   | Infer  |
|---------|-------|----------|-------|-------|--------|
| tmux    | 7.52  | 47.9     | 63.5  | 164.0 | 509.56 |


For precision ([# False positive]/[# Total Reports]):

| Project | SMOKE | Pinpoint | Saber | CSA | Infer |
|---------|-------|----------|-------|-----|-------|
| tmux    | 2/9   | 2/2      | 6/6   | 0/0 | 17/18 |


