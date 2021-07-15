# MacOS 초기화 후 개발환경 세팅 for M1



## 초기화 및 재설치

- 맥북을 종료하고 전원버튼을 꾸욱 누르기
- `Loading starting options... `나오면 손 떼기
- 옵션 > 계속 누르기
- 디스크 유틸리디 > 1. `Macintosh HD` 지우고 2. `Data` 드라이브 지우기 (순서 중요!)
-  닫기 누르고 `macOS Big Sur` 다시 설치 
- 설치 위치는 `Macintosh HD` 로 선택



## MacOS 환경 설정

### 한/영 단축키 변경

- 시스템 환경설정 - 키보드 - 단축키 - 입력 소스

### 배터리 퍼센트 표시
- 환경설정 - Dock 및 메뉴 막대 - 배터리 - 퍼신트 보기 체크

### Finder 경로 막대 및 상태 막대 표시
- Finder 파일 열기 - 상태 표시줄에서 보기 - 경로 막대 보기, 상태 막대 보기 클릭



## 개발 환경 설정

### iTerm2
- https://www.iterm2.com



### Oh my zsh

- macOS Big Sur 버전부터 기본 쉘이 기존 bash에서 zsh로 변경됨
- 터미널에서 아래 명령어 실행, 설치
```
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```



#### zsh 꾸미기

- Pure prompt 설치

  ```
  $ mkdir -p "$HOME/.zsh"
  $ git clone https://github.com/sindresorhus/pure.git "$HOME/.zsh/pure"
  $ echo "\nfpath+=$HOME/.zsh/pure\nautoload -U promptinit; promptinit\nprompt pure" >> "$HOME/.zshrc"
  $ exec $SHELL
  ```

- 이렇게만하면 화면이 깨져서 추가 다운로드 필요
- https://github.com/sindresorhus/iterm2-snazzy 들어가서 Install 항목에 있는 `Snazzy.itermcolors` 파일 저장, 실행
- iTerm2에서 `command+,` 를 눌러 Preferences 실행, Profiles 클릭 후 Default 프로파일 선택, Colors 선택
- Color Presets 셀렉트 박스에서 Snazzy 선택



#### zsh syntax highlighting 설치

- 아래 명령어 실행

```
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git "$HOME/.zsh/zsh-syntax-highlighting"
$ echo "\nsource $HOME/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> "$HOME/.zshrc"
```

- 설치 완료 후 재시작하면 적용 완료



### HomeBrew

- https://brew.sh



#### homebrew 설치

```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

- `~/.zshrc` 에 해당 코드 추가

	```
	eval $(/opt/homebrew/bin/brew shellenv)
	```
```
$ source ~/.zshrc
```



#### homebrew 이용해 python 설치

```
$ brew install pyenv
```

```
$ echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
$ echo 'eval "$(pyenv init -)"' >> ~/.zshrc
$ exec "$SHELL"

$ pyenv install 3.9.6
$ pyenv global 3.9.6
```

```
$ python -V
Python 3.9.6
```



