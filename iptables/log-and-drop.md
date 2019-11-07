#Log And Drop
Create a Log And Drop chain, to first log all packets not accepted and then drop them.

``` shell
iptables -N LOGANDDROP
iptables -A LOGANDDROP -j LOG --log-prefix "iptables dropped packets " --log-level 7
iptables -A LOGANDDROP -j DROP
```

Any packet you would normally `DROP` should now be sent to `LOGANDDROP`:

``` shell
iptables -A INPUT -j LOGANDDROP
```

Any dropped packet should now appear in your kernal log.

See `man iptables-extensions` for more details.
