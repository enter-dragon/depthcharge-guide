As of the current date (28th July 2023), there are two kernel types that can be used:

1. **Mainline kernel:** This is the latest stock Linux kernel directly from [kernel.org](https://kernel.org).

2. **ChromeOS kernel:** This is a Google-customized Linux kernel, currently located [here](https://chromium.googlesource.com/chromiumos/third_party/kernel.git).

There is no definitive way to predict which kernel will work best for each device in the future. Therefore, it is recommended to test both kernels to determine which one performs better on your specific device.

**Follow these steps with the desired kernel:**

1. Download the kernel source code.

2. Install all tools and dependencies needed to compile the kernel.

3. Generate the default config with `make defconfig`.

4. Edit the default config with `make menuconfig`:
   - 4.1. Enable any Chromebook/box or Google related options you find.
   - 4.2. Find out which soundcard your Chromebook/box uses and enable any options related to it.
   - 4.3. Enable modules that are needed for the storage format used when formatting the boot medium in [preparing the boot medium](Preparing-the-boot-medium).

5. Compile the kernel with `make -j"$(nproc)"`. This step might take a **very** long time, especially on slower devices.

6. Compile the kernel modules with `mkdir kernel-modules && make -j"$(nproc)" modules_install INSTALL_MOD_PATH=mod INSTALL_MOD_STRIP=1`.

7. Optional: Compile the kernel headers.

8. Optional: Create an initramfs and compile it into the kernel. External initramfs are not supported by Depthcharge.

9. Create the kernel cmdline:
   - 9.1. Run `blkid -o value -s PARTUUID /dev/insert_rootfs_partition_here`. Replace `insert_rootfs_partition_here` with your rootfs partition. It will be either `/dev/insert_devicep2` or `/dev/insert_device2` (notice the missing 'p' in the second example).
   - 9.2. Create a new file called `cmdline.txt`.
   - 9.3. Paste the following into the file: `loglevel=15 root=PARTUUID=insert_partuuid i915.modeset=1 rootwait rw`. Replace `insert_partuuid` with the output you got in step 9.1.
   - 9.4. Optional: add `security=apparmor` or `security=selinux` at the end if your distro requires that. Not including this may cause your distro not to behave correctly.

10. Sign the kernel with: `futility vbutil_kernel --arch x86_64 --keyblock /usr/share/vboot/devkeys/kernel.keyblock --signprivate /usr/share/vboot/devkeys/kernel_data_key.vbprivk --bootloader cmdline.txt --config cmdline.txt --vmlinuz ./arch/x86/boot/bzImage --pack ./bzImage.signed`.

Once you've finished compiling the kernel, you'll need to install it to the boot medium:

1. Determine the partition name to flash the kernel. It will be either `/dev/insert_devicep1` or `/dev/insert_device1` (notice the missing 'p' in the second example). Once you have it, flash the kernel with: `dd if=/path-to-kernel-source-code/bzImage.signed of=/dev/insert_device1`. Replace `path-to-kernel-source-code` with the appropriate path where you have stored the signed kernel image.

2. Mount the second partition of the storage medium (if you haven't already) and copy the kernel modules into `/lib/modules` (or `/usr/lib/modules`) on the second partition.

3. Optional: Copy the headers to the appropriate location and create symbolic links for all the required paths.

**[CONTINUE TO PREPARING THE CHROMEBOOK/BOX](Preparing-the-chromebook|box)**
