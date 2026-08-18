# IT-Knowledge
This is a work in progress. I'm collecting hard-won knowledge accumulated over the years. This is mostly intended to be a reference for myself. Hopefully there a few other people who find it useful as well.

## Systems
### BASH Scripting
#### Bash Shell Startup Modes
What scripts are executed during Bash startup and in what order? Lookup your situation in the table based on how Bash is being initialized. A regular login is typically Login=Yes and Interactive=Yes.

Typical RHEL Behavior
<table class="tg"><thead>
  <tr>
    <th class="tg-0lax" colspan="2" rowspan="2"></th>
    <th class="tg-1wig" colspan="2">Interactive Shell?</th>
  </tr>
  <tr>
    <th class="tg-1wig">No</th>
    <th class="tg-1wig">Yes</th>
  </tr></thead>
<tbody>
  <tr>
    <td class="tg-1wig" rowspan="2">Login Shell?</td>
    <td class="tg-1wig">No</td>
    <td class="tg-0lax">$BASH_ENV</td>
    <td class="tg-0lax">~/.bashrc; source /etc/bashrc</td>
  </tr>
  <tr>
    <td class="tg-1wig">Yes</td>
    <td class="tg-0lax">/etc/profile; Then first found of: ~/.bash_profile, ~/.bash_login, or ~/.profile</td>
    <td class="tg-0lax">/etc/profile; Then first found of: ~/.bash_profile, ~/.bash_login, or ~/.profile</td>
  </tr>
</tbody>
</table>



### Resource Usage
#### Memory
#### CPU Usage
`mpstat -P ALL 2 10000 | tee <file>`
#### I/O Usage
`iostat -dy -x 2 10000 | tee <file>`
#### Network Utilization
`sar -n DEV 2 10000`

#### PAM Limits
`ulimit -a`

#### Kernel Tuning

## [Networking](NETWORKING.md)
### Encapsulation
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
