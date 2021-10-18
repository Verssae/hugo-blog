---
title: "cudart64_110.dll not found error 해결법"
date: 2021-10-18T12:33:12+09:00
draft: false
tags: [tensorflow, CUDA, error]
summary: cudart64_110.dll not found error 해결법
---
## Could not load dynamic library 'cusolver64_11.dll'; dlerror: cusolver64_11.dll not found
### 증상
tensorflow-gpu를 사용하려고 import 할 때, 위와 같은 에러가 발생하였다. 
### 원인 및 해결책
[이곳](https://www.tensorflow.org/install/source_windows?hl=en#gpu)에서 본인이 사용할 tensorflow 버전에 맞는 cuDNN 및 CUDA를 설치하면 된다. 
