# Networking
## Helpful tcpdump/Wireshark Filters
### Basic
```
tcpdump -nn -i ens192 host 192.168.0.1 and port 22
tcpdump -nn -i ens192 "host 192.168.0.1 and (port 80 or port 443)"
```
### TCP Flags
#### Reset
`tcpdump -nn -i ens192 "host 192.168.0.1 and tcp[tcpflags] & (tcp-rst) != 0"`
#### ECN-Echo - Explicit Congestion Notification
`tcpdump -nn -i ens192 "port 22 and (tcp[13] & 0xc0 != 0)"`

### Multicast
`tcpdump -nn -i ens192 net 224.0.0.0/8`
#### VRRP Traffic
`tcpdump -nn -i ens192 host 224.0.0.18`
