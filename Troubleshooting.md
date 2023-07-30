## Distro won't boot for the first time

1. Make sure your Chromebook/box is x86_64 and **NOT** arm/arm64/x86.

2. Make sure developer mode is enabled.

3. Make sure you are **NOT** trying to boot via UEFI or RW_LEGACY. You need to press <kbd>CTRL</kbd> + <kbd>U</kbd> or select "Boot from external media" in the developer menu when booting.

4. If the Chromebook beeps when pressing <kbd>CTRL</kbd> + <kbd>U</kbd>, verify that you set the crossflags correctly in step 3 on [this page](Preparing-the-chromebook|box).

If nothing works, restart from the [first page](Prerequisites) and redo everything.

## Chromebook suddenly shows recovery screen

If you see the recovery screen, that means your Chromebook may have exited developer mode. Reinstall ChromeOS and re-enable developer mode. Then create a new depthcharge image.

**[RESTART FROM THE FIRST PAGE](Prerequisites)**
