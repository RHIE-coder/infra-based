# Redis

[origin guide site](https://redis.io/docs/getting-started/installation/install-redis-on-linux/)

## Centos 

```bash
sudo yum install epel-release yum-utils
sudo yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
sudo yum-config-manager --enable remi
```

### redis-server
### redis-tools( redis-cli )

<br>
<br>
<br>
<hr>
<br>
<br>
<br>

#### `Manual Installation` (오류가 많아 추천하지 않음)

```bash
sudo yum install redis
```

```bash
tar -xzvf redis-stable.tar.gz
cd redis-stable
make
```

### Error 발생시

```
yum install gcc
cd deps
make hiredis jemalloc linenoise lua
```
```
cd ..
make install
```