**If your system has successfully booted, follow the next steps:**

1. Set up an internet connection.

2. **Audio:**
   - 2.1. Check if audio works. If all audio devices (internal + external, mic + speakers) work correctly, you can skip the next step.
   - 2.2. IF some audio devices do not work correctly, follow the instructions in [this repository](https://github.com/weirdTreeThing/chromebook-linux-audio). If the link doesn't work, find the Chrultrabook community online and ask them for help.

3. **Non-audio hardware:**
   - 3.1. Check if all devices work (touchscreen, touchpad, keyboard, keyboard backlight, etc.). Keep in mind that not all hardware will necessarily behave the same as it did in ChromeOS.
   - 3.2. If some device doesn't work, check your kernel configuration for an option to enable it.

4. **Keyboard layout:** As of the time of writing, [keyd](https://github.com/rvaiya/keyd) is an excellent choice to remap the keys, as not all actions translate 1:1 from ChromeOS into Linux.

5. **IF** you created an image instead of directly mounting the USB, expand the last partition to fill the whole drive, and do not forget to expand the filesystem inside that partition.
