# Conntrack
Use the conntrack module to create a stateful firewall.

``` shell
iptables -A INPUT -m conntrack --ctstate ESTABLISHED, RELATED -j ACCEPT
```
The conntrack module will keep track of each packets state.
There are a few states but the most important once are:

- `INVALID`: The packet is associated with no known connection.
- `NEW`: The packet has started a new connection.
- `ESTABLISHED`: The packet is associated with a connection which has seen packets in both directions.
- `RELATED`: The packet is starting a new connection, but is associated with an existing connection.

see `man iptables-extensions` for more details.
