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

 - 전체 설치
```
rpm -i --nodeps *.rpm
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
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package git.x86_64 0:1.8.3.1-23.el7_8 will be installed
--> Processing Dependency: perl-Git = 1.8.3.1-23.el7_8 for package: git-1.8.3.1-23.el7_8.x86_64
--> Processing Dependency: perl(Term::ReadKey) for package: git-1.8.3.1-23.el7_8.x86_64
--> Processing Dependency: perl(Git) for package: git-1.8.3.1-23.el7_8.x86_64
--> Processing Dependency: perl(Error) for package: git-1.8.3.1-23.el7_8.x86_64
--> Running transaction check
---> Package perl-Error.noarch 1:0.17020-2.el7 will be installed
---> Package perl-Git.noarch 0:1.8.3.1-23.el7_8 will be installed
---> Package perl-TermReadKey.x86_64 0:2.30-20.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package                      Arch               Version                       Repository        Size
======================================================================================================
Installing:
 git                          x86_64             1.8.3.1-23.el7_8              base             4.4 M
Installing for dependencies:
 perl-Error                   noarch             1:0.17020-2.el7               base              32 k
 perl-Git                     noarch             1.8.3.1-23.el7_8              base              56 k
 perl-TermReadKey             x86_64             2.30-20.el7                   base              31 k

Transaction Summary
======================================================================================================
Install  1 Package (+3 Dependent packages)

Total download size: 4.5 M
Installed size: 22 M
Background downloading packages, then exiting:
(1/4): perl-Git-1.8.3.1-23.el7_8.noarch.rpm                                    |  56 kB  00:00:00
(2/4): perl-TermReadKey-2.30-20.el7.x86_64.rpm                                 |  31 kB  00:00:00
(3/4): perl-Error-0.17020-2.el7.noarch.rpm                                     |  32 kB  00:00:00
(4/4): git-1.8.3.1-23.el7_8.x86_64.rpm                                         | 4.4 MB  00:00:00
------------------------------------------------------------------------------------------------------
Total                                                                  26 MB/s | 4.5 MB  00:00:00
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

## zip

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package zip.x86_64 0:3.0-11.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package              Arch                    Version                     Repository             Size
======================================================================================================
Installing:
 zip                  x86_64                  3.0-11.el7                  base                  260 k

Transaction Summary
======================================================================================================
Install  1 Package`

Total download size: 260 k
Installed size: 796 k
Background downloading packages, then exiting:
zip-3.0-11.el7.x86_64.rpm                                                      | 260 kB  00:00:00
exiting because "Download Only" specified
```

<br>
<br>
<br>

## unzip

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package unzip.x86_64 0:6.0-24.el7_9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package              Arch                  Version                      Repository              Size
======================================================================================================
Installing:
 unzip                x86_64                6.0-24.el7_9                 updates                172 k

Transaction Summary
======================================================================================================
Install  1 Package

Total download size: 172 k
Installed size: 369 k
Background downloading packages, then exiting:
unzip-6.0-24.el7_9.x86_64.rpm                                                  | 172 kB  00:00:00
exiting because "Download Only" specified
```

<br>
<br>
<br>

## tree

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package tree.x86_64 0:1.6.0-10.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package              Arch                   Version                       Repository            Size
======================================================================================================
Installing:
 tree                 x86_64                 1.6.0-10.el7                  base                  46 k

Transaction Summary
======================================================================================================
Install  1 Package

