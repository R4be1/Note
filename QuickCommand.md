## Quick and easy to use fscan.
curl -#L https://github.com/shadow1ng/fscan/releases/download/1.8.3/fscan -o /tmp/fscan && chmod +x /tmp/fscan && (nohup /tmp/fscan -h 10.0.200.3/24 -o /tmp/results.txt > /dev/null 2>&1 &) && echo FscanRunning

## Quick and easy to use Masscan -> results.txt`ip:port`
sudo ./masscan -p- --rate=1000 -iL ../ips.txt -oL results.txt && awk '{print $4 ":" $3}' results.txt
