# my-linux-references
A simple repository to store handy Linux scripts, references, commands, or things I just want to remember.

## Backups / rsync

rsync is a great tool to use for Linux system backups.

Things to remember before running some types of backups:
1. clean out temporary files
2. clean out package cache (for Arch linux)

### Full system backup
`sudo rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/home/*/.cache/mozilla","/home/*/VirtualBox VMs"} / /mnt/LocalData/optiblack`

### Remove files have been deleted in source dir

I have used this command after forgetting to clean the package cache before running full system backup.  When I wanted to remove data from the backup where I had removed data in the source directory, this was how I updated the backup.

`sudo rsync -aAXv --delete /var/cache/pacman/pkg/ /mnt/LocalData/optiblack/var/cache/pacman/pkg`