Total download size: 46 k
Installed size: 87 k
Background downloading packages, then exiting:
tree-1.6.0-10.el7.x86_64.rpm                                                   |  46 kB  00:00:00
exiting because "Download Only" specified
```

<br>
<br>
<br>

## Perl

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package perl.x86_64 4:5.16.3-299.el7_9 will be installed
--> Processing Dependency: perl-libs = 4:5.16.3-299.el7_9 for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Socket) >= 1.3 for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Scalar::Util) >= 1.10 for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl-macros for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl-libs for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(threads::shared) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(threads) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(constant) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Time::Local) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Time::HiRes) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Storable) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Socket) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Scalar::Util) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Pod::Simple::XHTML) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Pod::Simple::Search) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Getopt::Long) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Filter::Util::Call) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(File::Temp) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(File::Spec::Unix) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(File::Spec::Functions) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(File::Spec) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(File::Path) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Exporter) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Cwd) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: perl(Carp) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Processing Dependency: libperl.so()(64bit) for package: 4:perl-5.16.3-299.el7_9.x86_64
--> Running transaction check
---> Package perl-Carp.noarch 0:1.26-244.el7 will be installed
---> Package perl-Exporter.noarch 0:5.68-3.el7 will be installed
---> Package perl-File-Path.noarch 0:2.09-2.el7 will be installed
---> Package perl-File-Temp.noarch 0:0.23.01-3.el7 will be installed
---> Package perl-Filter.x86_64 0:1.49-3.el7 will be installed
---> Package perl-Getopt-Long.noarch 0:2.40-3.el7 will be installed
--> Processing Dependency: perl(Pod::Usage) >= 1.14 for package: perl-Getopt-Long-2.40-3.el7.noarch
--> Processing Dependency: perl(Text::ParseWords) for package: perl-Getopt-Long-2.40-3.el7.noarch
---> Package perl-PathTools.x86_64 0:3.40-5.el7 will be installed
---> Package perl-Pod-Simple.noarch 1:3.28-4.el7 will be installed
--> Processing Dependency: perl(Pod::Escapes) >= 1.04 for package: 1:perl-Pod-Simple-3.28-4.el7.noarch
--> Processing Dependency: perl(Encode) for package: 1:perl-Pod-Simple-3.28-4.el7.noarch
---> Package perl-Scalar-List-Utils.x86_64 0:1.27-248.el7 will be installed
---> Package perl-Socket.x86_64 0:2.010-5.el7 will be installed
---> Package perl-Storable.x86_64 0:2.45-3.el7 will be installed
---> Package perl-Time-HiRes.x86_64 4:1.9725-3.el7 will be installed
---> Package perl-Time-Local.noarch 0:1.2300-2.el7 will be installed
---> Package perl-constant.noarch 0:1.27-2.el7 will be installed
---> Package perl-libs.x86_64 4:5.16.3-299.el7_9 will be installed
---> Package perl-macros.x86_64 4:5.16.3-299.el7_9 will be installed
---> Package perl-threads.x86_64 0:1.87-4.el7 will be installed
---> Package perl-threads-shared.x86_64 0:1.43-6.el7 will be installed
--> Running transaction check
---> Package perl-Encode.x86_64 0:2.51-7.el7 will be installed
---> Package perl-Pod-Escapes.noarch 1:1.04-299.el7_9 will be installed
---> Package perl-Pod-Usage.noarch 0:1.63-3.el7 will be installed
--> Processing Dependency: perl(Pod::Text) >= 3.15 for package: perl-Pod-Usage-1.63-3.el7.noarch
--> Processing Dependency: perl-Pod-Perldoc for package: perl-Pod-Usage-1.63-3.el7.noarch
---> Package perl-Text-ParseWords.noarch 0:3.29-4.el7 will be installed
--> Running transaction check
---> Package perl-Pod-Perldoc.noarch 0:3.20-4.el7 will be installed
--> Processing Dependency: perl(parent) for package: perl-Pod-Perldoc-3.20-4.el7.noarch
--> Processing Dependency: perl(HTTP::Tiny) for package: perl-Pod-Perldoc-3.20-4.el7.noarch
---> Package perl-podlators.noarch 0:2.5.1-3.el7 will be installed
--> Running transaction check
---> Package perl-HTTP-Tiny.noarch 0:0.033-3.el7 will be installed
---> Package perl-parent.noarch 1:0.225-244.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package                         Arch            Version                       Repository        Size
======================================================================================================
Installing:
 perl                            x86_64          4:5.16.3-299.el7_9            updates          8.0 M
Installing for dependencies:
 perl-Carp                       noarch          1.26-244.el7                  base              19 k
 perl-Encode                     x86_64          2.51-7.el7                    base             1.5 M
 perl-Exporter                   noarch          5.68-3.el7                    base              28 k
 perl-File-Path                  noarch          2.09-2.el7                    base              26 k
 perl-File-Temp                  noarch          0.23.01-3.el7                 base              56 k
 perl-Filter                     x86_64          1.49-3.el7                    base              76 k
 perl-Getopt-Long                noarch          2.40-3.el7                    base              56 k
 perl-HTTP-Tiny                  noarch          0.033-3.el7                   base              38 k
 perl-PathTools                  x86_64          3.40-5.el7                    base              82 k
 perl-Pod-Escapes                noarch          1:1.04-299.el7_9              updates           52 k
 perl-Pod-Perldoc                noarch          3.20-4.el7                    base              87 k
 perl-Pod-Simple                 noarch          1:3.28-4.el7                  base             216 k
 perl-Pod-Usage                  noarch          1.63-3.el7                    base              27 k
 perl-Scalar-List-Utils          x86_64          1.27-248.el7                  base              36 k
 perl-Socket                     x86_64          2.010-5.el7                   base              49 k
 perl-Storable                   x86_64          2.45-3.el7                    base              77 k
 perl-Text-ParseWords            noarch          3.29-4.el7                    base              14 k
 perl-Time-HiRes                 x86_64          4:1.9725-3.el7                base              45 k
 perl-Time-Local                 noarch          1.2300-2.el7                  base              24 k
 perl-constant                   noarch          1.27-2.el7                    base              19 k
 perl-libs                       x86_64          4:5.16.3-299.el7_9            updates          690 k
 perl-macros                     x86_64          4:5.16.3-299.el7_9            updates           44 k
 perl-parent                     noarch          1:0.225-244.el7               base              12 k
 perl-podlators                  noarch          2.5.1-3.el7                   base             112 k
 perl-threads                    x86_64          1.87-4.el7                    base              49 k
 perl-threads-shared             x86_64          1.43-6.el7                    base              39 k

Transaction Summary
======================================================================================================
Install  1 Package (+26 Dependent packages)

Total download size: 11 M
Installed size: 36 M
Background downloading packages, then exiting:
(1/27): perl-Carp-1.26-244.el7.noarch.rpm                                      |  19 kB  00:00:00
(2/27): perl-File-Path-2.09-2.el7.noarch.rpm                                   |  26 kB  00:00:00
(3/27): perl-File-Temp-0.23.01-3.el7.noarch.rpm                                |  56 kB  00:00:00
(4/27): perl-Exporter-5.68-3.el7.noarch.rpm                                    |  28 kB  00:00:00
(5/27): perl-Filter-1.49-3.el7.x86_64.rpm                                      |  76 kB  00:00:00
(6/27): perl-Getopt-Long-2.40-3.el7.noarch.rpm                                 |  56 kB  00:00:00
(7/27): perl-HTTP-Tiny-0.033-3.el7.noarch.rpm                                  |  38 kB  00:00:00
(8/27): perl-PathTools-3.40-5.el7.x86_64.rpm                                   |  82 kB  00:00:00
(9/27): perl-Encode-2.51-7.el7.x86_64.rpm                                      | 1.5 MB  00:00:00
(10/27): perl-Pod-Simple-3.28-4.el7.noarch.rpm                                 | 216 kB  00:00:00
(11/27): perl-Pod-Perldoc-3.20-4.el7.noarch.rpm                                |  87 kB  00:00:00
(12/27): perl-Pod-Usage-1.63-3.el7.noarch.rpm                                  |  27 kB  00:00:00
(13/27): perl-Scalar-List-Utils-1.27-248.el7.x86_64.rpm                        |  36 kB  00:00:00
(14/27): perl-Socket-2.010-5.el7.x86_64.rpm                                    |  49 kB  00:00:00
(15/27): perl-Text-ParseWords-3.29-4.el7.noarch.rpm                            |  14 kB  00:00:00
(16/27): perl-Time-HiRes-1.9725-3.el7.x86_64.rpm                               |  45 kB  00:00:00
(17/27): perl-5.16.3-299.el7_9.x86_64.rpm                                      | 8.0 MB  00:00:00
(18/27): perl-Time-Local-1.2300-2.el7.noarch.rpm                               |  24 kB  00:00:00
(19/27): perl-Storable-2.45-3.el7.x86_64.rpm                                   |  77 kB  00:00:00
(20/27): perl-Pod-Escapes-1.04-299.el7_9.noarch.rpm                            |  52 kB  00:00:00
(21/27): perl-libs-5.16.3-299.el7_9.x86_64.rpm                                 | 690 kB  00:00:00
(22/27): perl-constant-1.27-2.el7.noarch.rpm                                   |  19 kB  00:00:00
(23/27): perl-macros-5.16.3-299.el7_9.x86_64.rpm                               |  44 kB  00:00:00
(24/27): perl-threads-1.87-4.el7.x86_64.rpm                                    |  49 kB  00:00:00
(25/27): perl-parent-0.225-244.el7.noarch.rpm                                  |  12 kB  00:00:00
(26/27): perl-podlators-2.5.1-3.el7.noarch.rpm                                 | 112 kB  00:00:00
(27/27): perl-threads-shared-1.43-6.el7.x86_64.rpm                             |  39 kB  00:00:00
------------------------------------------------------------------------------------------------------
Total                                                                  30 MB/s |  11 MB  00:00:00
exiting because "Download Only" specified
```

