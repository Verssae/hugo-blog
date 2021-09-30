---
title: "Markov"
date: 2021-09-29T22:44:26+09:00
draft: true
tags: []
summary: Markov model에 대해 공부하다가 든 의문점
---

Autoregressive Models의 approximation 중 하나인 Markov model(다른 하나는 latent autoregressive model)에서의 랜덤 변수의 분포는 T개의 이전 시퀀스에만 의존하는데, T=1일 때 first-order Markov model이라고 한다.

강화학습 공부 시에 Markov 상태는 T=1인 경우로만 한정해서 알고 있었기에, T > 1인 경우의 강화학습에 대해 더 찾아봐야겠다.