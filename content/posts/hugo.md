---
title: "Hugo"
date: 2021-09-28T10:17:59+09:00
draft: false
tags: [hugo, usage]
summary: Hugo로 블로그 만들기
---
# Hugo-blog
A blog powered by HUGO 
## Requirements
* [golang](https://golang.org/dl/)
* hugo
```
brew install hugo
```
## Installation
* Clone themes 
```
git submodule update --init --recursive
```
* Update themes
```
git submodule update --remote --merge
```
## Run
* Run local server (`-D` for development mode)
```
hugo server -D
```
* Publish (`PaperMod` is name of theme) to `origin` of `/public` (using git submodule add [verssae.github.io](https://verssae.github.io))
```
hugo -t PaperMod
cd publish
git add *
git commit
git push origin main
```
