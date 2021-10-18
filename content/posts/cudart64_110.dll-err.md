---
title: "cudart64_110.dll dllerror 해결법"
date: 2021-10-18T12:23:43+09:00
draft: false
tags: [tensorflow, CUDA, error]
summary: cudart64_110.dll not found error 해결법
---
## "Could not load dynamic library 'cudart64_110.dll'; dlerror: cudart64_110.dll not found"
### 증상
tensorflow-gpu를 사용하려고 import 할 때, 위와 같은 에러가 발생하였다. 

### 분석
CUDA 설치 폴더에 해당 dll들이 모두 존재하는 것으로 보아, dll 폴더 위치를 인식하지 못하는 것으로 보인다. 

### 임시 해결책
`os.add_dll_directory("C:/Program Files/NVIDIA GPU Computing Toolkit/CUDA/v11.2/bin")`을 tensorflow를 import 하기 전에 실행하면 dll을 제대로 임포트할 수 있다. 물론 CUDA 버전 및 경로는 맞춰야 한다.

### 원인 및 해결책
구글링 끝에 [tensorflow issue](https://github.com/tensorflow/tensorflow/issues/48868)에서 원인을 찾을 수 있었다.

이는 Windows와 관련된 결함으로, Python을 Microsoft Store에서 설치할 경우 Python이 path를 정상적으로 로드하지 못하는 일이 발생한다고 한다. 

나와 같이 Microsoft Store에서 Python을 설치한 경우, Python 공식 웹사이트에서 설치하면 된다.

Scoop을 사용해도 문제없이 설치할 수 있었다.