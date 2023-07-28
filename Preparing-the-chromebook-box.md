1. Put your Chromebook/box into developer mode. This might not be possible if your device is enrolled/managed by a school/organization.
2. Open the ChromeOS shell by pressing <kbd>CTRL</kbd><kbd>ALT</kbd><kbd>T</kbd>, type `shell` and press <kbd>Enter</kbd>.
3. Enable USB and Custom Kernel Booting with: `sudo crossystem dev_boot_usb=1 dev_boot_signed_only=0`
4. Plug in your storage medium and reboot the Chromebook/box.
5. Press <kbd>CTRL</kbd><kbd>U</kbd> or select boot from external on the developer screen.
6. Wait for the system to boot. In case it doesnt see [troubleshooting](troubleshooting).
7. Once the system boots, set up an internet connection.
8. Check if audio works. If all audio devices (internal + external, mic + speakers) work, then you can skip the next step.
9. IF not all audio devices work, follow the instructions in [this repo](https://github.com/weirdTreeThing/chromebook-linux-audio)