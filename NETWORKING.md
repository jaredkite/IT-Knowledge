# Networking
## Helpful tcpdump/Wireshark Filters
### Basic
```
tcpdump -nn -i ens192 host 192.168.0.1 and port 22
tcpdump -nn -i ens192 "host 192.168.0.1 and (port 80 or port 443)"
```
### TCP Flags
The TCP flags exist in the 13th octet of the TCP header. 
|C|E|U|A...
#### Reset
`tcpdump -nn -i ens192 "host 192.168.0.1 and tcp[tcpflags] & (tcp-rst) != 0"`
#### Congestion Experienced
If both ends and the underlying network supports ECN. The fact that congestion happened
is indicated in the second octet of the IP header. ECN is negotiated during the setup
of a new connection and indicated in the SYN and SYN-ACK packets.

`tcpdump -nn -i ens192 "ip[1] & 0x03 == 0x03"`
#### ECN-Echo - Explicit Congestion Notification
`tcpdump -nn -i ens192 "port 22 and (tcp[13] & 0xc0 != 0)"`

### Multicast
`tcpdump -nn -i ens192 net 224.0.0.0/8`
#### VRRP Traffic
`tcpdump -nn -i ens192 host 224.0.0.18`

## Data Encapsulation
The following diagram illustrates how data is packaged up in multiple layers of encapsulation before it is sent across a computer network. When data is received by a computer on a computer network, the data is unencapsulated in the opposite order and eventually presented to the application. In this case the application could be a web browser.
```
Application (i.e.: web browser)
Application Data
               |
               V
Layer 5 - Session (i.e.: HTTPS Data)
[ HTTP Header ][ Application Data ]
               |
               V
Layer 4 - Transport (i.e.: TCP Segment)
[ TCP Header ][[ HTTP Header ][ Application Data ]]
               |
               V
Layer 3 - Network (i.e.: IP Packet):
[ IP Header ][[ TCP Header ][[ HTTP Header ][ Application Data ]]]
               |
               V
Layer 2 - Data Link (i.e.: Ethernet Frame):
[ Ethernet Header ][[ IP Header ][[ TCP Header ][[ HTTP Header ][ Application Data ]]]]                 
```
## Common Misconfigurations
### MTU
Path MTU (PMTUD) Discovery Process

```
nmcli con show ens192
nmcli con mod ens192 802-3-ethernet.mtu 1500
```
