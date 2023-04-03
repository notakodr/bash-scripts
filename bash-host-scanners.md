# Bash Host Scanners

{% code overflow="wrap" %}
```bash
for ip in $(seq 1 255) do
    ping -c 1 192.168.0.$ip > /dev/null && echo "[*] Online 192.168.0.$ip" done
```
{% endcode %}

{% code overflow="wrap" %}
```bash
for ip in {1..254}; do (ping -c 1 192.168.0.$ip >/dev/null 2>&1 && echo "[*] 192.168.0.$ip is up") & done
```
{% endcode %}
