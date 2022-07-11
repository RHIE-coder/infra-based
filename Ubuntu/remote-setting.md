# 환경셋팅

## 🌈Ubuntu 18.4 LTS

[Download Ubuntu 18.4](https://releases.ubuntu.com/bionic)

## 🌈VirtualBox

[Download VirtualBox](https://www.virtualbox.org/wiki/Downloads)

## 🌈Putty or WSL2

[Download Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

 - how to download `WSL2`
 
```
[Powershell 관리자모드로 실행]
wsl --install
[컴퓨터 재부팅]
[Microsoft Store에서 Windows Terminal 설치]
wsl
sudo apt-get update
sudo apt-get install wget ca-certificates
logout
```

## 🌈Visual Studio Code

[Download VSCode](https://code.visualstudio.com)

## 🌈Start Setting

### 🍀원격 환경

#### 1. VirtualBox에 Ubuntu설치하기
#### 2. VirtualBox 게스트 확장과 한글 입력 셋팅해보기[Shift+Space]
#### 3. putty 혹은 WSL2로 리눅스 접속

 - 리눅스에 `openssh-server` 설치
```shell
sudo apt-get install openssh-server
sudo service sshd start
```
 
 - active(running) 상태인지 확인하기
```shell
sudo service sshd status
```

 - VirtualBox에 포트포워딩하기

<br><br>

#### - 게스트OS IP확인
```shell
sudo apt install net-tools
```
```shell
ifconfig
```

<br><br>

#### - 호스트OS IP확인
window cmd
```cmd
ipconfig
```

 - Putty로 접속

<br><br>

#### 4. VSCode로 리눅스 접속

 - 확장 프로그램 설치
    - Remote - SSH

 - `F1`누르고 `Remote-SSH:Connect to Host..` 하기
```
>remotessh
```
 - 접속 하기 `[userid]@[ipaddress]`

*example*

```
rhie@192.168.56.1
```
#### 에러발생시 아래 폴더 확인
```
C:\Users\[사용자 이름]\.ssh
```

### 🍀Prerequisites
#### jq
```
sudo apt install jq
```

#### git
```
sudo apt install git
```
#### curl
```
sudo apt install curl
```

#### wget
```
wget --version
```