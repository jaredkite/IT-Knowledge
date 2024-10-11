# Networking
## Helpful tcpdump/Wireshark Filters
### Basic
```
tcpdump -nn -i ens192 host 192.168.0.1 and port 22
tcpdump -nn -i ens192 "host 192.168.0.1 and (port 80 or port 443)"
```
### TCP Flags
`tcpdump -nn -i ens192 host 192.168.0.1 and tcp[tcpflags] & (tcp-rst) != 0`
