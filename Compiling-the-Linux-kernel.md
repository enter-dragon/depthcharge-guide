At the moment of writing (28 July, 2023) there are 2 kernel types that can be used:

* Mainline kernel: The latest stock Linux kernel straight from [kernel.org](https://kernel.org). 
* ChromeOS kernel: Google-customized Linux kernel, currently located [here](https://chromium.googlesource.com/chromiumos/third_party/kernel.git)

There is no way to predict which kernel will be best for which device in the future and therefore you should try testing both to see which one runs better on your device.

Follow these steps with the desired kernel:
1. Download the kernel source code
2. Install all tools and dependencies needed to compile the kernel.
3. Generate the default config with `make defconfig`
4. Edit the default config with `make menuconfig`:  
    4.1. Enable any Chromebook/Google related options you find.  
    4.2. Find out which soundcard your Chromebook uses and enable any options related to it.  
    4.3. Enable modules that are needed for the storage format which you used when formatting the boot medium in [preparing the boot medium](Preparing-the-boot-medium).  
6. Compile the kernel with `make -j"$(nproc)"`. This step might take a **very** long time, especially on slower devices.
7. Compile the kernel modules with `mkdir kernel-modules && make -j"$(nproc)" modules_install INSTALL_MOD_PATH=mod INSTALL_MOD_STRIP=1`
8. Optional: Compile the kernel headers
9. Optional: Create an initramfs and compile it into the kernel. External initramfs' are not supported by depthcharge.
10. Sign the kernel with: `futility vbutil_kernel --arch x86_64 --keyblock /usr/share/vboot/devkeys/kernel.keyblock --signprivate /usr/share/vboot/devkeys/kernel_data_key.vbprivk --bootloader .config --config .config --vmlinuz ./arch/x86/boot/bzImage --pack ./bzImage.signed`

Once you are done compiling the kernel, you will need to install it to the boot medium:
1. You will need to determine the partition name to flash the kernel. It will be either `/dev/insert_devicep1` or `/dev/insert_device1` (notice the p missing in the second example). Once you have it, flash the kernel with: `dd if=/path-to-kernel-source-code/bzImage.signed of=/dev/insert_device1`. Replace `path-to-kernel-source-code` with the appropriate path or wherever you have stored the signed kernel image.
2. Mount the second partition of the storage medium (if you havent already) and copy the kernel modules into /lib/modules (or /usr/lib/modules) on the second partition.
3. Optional: Copy the headers to the appropriate location and create symbolic links for all the required paths.

<h3 align="right"><a href="Preparing-the-chromebook|box">CONTINUE TO PREPARING THE CHROMEBOOK</a></h3>