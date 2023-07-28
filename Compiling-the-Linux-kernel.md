At the moment of writing (28 July, 2023) there are 2 kernel types that can be used:

* Mainline kernel: The latest stock Linux kernel straight from [kernel.org](https://kernel.org). 
* ChromeOS kernel: Google-customized Linux kernel, currently located [here](https://chromium.googlesource.com/chromiumos/third_party/kernel.git)

There is no way to predict which kernel will be best for which device in the future and therefore you should try testing both to see which one runs better on your device.

Follow these steps with the desired kernel:
1. Download the kernel source code
2. Generate the default config
3. Edit the default config and enable any Chromebook/Google related options you find.
4. Find out which soundcard your Chromebook uses and enable any options related to it.
5. Compile the kernel. This step might take a **very** long time, especially on slower devices.
6. Compile the kernel modules
7. Optional: Compile the kernel headers
8. Optional: Create an initramfs and compile it into the kernel. External initramfs' are not supported by depthcharge.

<h3 align="right"><a href="Preparing-the-distro">CONTINUE TO PREPARING THE DISTRO</a></h3>