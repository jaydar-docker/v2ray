# V2Ray

### 0x01 Pull
```bash
docker pull jaydar/v2ray
```

### 0x02 Create directory
```bash
mkdir -p ~/Docker/v2ray
```

### 0x03 Run

```bash
docker run --name v2ray -d -p 9899:9899 -p 9899:9899/udp jaydar/v2ray

docker run --name v2ray -d -p 9899:9899 -p 9899:9899/udp  -v ~/Docker/V2Ray:/etc/v2ray/ jaydar/v2ray
```
### 0x04 config.json
```json
{
    "log": {
        "access": "/var/log/v2ray/access.log",
        "error": "/var/log/v2ray/error.log",
        "loglevel": "warning"
    },
    "inbounds": [
        {
            "protocol": "shadowsocks",
            "port": 9899,
            "settings": {
                "method": "aes-256-cfb",
                "password": "darcy",
                "network": "tcp,udp",
                "level": 1,
                "ota": false
            }
        }
    ],
    "outbounds": [
        {
            "protocol": "freedom",
            "settings": {},
            "tag": "direct"
        }
    ],
    "dns": {
        "servers": [
            "8.8.8.8",
            "8.8.4.4",
            "114.114.114",
            "localhost"
        ]
    },
    "transport": {
        "kcpSettings": {
            "uplinkCapacity": 100,
            "downlinkCapacity": 100,
            "congestion": true
        }
    }
}
```