<br>
<br>
<br>

## for VIM
 - gpm-libs: `Libgpm.so.2()(64bit)`
```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package gpm-libs.x86_64 0:1.20.7-6.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package                 Arch                  Version                      Repository           Size
======================================================================================================
Installing:
 gpm-libs                x86_64                1.20.7-6.el7                 base                 32 k

Transaction Summary
======================================================================================================
Install  1 Package

Total download size: 32 k
Installed size: 27 k
Background downloading packages, then exiting:
gpm-libs-1.20.7-6.el7.x86_64.rpm                                               |  32 kB  00:00:00
exiting because "Download Only" specified
```
 - vim-common

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package vim-common.x86_64 2:7.4.629-8.el7_9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package                Arch               Version                          Repository           Size
======================================================================================================
Installing:
 vim-common             x86_64             2:7.4.629-8.el7_9                updates             5.9 M

Transaction Summary
======================================================================================================
Install  1 Package

Total download size: 5.9 M
Installed size: 21 M
Background downloading packages, then exiting:
vim-common-7.4.629-8.el7_9.x86_64.rpm                                          | 5.9 MB  00:00:00
exiting because "Download Only" specified
```
 - vim-filesystem

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package vim-filesystem.x86_64 2:7.4.629-8.el7_9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================
 Package                   Arch              Version                         Repository          Size
======================================================================================================
Installing:
 vim-filesystem            x86_64            2:7.4.629-8.el7_9               updates             11 k

Transaction Summary
======================================================================================================
Install  1 Package

Total download size: 11 k
Installed size: 0
Background downloading packages, then exiting:
vim-filesystem-7.4.629-8.el7_9.x86_64.rpm                                      |  11 kB  00:00:00
exiting because "Download Only" specified
```

