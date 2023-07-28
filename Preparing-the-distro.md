First off, you need to chose a distro. Keep in mind that there are multiple caveats with distros:  
Note: Rootfs refers to the root file system, i.e. all files needed for the distro to boot into at least a tty environment.
1. Some distros provide clean rootfs tars. Keep in mind that cloud/server/container rootfs versions might need a lot of cleaning.
2. If you cannot find a rootfs, try to bootstrapp the distro locally.
3. If you cannot find a rootfs or bootstrap the distro manually, extract the rootfs from the live image squashfs. Keep in mind that some live images do not have rootfs squashfs at all.

Once you have your distro, proceed with the steps below:
1. Mount the second partition of your drive, the one that was formatted in step 7 in [preparing the boot medium](Preparing-the-boot-medium).
2. Extract the rootfs into the mounted partition. If you extract everything correctly, you should get the following results (replace `/mnt/usb_drive` with whatever directory you mounted the partition under). You might not have all the folders from below, due to all distros being different.  
```
$ ls /mnt/usb_drive/
bin   dev  home  lib64  opt   root  sbin  sys  usr
boot  etc  lib   mnt    proc  run   srv   tmp  var
```
3. Chroot into the partition with `sudo chroot /mnt/usb_drive/` replace `/mnt/usb_drive` with whatever directory you mounted the partition under.  
4. Create a new user with:  
    4.1. Create user: `useradd --create-home --shell /bin/bash insert_username` Replace insert_username with the username you want.  
    4.2. Set password: `passwd insert_username`  
    4.3. Add root permissions: `usermod -aG doas insert_username`. You might need to replace `sudo` with `wheel` or `doas`, depending on your distro.  
5. 
