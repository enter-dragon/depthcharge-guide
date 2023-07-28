As mentioned in [prerequisites](prerequisites), you will need a boot medium.
**EITHER** of the following will work:
* An SD-card.
* A USB-drive.
* Any other kind of storage medium that your Chromebook/box is be able to read.

<br></br>

Once you have your storage medium, follow the steps below. **Replace `insert_device` with your storage name.**
1. Make sure there are no important files on it as wiping will delete everything.
2. Wipe the drive, either via GUI or with `wipefs -af /dev/insert_device`. Be careful to not accidentally wipe the wrong device.
3. Create a gpt layout with `parted -s /dev/insert_device mklabel gpt`
4. Create the kernel partition with `parted -s -a optimal /dev/insert_device unit mib mkpart Kernel 1 insert_size`. Replace `insert_size` with your kernel size in mb + 20mb. For example, if your kernel is 60mb, replace `insert_size` with `70`.
5. Create the rootfs partition with `parted -s -a optimal /dev/insert_device unit mib mkpart Root insert_size 100%` Replace `insert_size` with the number you used in the previous step.
6. Add the correct labels to the kernel partition with `cgpt add -i 1 -t kernel -S 1 -T 5 -P 15 /dev/insert_device`
7. To format the rootfs partition, you will need to figure out what its called. It will be either `/dev/insert_devicep2` or `/dev/insert_device2` (notice the p missing in the second example). Once you have your device partition, format it with `mkfs.ext4 /dev/insert_device_with_partition`. You can also use other storage formats, for example `mkfs.btrfs` or `mkfs.f2fs`.

<h3 align="right"><a href="Preparing-the-distro">CONTINUE TO PREPARING THE DISTRO</a></h3>