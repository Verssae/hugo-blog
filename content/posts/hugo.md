---
title: "Hugo-blog (README)"
date: 2021-09-28T10:17:59+09:00
draft: false
tags: [hugo, usage]
summary: Hugo로 블로그 만들기
---
> A blog powered by HUGO 
## Requirements
* [golang](https://golang.org/dl/)
* hugo
```
brew install hugo
```
## Installation
* Clone submodules (public, themes/PaperMod) 
```
git submodule update --init
git submodule foreach checkout main
```
## New Post
```zsh
hugo new posts/<title.md>
```

## Run server
```zsh
hugo server -D
```
## Compile
```zsh
hugo -t PaperMod
```
## Publish
```zsh
cd public
git add *
git commit
git push origin main
```

## Notices
* When you want to commit, commit submodules first


