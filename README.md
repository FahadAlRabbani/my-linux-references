# my-linux-references
A simple repository to store handy Linux scripts, references, commands, or things I just want to remember.

## Backups / rsync

rsync is a great tool to use for Linux system backups.

Things to remember before running some types of backups:
1. clean out temporary files
2. clean out package cache (for Arch linux)

### Cleaning the package cache (for Arch linux)

To clean out the package cache on Arch linux run the command below.  By default, it will keep the 3 most recent versions of all cached packages regardless if they are installed or not.

`sudo paccache -r`

### Full system backup

Make sure to check list of folders you want to exclude from the backup.  The two last entries in ```--exclude``` are ones I've added as I don't want them backed up.

`sudo rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/home/*/.cache/mozilla","/home/*/VirtualBox VMs"} / /mnt/LocalData/optiblack`

### Remove that files have been deleted in source dir

I have used this command after forgetting to clean the package cache before running full system backup.  When I wanted to remove data from the backup where I had removed data in the source directory, this was how I updated the backup.

`sudo rsync -aAXv --delete /var/cache/pacman/pkg/ /mnt/LocalData/optiblack/var/cache/pacman/pkg`

> NOTE: The trailing '/' at the end of source dir means copy the source directory contents into the target directory without creating a new sub-directory for the files

### References

https://wiki.archlinux.org/index.php/rsync
https://wiki.archlinux.org/index.php/pacman