<!-- yum install -y gcc-c++ make -->

<br>
<br>
<br>

### wget


```bash
의존성 없음
```

<br>
<br>
<br>

### gcc

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package gcc.x86_64 0:4.8.5-44.el7 will be installed
--> Processing Dependency: cpp = 4.8.5-44.el7 for package: gcc-4.8.5-44.el7.x86_64
--> Processing Dependency: glibc-devel >= 2.2.90-12 for package: gcc-4.8.5-44.el7.x86_64
--> Processing Dependency: libmpfr.so.4()(64bit) for package: gcc-4.8.5-44.el7.x86_64
--> Processing Dependency: libmpc.so.3()(64bit) for package: gcc-4.8.5-44.el7.x86_64
--> Running transaction check
---> Package cpp.x86_64 0:4.8.5-44.el7 will be installed
---> Package glibc-devel.x86_64 0:2.17-326.el7_9 will be installed
--> Processing Dependency: glibc-headers = 2.17-326.el7_9 for package: glibc-devel-2.17-326.el7_9.x86_64
--> Processing Dependency: glibc = 2.17-326.el7_9 for package: glibc-devel-2.17-326.el7_9.x86_64
--> Processing Dependency: glibc-headers for package: glibc-devel-2.17-326.el7_9.x86_64
---> Package libmpc.x86_64 0:1.0.1-3.el7 will be installed
---> Package mpfr.x86_64 0:3.1.1-4.el7 will be installed
--> Running transaction check
---> Package glibc.x86_64 0:2.17-317.el7 will be updated
--> Processing Dependency: glibc = 2.17-317.el7 for package: glibc-common-2.17-317.el7.x86_64
---> Package glibc.x86_64 0:2.17-326.el7_9 will be an update
---> Package glibc-headers.x86_64 0:2.17-326.el7_9 will be installed
--> Processing Dependency: kernel-headers >= 2.2.1 for package: glibc-headers-2.17-326.el7_9.x86_64
--> Processing Dependency: kernel-headers for package: glibc-headers-2.17-326.el7_9.x86_64
--> Running transaction check
---> Package glibc-common.x86_64 0:2.17-317.el7 will be updated
---> Package glibc-common.x86_64 0:2.17-326.el7_9 will be an update
---> Package kernel-headers.x86_64 0:3.10.0-1160.71.1.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                       Arch                  Version                               Repository              Size
========================================================================================================================
Installing:
 gcc                           x86_64                4.8.5-44.el7                          base                    16 M
