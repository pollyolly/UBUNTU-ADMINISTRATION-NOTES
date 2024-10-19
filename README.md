### Network Config
Edit network configuration
```
$sudo vim /etc/netplan/00-installer-config.yaml
```
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: false
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
          search: [iwebitechnoloyg.xyz, server1.iwebitechnology.xyz]
          addresses: [8.8.8.8, 8.8.4.4]
          #addresses:
             #- 8.8.8.8 #Google DNS use for name resolution
             #- 8.8.4.4
```
Apply changes in configuration
```
$sudo netplan apply
```
Show network interface name
```
$ip link show
```
Check newtork interface if up and running
```
$ip addr show eth0
```
### Resolved DNS 
Sometimes you need DNS for temporary network configuration. 
```
# vim /etc/resolv.conf

nameserver 8.8.8.8 
nameserver 8.8.4.4
```
### Troubleshooting
This will apply the configuration temporariyly allowing to verify if config is correct. If it doesnt work it will rollback.
```
$sudo netplan try
```
