# 환경셋팅

## 🌈CentOS 7

[Download CentOS 7](https://www.centos.org/download/)


## 🌈Prerequsite


### 🍀 IP 확인하기
```
yum -y install net-tools
ifconfig
```

OR

```
ip addr
```

### 🍀 SSH

```
rpm -qa | grep -i openssh-server
which sshd
```

만일 없으면

```
yum install openssh-server
```

 - `/etc/ssh/sshd_config` 파일 수정

```vim
...
...
...
# PORT 22 --> 주석 해제
...
...
...
```

### 🍀 Utilities

```
yum install -y vim
yum install -y git
```


### 🍀 Tips

#### - *scp*
 - `로컬 -> 원격`
```
scp [전송할 파일 경로] [유저]@[주소]:[받을 경로]
```

 - `원격 -> 로컬`

```
scp [유저]@[주소]:[전송할 파일 경로] [받을 경로] 
```
 - 옵션
```
 -r : 폴더 복사
```

#### - *yum rpm downloadonly*

```
yum install 패키지명 -y --downloadonly --downloaddir=경로
```

#### - *rpm*

 - 설치
```
rpm -ivh 패키지명
```


 - 확인
```
rpm -qa | grep 패키지명
```


 - 제거
```
rpm -ev 패키지명
```

<br>
<br>
<br>
<br>
<br>
<hr>
<hr>
<hr>

# Dependencies Order

## vim

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.kakao.com
 * extras: mirror.kakao.com
 * updates: mirror.kakao.com
Resolving Dependencies
--> Running transaction check
---> Package vim-enhanced.x86_64 2:7.4.629-8.el7_9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package                  Arch               Version                        Repository           Size
======================================================================================================
Installing:
 vim-enhanced             x86_64             2:7.4.629-8.el7_9              updates             1.1 M

Transaction Summary
======================================================================================================
Install  1 Package

Total download size: 1.1 M
Installed size: 2.2 M
Background downloading packages, then exiting:
vim-enhanced-7.4.629-8.el7_9.x86_64.rpm                                        | 1.1 MB  00:00:00
exiting because "Download Only" specified
```

<br>
<br>
<br>

## git

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.kakao.com
 * extras: mirror.kakao.com
 * updates: mirror.kakao.com
Resolving Dependencies
--> Running transaction check
---> Package git.x86_64 0:1.8.3.1-23.el7_8 will be installed
--> Processing Dependency: perl-Git = 1.8.3.1-23.el7_8 for package: git-1.8.3.1-23.el7_8.x86_64
--> Processing Dependency: perl(Git) for package: git-1.8.3.1-23.el7_8.x86_64
--> Running transaction check
---> Package perl-Git.noarch 0:1.8.3.1-23.el7_8 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package                Arch                 Version                         Repository          Size
======================================================================================================
Installing:
 git                    x86_64               1.8.3.1-23.el7_8                base               4.4 M
Installing for dependencies:
 perl-Git               noarch               1.8.3.1-23.el7_8                base                56 k

Transaction Summary
======================================================================================================
Install  1 Package (+1 Dependent package)

Total download size: 4.5 M
Installed size: 22 M
Background downloading packages, then exiting:
(1/2): perl-Git-1.8.3.1-23.el7_8.noarch.rpm                                    |  56 kB  00:00:00
(2/2): git-1.8.3.1-23.el7_8.x86_64.rpm                                         | 4.4 MB  00:00:00
------------------------------------------------------------------------------------------------------
Total                                                                  23 MB/s | 4.5 MB  00:00:00
exiting because "Download Only" specified
```

<br>
<br>
<br>

## nodejs

 - pre-working
```
# yum clean all <-- 꼬일 때 
curl -sL https://rpm.nodesource.com/setup_14.x | sudo -E bash -
```
 - contents

```
Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
base                                                                           | 3.6 kB  00:00:00
extras                                                                         | 2.9 kB  00:00:00
nodesource                                                                     | 2.5 kB  00:00:00
updates                                                                        | 2.9 kB  00:00:00
(1/5): base/7/x86_64/group_gz                                                  | 153 kB  00:00:00
(2/5): extras/7/x86_64/primary_db                                              | 247 kB  00:00:00
(3/5): base/7/x86_64/primary_db                                                | 6.1 MB  00:00:00
(4/5): updates/7/x86_64/primary_db                                             |  16 MB  00:00:05
(5/5): nodesource/x86_64/primary_db                                            |  58 kB  00:00:05
Resolving Dependencies
--> Running transaction check
---> Package nodejs.x86_64 2:14.20.0-1nodesource will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package            Arch               Version                           Repository              Size
======================================================================================================
Installing:
 nodejs             x86_64             2:14.20.0-1nodesource             nodesource              33 M

Transaction Summary
======================================================================================================
Install  1 Package

Total download size: 33 M
Installed size: 93 M
Background downloading packages, then exiting:
경고: /home/owen-rhie/yum-pack/nodejs-14.20.0-1nodesource.x86_64.rpm: Header V4 RSA/SHA512 Signature, key ID 34fa74dd: NOKEY
Public key for nodejs-14.20.0-1nodesource.x86_64.rpm is not installed
nodejs-14.20.0-1nodesource.x86_64.rpm                                          |  33 MB  00:00:01
exiting because "Download Only" specified
```

<br>
<br>
<br>

## ---

```
```

<br>
<br>
<br>

## ---

```
```

<br>
<br>
<br>

## ---

```
```

<br>
<br>
<br>

## ---

```
```

<br>
<br>
<br>

## ---

```
```
<!-- yum install -y gcc-c++ make -->