---
title: Initial MacOS Setup for Web Dev
author: Brandon Baek
date: 2022-09-10
categories: [Tutorial, Mac]
tags: [web dev,macos,setup]
---

# Mac OS 초기설정

## 인텔cpu와 m1실리콘 칩셋에 따라 설치환경에 차이

인텔기반의 맥 제품은 Homebrew 설치시 /usr/local/bin 디렉토리를 사용  
M1 애플실리콘 제품의 경우에는 /opt/homebrew/bin 디렉토리를 사용하기에 기본으로 제공하는 zsh가 아닌 다른 쉘을 설치한다거나 하면 디렉토리 설정에 주의가 필요함

홈브류 설치
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
홈브류 설치후 m1의 경우 추가 설정관련 경고가 뜹니다. 이걸 따라해주면 완성.

## VS Code
한글입력 오류 발생시 cm+shift+p configure display language에서 ko 한글 선택후 restart
vscode 전체가 한글화 되고 나서 다시 언어를 en으로 바꿔주면 한글 입력 오류 해결

## Git configuration

```shell
brew install gh
git config --global user.name "name"
git config --global user.email email@email.com
gh auth login
```

## Ruby setup with chruby
https://jekyllrb.com/docs/installation/macos/
the link provide ruby(chruby) installation guide with jekyll install

```shell
brew install chruby ruby-install
ruby-install ruby

echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.1.2" >> ~/.zshrc # run 'chruby' to see actual version
ruby -v
```

## 한글입력 Shift + Space 변환
monterey에서는 한글입력 shortcut을 shift + space 설정하는 방법이 막혀버렸습니다.  
기존에는 fn버튼을 함께 눌러주는 방식으로 shortcut을 지정할 수 있었으나 monterey에서는 불가능.  
방법은 plist edit툴을 사용해서 해당파일을 직접 수정해주는것.

```shell
brew install --cask plistedit-pro
```
xcode를 사용해도 된다고 하나 저는 plistedit-pro를 사용했음
**"~/Library/Preferences/com.apple.symbolichotkeys.plist"**
위에 파일에서 61번 key value(parameter-item2)를 131072로 변경후 리부팅하면됨. (original value 786432)