Installing for dependencies:
 cpp                           x86_64                4.8.5-44.el7                          base                   5.9 M
 glibc-devel                   x86_64                2.17-326.el7_9                        updates                1.1 M
 glibc-headers                 x86_64                2.17-326.el7_9                        updates                691 k
 kernel-headers                x86_64                3.10.0-1160.71.1.el7                  updates                9.1 M
 libmpc                        x86_64                1.0.1-3.el7                           base                    51 k
 mpfr                          x86_64                3.1.1-4.el7                           base                   203 k
Updating for dependencies:
 glibc                         x86_64                2.17-326.el7_9                        updates                3.6 M
 glibc-common                  x86_64                2.17-326.el7_9                        updates                 12 M

Transaction Summary
========================================================================================================================
Install  1 Package  (+6 Dependent packages)
Upgrade             ( 2 Dependent packages)

Total download size: 48 M
Background downloading packages, then exiting:
Delta RPMs disabled because /usr/bin/applydeltarpm not installed.
(1/9): cpp-4.8.5-44.el7.x86_64.rpm                                                               | 5.9 MB  00:00:00     
(2/9): glibc-devel-2.17-326.el7_9.x86_64.rpm                                                     | 1.1 MB  00:00:00     
(3/9): glibc-2.17-326.el7_9.x86_64.rpm                                                           | 3.6 MB  00:00:00     
(4/9): glibc-headers-2.17-326.el7_9.x86_64.rpm                                                   | 691 kB  00:00:00     
(5/9): mpfr-3.1.1-4.el7.x86_64.rpm                                                               | 203 kB  00:00:00     
(6/9): libmpc-1.0.1-3.el7.x86_64.rpm                                                             |  51 kB  00:00:00     
(7/9): gcc-4.8.5-44.el7.x86_64.rpm                                                               |  16 MB  00:00:00     
(8/9): glibc-common-2.17-326.el7_9.x86_64.rpm                                                    |  12 MB  00:00:00     
(9/9): kernel-headers-3.10.0-1160.71.1.el7.x86_64.rpm                                            | 9.1 MB  00:00:00     
------------------------------------------------------------------------------------------------------------------------
Total                                                                                    57 MB/s |  48 MB  00:00:00     
exiting because "Download Only" specified
```

####  - yum installed log

```
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.navercorp.com
 * extras: mirror.navercorp.com
 * updates: mirror.navercorp.com
Resolving Dependencies
--> Running transaction check
---> Package gcc.x86_64 0:4.8.5-44.el7 will be installed
--> Processing Dependency: cpp = 4.8.5-44.el7 for package: gcc-4.8.5-44.el7.x86_64
--> Processing Dependency: glibc-devel >= 2.2.90-12 for package: gcc-4.8.5-44.el7.x86_64
--> Processing Dependency: libmpfr.so.4()(64bit) for package: gcc-4.8.5-44.el7.x86_64
--> Processing Dependency: libmpc.so.3()(64bit) for package: gcc-4.8.5-44.el7.x86_64
--> Running transaction check
---> Package cpp.x86_64 0:4.8.5-44.el7 will be installed
---> Package glibc-devel.x86_64 0:2.17-326.el7_9 will be installed
--> Processing Dependency: glibc-headers = 2.17-326.el7_9 for package: glibc-devel-2.17-326.el7_9.x86_64
--> Processing Dependency: glibc-headers for package: glibc-devel-2.17-326.el7_9.x86_64
---> Package libmpc.x86_64 0:1.0.1-3.el7 will be installed
---> Package mpfr.x86_64 0:3.1.1-4.el7 will be installed
--> Running transaction check
---> Package glibc-headers.x86_64 0:2.17-326.el7_9 will be installed
--> Processing Dependency: kernel-headers >= 2.2.1 for package: glibc-headers-2.17-326.el7_9.x86_64
--> Processing Dependency: kernel-headers for package: glibc-headers-2.17-326.el7_9.x86_64
--> Running transaction check
---> Package kernel-headers.x86_64 0:3.10.0-1160.71.1.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=========================================================================================================================
 Package                       Arch                  Version                                Repository              Size
