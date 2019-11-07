# Common Rules
A List of common iptable rules and commands.

Flush all rules and delete all chains.
``` shell
iptables -F
iptables -X
```

Only allow outgoing pings, reject incoming pings.
``` shell
iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
```

Allow all loopback connections.
``` shell
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
```

## Stateful Rules
The following rules are all stateful, they will only allow incoming traffic if it is `ESABLISHED,RELATED`

Allow HTTP connections.
``` shell
iptables -A INPUT -p tcp -m tcp --sport 80 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 80 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```

Allow HTTPS connections.
``` shell
iptables -A INPUT -p tcp -m tcp --sport 443 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 443 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```

Allow DNS connections.
``` shell
iptables -A INPUT -p udp -m udp --sport 53 -m conntrack --ctstate ESTABLISHED,RELATED  -j ACCEPT
iptables -A OUTPUT -p udp -m udp --dport 53 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```

Allow SSH connections.
``` shell
iptables -A INPUT -p tcp -m tcp --sport 22 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
```



