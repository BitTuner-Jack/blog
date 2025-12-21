1. 查看 1455 端口是否被排除：

```kotlin
netsh interface ipv4 show excludedportrange protocol=tcp
```

2. 如果被排除了，重启 WinNAT 服务：

```bash
net stop winnat
net start winnat
```