=========================================================================================================================
Installing:
 gcc                           x86_64                4.8.5-44.el7                           base                    16 M
Installing for dependencies:
 cpp                           x86_64                4.8.5-44.el7                           base                   5.9 M
 glibc-devel                   x86_64                2.17-326.el7_9                         updates                1.1 M
 glibc-headers                 x86_64                2.17-326.el7_9                         updates                691 k
 kernel-headers                x86_64                3.10.0-1160.71.1.el7                   updates                9.1 M
 libmpc                        x86_64                1.0.1-3.el7                            base                    51 k
 mpfr                          x86_64                3.1.1-4.el7                            base                   203 k

Transaction Summary
=========================================================================================================================
Install  1 Package (+6 Dependent packages)

Total download size: 33 M
Installed size: 60 M
Is this ok [y/d/N]: y
Downloading packages:
(1/7): glibc-headers-2.17-326.el7_9.x86_64.rpm                                                    | 691 kB  00:00:00     
(2/7): cpp-4.8.5-44.el7.x86_64.rpm                                                                | 5.9 MB  00:00:00     
(3/7): mpfr-3.1.1-4.el7.x86_64.rpm                                                                | 203 kB  00:00:00     
(4/7): libmpc-1.0.1-3.el7.x86_64.rpm                                                              |  51 kB  00:00:00     
(5/7): kernel-headers-3.10.0-1160.71.1.el7.x86_64.rpm                                             | 9.1 MB  00:00:00     
(6/7): glibc-devel-2.17-326.el7_9.x86_64.rpm                                                      | 1.1 MB  00:00:00     
(7/7): gcc-4.8.5-44.el7.x86_64.rpm                                                                |  16 MB  00:00:00     
-------------------------------------------------------------------------------------------------------------------------
Total                                                                                     35 MB/s |  33 MB  00:00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : mpfr-3.1.1-4.el7.x86_64                                                                               1/7 
  Installing : libmpc-1.0.1-3.el7.x86_64                                                                             2/7 
  Installing : cpp-4.8.5-44.el7.x86_64                                                                               3/7 
  Installing : kernel-headers-3.10.0-1160.71.1.el7.x86_64                                                            4/7 
  Installing : glibc-headers-2.17-326.el7_9.x86_64                                                                   5/7 
  Installing : glibc-devel-2.17-326.el7_9.x86_64                                                                     6/7 
  Installing : gcc-4.8.5-44.el7.x86_64                                                                               7/7 
  Verifying  : kernel-headers-3.10.0-1160.71.1.el7.x86_64                                                            1/7 
  Verifying  : mpfr-3.1.1-4.el7.x86_64                                                                               2/7 
  Verifying  : glibc-devel-2.17-326.el7_9.x86_64                                                                     3/7 
  Verifying  : cpp-4.8.5-44.el7.x86_64                                                                               4/7 
  Verifying  : glibc-headers-2.17-326.el7_9.x86_64                                                                   5/7 
  Verifying  : gcc-4.8.5-44.el7.x86_64                                                                               6/7 
  Verifying  : libmpc-1.0.1-3.el7.x86_64                                                                             7/7 

Installed:
  gcc.x86_64 0:4.8.5-44.el7                                                                                              

Dependency Installed:
  cpp.x86_64 0:4.8.5-44.el7                    glibc-devel.x86_64 0:2.17-326.el7_9 glibc-headers.x86_64 0:2.17-326.el7_9
  kernel-headers.x86_64 0:3.10.0-1160.71.1.el7 libmpc.x86_64 0:1.0.1-3.el7         mpfr.x86_64 0:3.1.1-4.el7            

Complete!
```