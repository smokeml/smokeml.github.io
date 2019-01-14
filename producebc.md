---
layout: default
title: ICSE 2019 Artifact Evaluation for SMOKE
permalink: /producebc/
---




## Generate BitCode files and compile_commands.json

！Note: This step is not necessary for evaluating this artifact. This step requires a project can be successfully compiled on a machine, which itself is quite complicated and time-consuming. We have prepared all the BitCode files for the subjects in the paper in both version36 and version40 for evaluation. 

**compile_commands.json** is the Compilation Database file. It specifies how to replay single compilations independently of the build system. Please refer to [JSON Compilation Database Format Specification](https://clang.llvm.org/docs/JSONCompilationDatabase.html)

We use **pp-capture** command to generate BitCode files and the compile_commands.json file. 

```bash
cd ~/srcs/tmux/tmux-2.5
pp-capture -- make -j4

```

pp-capture generates a **".piggy"** folder under ~/srcs/tmux/tmux-2.5. Bitcode file can be found under ".piggy/top" and the compile_commands.json file is located at .piggy/

