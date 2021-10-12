---
title: "[Python] Discord Webhook으로 학습 종료 시 알림 보내기"
date: 2021-10-12T17:38:24+09:00
draft: false
tags: ['python', 'discord-webhook']
summary: Python에서 학습 종료 시 알람을 discord-webhook을 사용하여 구현하기
---

## 들어가기
Tensorflow, pytorch 등으로 모델을 학습하고 끝날 때 까지 마냥 기다리고만 있을 순 없다.

가장 간단하게 python 코드 상에서 내 디바이스로 알림을 보내는 방법을 찾아본 결과, **Discord Webhook**을 사용하는 것이 제일 적합한 것 같았다.

누군가 Slack Incomming API로 python에서 메시지를 보내는 것에서 영감을 받아, 내가 자주 사용하는 Discord를 사용하여 구현해보고자 했다.

## 설치
```pip install discord-webhook```

## 사용법
다양한 예제는 [python-discord-webhook](https://github.com/lovvskillz/python-discord-webhook)을 참고하면 좋다.

```python
from discord_webhook import DiscordWebhook

webhook = DiscordWebhook(url='your webhook url', content='Webhook Message', username='name of bot')
response = webhook.execute()
```
webhook url은 알림을 받을 discord 서버에서  `서버 설정` > `연동` > `웹후크` > `새 웹후크` 로 만들고 URL을 복사하면 된다.

DiscordWebhook 인스턴스를 생성하고 excute를 통해 다음과 같이 서버에 메시지를 보낼 수 있다. 

![img1](/dscord1.png)


## Embed
Discord bot을 개발해봤다면 알겠지만 `Embed`를 통해 rich한 데이터들을 메시지와 함께 보낼 수 있다.
```python
from discord_webhook import DiscordEmbed

embed = DiscordEmbed(title='your title', description='your desc', color='03b2f8')

# set author
embed.set_author(name='Author Name', url='author url', icon_url='author icon url')

# set image
embed.set_image(url='your image url') # url만 가능 (local file은 안됨)

# set thumbnail
embed.set_thumbnail(url='your thumbnail url') # url만 가능 (local file은 안됨)

# set footer
embed.set_footer(text='Embed Footer Text', icon_url='URL of icon')

# set timestamp (default is now)
embed.set_timestamp()

# add fields to embed
embed.add_embed_field(name='Field 1', value='value 1')
embed.add_embed_field(name='Field 2', value='value 2')

# add embed object to webhook
webhook.add_embed(embed)

response = webhook.execute()
```
나는 주로 embed의 field를 통해 학습 결과로 나온 수치들을 전송한다.
```python
embed.add_embed_field(name='average reward', value=f'{a.mean():.2f}')
embed.add_embed_field(name='min', value=f'{a.min():.2f}')
embed.add_embed_field(name='max', value=f'{a.max():.2f}')
```

plot 결과를 전송하고 싶은데, set_images나 set_thumbnail로는 local 이미지를 전송할 수 없다. 

따라서 이미지를 파일로 먼저 전송한 후, attachement를 이용해 thumbnail을 보낼 수 있다.
```python
plt.savefig('result.png', dpi=300)

with open('result.png', 'rb') as f:
  webhook.add_file(file=f.read(), filename='plot.png')
embed.set_thumbnail(url='attachment://plot.png')

```
이렇게 간단하고 깔끔하게 학습 종료 시 discord 메시지를 전송함으로써 알림을 보낼 수 있다. 
![img2](/discord2.png)