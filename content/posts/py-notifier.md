---
title: "[Python] 데스크톱 알림 보내기"
date: 2021-10-03T13:45:36+09:00
draft: true
tags: []
summary: Python으로 데스크톱 푸시 알림을 보내보자
---
Tensorflow나 Pytorch로 모델 학습을 진행할 때 학습이 완료되면 알림을 받으면 굉장히 유용할 것 같지 않은가?
여러 모듈을 찾아본 결과 가장 간단한 것을 찾았다. 
`pip install py-notifier`
Windows, Linux, MacOs에서 사용 가능하다.

## Requirements
* Windows: `pip install win10toast`
* Linux: `sudo apt=get install libnotify-bin`
* MacOs: `pip install pync`

## Example
```python
from pynotifier import Notification

Notification(
	title='Notification Title',
	description='Notification Description',
	icon_path='/absolute/path/to/image/icon.png', # On Windows .ico is required, on Linux - .png
	duration=5,                                   # Duration in seconds
	urgency='normal'
).send()
```

## 아쉬운 점
* Mac에서만 테스트해본 결과 알림 소리가 안난다. 사운드가 필요한 경우 추가적인 모듈을 활용하면 많이 있을듯.
* 원격 서버에서 로컬 컴퓨터로 알림 보내기는 당연히 안된다. 

## 개선 계획
