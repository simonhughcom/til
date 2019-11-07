# Multiport

Use the multiport module to filter by multiple ports.

``` shell
iptables -A INPUT -p tcp -m multiport --sports 80,443 -j ACCEPT
```
Using the multiport module you can filter up to 15 ports in one rule.

See `man iptables-extensions` for more details.
