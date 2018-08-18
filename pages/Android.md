# my-linux-references

## Android

Working with Android

### Mounting Android USB

To mount Android when plugging in through USB to access the files you can do the following.

Create a mount point such as /mnt/Android

Download and install simple-mtpfs (https://github.com/phatina/simple-mtpfs) or in the AUR.

```
sudo simple-mtpfs --device 1 /mnt/Androud
```
After that you should be abled to access the Android filesystem through the mount point

Note: You may need to be root or use sudo in order to access this mount point depending on your system


Simply run `sudo unmount /mnt/Android` before unplugging the phone to ensure no files are being accessed.