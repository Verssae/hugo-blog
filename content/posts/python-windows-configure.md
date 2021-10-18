---
title: "[Python] Windows 환경 설정"
date: 2021-10-18T11:53:20+09:00
draft: false
tags: [python, windows]
summary: 
---
## 들어가기
최근  Windows 11로 클린 설치를 하면서, 개발 환경을 다시 설정하면서 많은 troubleshooting을 겪게 되었다.

Python 위주로 Windows 개발 환경 설정을 정리해본다.

## Python 가상환경
Python 가상환경은 지금까지 Anaconda로 관리해오다가, 최근 venv 및 pipenv 등 다른 가상환경 관리자를 알게되어 Pipfile로 가상환경 및 패키지 관리를 하는 pipenv를 눈여겨보고 있었다.

특히 이번 Windows 11로 설치하고 나서 PowerShell에서 Anaconda가 잘 작동하지 않아 (https 관련 에러가 계속 나는데 해결하지 못함ㅠ) 이번 기회에 확실히 Pipenv를 사용해보고자 마음먹었다.

Anaconda와 달리 pipenv는 사용할 Python 버전이 설치되어있어야 하기 때문에, 필요한 Python 버전을 편하게 다운받을 수 있는 패키지 관리자가 또 필요하다.

### OSX/Linux
[pyenv](https://github.com/pyenv/pyenv)를 사용하여 원하는 버전의 Python을 설치하여 사용하면 된다.

### Windows
정식으로 pyenv를 지원하지 않아 pyenv-win이 있긴 하지만, 사용해본 결과 path 설정 등 귀찮은 부분이 많았다. 

따라서 [Scoop](https://scoop.sh/)을 사용하여 Python을 설치하기로 했다. 

Scoop 설치 방법은 [이곳](https://www.sangkon.com/windows-setting-for-developer/)에 잘 나와있다.

```PowerShell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
```
Scoop에서 사용할 수 있는 패키지 중 개별 버전을 설치하기 위해서 bucket을 추가해야 한다.
```PowerShell
scoop install git
scoop bucket add extras
scoop bucket add versions
```
Python 등 패키지 설치는 `search`를 통해 검색할 수 있고, `install`을 통해 설치할 수 있다.
```PowerShell
scoop search python
scoop install python38
```
Scoop을 사용하여 `go`와 `hugo`도 간편하게 설치할 수 있었다. 

## Pipenv
Pipenv 사용 방법은 [이곳](https://velog.io/@doondoony/pipenv-101)에 잘 나와있다.
