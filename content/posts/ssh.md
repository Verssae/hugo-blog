---
title: "SSH 접속하기"
date: 2021-09-25T23:14:26+09:00
draft: false
tags: ["ssh", "usage"]
summary: "ssh로 원격 서버에 편하게 접속하게 만들기"
---
1. 로컬 호스트에 키 생성
```bash
ssh-keygen
```
1. 원격 호스트에 public key 복사
```bash
ssh-copy-id i- ~/.ssh/id_rsa.pub <username>@<remote-server>
```
3. 로컬 호스트에서 원격 호스트로 ssh 접속
```bash
ssh <remote-server>
```
