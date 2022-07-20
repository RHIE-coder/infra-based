# 환경셋팅

## 🌈CentOS 7

[Download CentOS 7](https://www.centos.org/download/)


## 🌈Prerequsite


### - IP 확인하기
```
yum -y install net-tools
ifconfig
```

OR

```
ip addr
```

### - SSH

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

### - Utilities

```
yum install -y vim
```