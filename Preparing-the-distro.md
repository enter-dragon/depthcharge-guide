**Choosing a Distro:**

Before proceeding, you need to choose a distro. Please keep in mind the following caveats:

Note: Rootfs refers to the root file system, i.e., all files needed for the distro to boot into at least a tty environment.

1. Some distros provide clean rootfs tars. However, cloud/server/container rootfs versions might require additional cleaning.

2. If you cannot find a rootfs, try to bootstrap the distro locally.

3. If you cannot find a rootfs or manually bootstrap the distro, extract the rootfs from the live image squashfs. Be aware that some live images may not have a rootfs squashfs at all.

**Steps:**

Once you have chosen your distro, proceed with the following steps:

1. Mount the second partition of your drive, the one that was formatted in step 7 in [preparing the boot medium](Preparing-the-boot-medium).

2. Extract the rootfs into the mounted partition. If you extract everything correctly, you should get the following results (replace `/mnt/usb_drive` with whatever directory you mounted the partition under). Note that the folder structure may vary depending on the distro.
```
$ ls /mnt/usb_drive/
bin   dev  home  lib64  opt   root  sbin  sys  usr
boot  etc  lib   mnt    proc  run   srv   tmp  var
```

3. Chroot into the partition with `sudo chroot /mnt/usb_drive/`. Replace `/mnt/usb_drive` with whatever directory you mounted the partition under.

4. Create a new user with the following commands:
    - 4.1. Create user: `useradd --create-home --shell /bin/bash insert_username`. Replace `insert_username` with the desired username.
    - 4.2. Set password: `passwd insert_username`.
    - 4.3. Add root permissions: `usermod -aG sudo insert_username`. You may need to replace `sudo` with `wheel` or `doas`, depending on your distro.

**[CONTINUE TO COMPILING THE LINUX KERNEL](Compiling-the-Linux-kernel)**
