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
    4.3. Enable modules that are needed for the storage format which you used when formatting the boot medium in [Preparing the boot medium](Preparing-the-boot-medium)
6. Compile the kernel with `make -j"$(nproc)"`. This step might take a **very** long time, especially on slower devices.
7. Compile the kernel modules with `mkdir kernel-modules && make -j"$(nproc)" modules_install INSTALL_MOD_PATH=mod INSTALL_MOD_STRIP=1`
8. Optional: Compile the kernel headers
9. Optional: Create an initramfs and compile it into the kernel. External initramfs' are not supported by depthcharge.

<h3 align="right"><a href="Preparing-the-distro">CONTINUE TO PREPARING THE DISTRO</a></h3>