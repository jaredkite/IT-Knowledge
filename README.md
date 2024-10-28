# IT-Knowledge
Knowledge accumulated over the years

## Systems
### BASH Scripting
#### Shell Startup Modes
```
    ----------------------------------
    |
    |
 N  |
    |
    |
    ----------------------------------
    |
    |
 Y  |
    |
    |
    -----------------------------------
```
### Resource Usage
#### Memory
#### CPU
`mpstat -P ALL 2 10000 | tee <file>`
#### I/O
`iostat -dy -x 2 10000 | tee <file>`
#### Network
`sar -n DEV 2 10000`

#### PAM Limits
`ulimit -a`

#### Kernel Tuning


## Networking
[Networking](NETWORKING.md)
### Encapsulation
- Layer 2 (i.e.: Ethernet)
- Layer 3 (i.e.: IP)
- Layer 4 (i.e.: TCP)

### Common Misconfigurations
#### MTU
Path MTU (PMTUD) Discovery Process

```
nmcli con show ens192
nmcli con mod ens192 802-3-ethernet.mtu 1500
```
### Troubleshooting
#### Connectivity
#### Traffic
#### Throughput


## Automation

## DevOps
