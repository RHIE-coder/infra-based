# Redis

[origin guide site](https://redis.io/docs/getting-started/installation/install-redis-on-linux/)

## Ubuntu

```bash
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

sudo apt-get update
sudo apt-get install redis
```
 - check
```bash
sudo systemctl status redis-server
```

### redis-server
### redis-tools( redis-cli )