# my-linux-references

## Networking

### Check Network Interface Status & IP Address

```
ip addr
```

### Setting Default Gateway

```
route add default gw 192.168.0.254
```
OR
```
ip route add default via 192.168.0.254 dev enp0s25
```

### Add a DNS Name Server

```
sudo echo "nameserver <IP or FQDN>" >> /etc/resolve.conf
```