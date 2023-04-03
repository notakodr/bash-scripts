# Bash Port Scanners

{% code overflow="wrap" %}
```bash
for port in $(seq 1 65535); do
    (echo PleaseSubscribe > /dev/tcp/192.168.0.1/$port && echo "[*] Port $port is open") 2> /dev/null; done
```
{% endcode %}

{% code overflow="wrap" %}
```bash
for port in {1..65535}; do (echo >/dev/tcp/192.168.0.1/$port) >/dev/null 2>&1 && echo "[*] Port $port is open"; done
```
{% endcode %}
