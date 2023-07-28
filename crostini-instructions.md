First of all, some devices do not support privileged containers (which are required to make loop images). As of time of writing (28 July, 2023) the whole octopus board family does not allow privileged containers.

You do not need developer mode for building with Crostini (although you will need developer mode if you plan to install the image on that Chromebook/box).

Instructions to run a privileged container:
1. Set up "Linux" in the ChromeOS settings. If you already have it set up, skip this step.
2. Press <kbd>CTRL</kbd><kbd>ALT</kbd><kbd>T</kbd> to open the ChromeOS terminal
3. Type ``shell`` and press <kbd>Enter</kbd>
4. Paste the command from below and press <kbd>Enter</kbd>

```
vmc stop termina; vmc start termina | exit; vmc container termina penguin --privileged true 2>/dev/null 1>/dev/null; sleep 10; vmc container termina penguin --privileged true
```
5. Wait for the command to execute
6. Create an empty image: `fallocate -l 12G depthcharge.img` (you can adjust the `12G` if your image needs more/less space)
7. Mount the image as loop device: `losetup -f --show depthcharge.img`. Make a note of what this command returns. Use it whenever the guide prompts you for a boot medium/device path/partition.