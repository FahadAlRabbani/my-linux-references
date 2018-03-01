# my-linux-references

## NFS (Network File System) - Arch Linux

### Install NFS Client / Server in Arch Linux

```
sudo pacman -Syu nfs-utils
```

## NFS (Network File System) - OpenSuSE Linux

### Install NFS Client / Server in OpenSuSE Linux

```
sudo zypper install nfs-client nfs-kernel-server 
```

### Start RPCBind and NFS Server Services

```
systemctl enable rpcbind
systemctl start rpcbind
systemctl enable nfsserver
systemctl start nfsserver
```

## NFS (Network File System) - Common Server Setup

### Export an NFS Share

Create a folder to be shared or identify a path to be shared
```
mkdir /home/eric/NFS-Share
```

Exit the /etc/exports folder
```
sudo vim /etc/exports
```

Add the export line (few examples):
```
/path/to/folder <client ip, name, or subnet>(options)
/home/eric/NFS-Share 192.168.1.161(rw)
/home/eric/NFS-Share 192.168.1.0/24(ro)
/home/eric/NFS-Share clientname(rw,sync)
```

Export the shares in the /etc/exports folder (only required if nfsservice is running)
```
sudo exportfs -a
```
Restart the rpcbind and nfsserver services

```
systemctl restart rpcbind
systemctl restart nfsserver
```

## NFS (Network File System) - Common Client Setup

### Check sharers on server from Client

```
showmount -e <server name or IP>
```

### Mount NFS share to local directory

```
sudo mount -t nfs <server name or IP>:/nfs/share/path /path/to/mount
```

Run mount to verify the folder has been mounted and do any further testing required as checking read or write capabilities
