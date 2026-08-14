# IT-Knowledge
Knowledge accumulated over the years

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
