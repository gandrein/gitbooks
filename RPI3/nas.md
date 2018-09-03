# Mounting NAS drives

## Samba Drives

On my current distribution (dietpi) I have been having difficulties mounting the TP-LINK DD-WRT Samba based NAS.

Typically I was getting the following error
```
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

According to the forums it had to do with the version of the Samba client/server. Of all the tries, the following simply worked
```
mount -t cifs -o username=<user>,password=<pwd>,rw,vers=1.0 //192.168.100.1/ddwrt-plexshare/MediaPlex /mnt/MediaPlexNas
```

**Note** the `vers=1.0` argument which is without `""`. Haven't tested if placing it at the end of the list of args made the difference.

After placing this in `/etc/fstab`, formated as below and tested with `sudo mount -a`
```
//192.168.100.1/ddwrt-plexshare/MediaPlex /mnt/MediaPlexNas cifs username=<user>,password=<pwd>,rw,vers=1.0
```
everything was good.