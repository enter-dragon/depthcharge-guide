If your system booted successfully, proceed with the next steps:
1. Set up an internet connection.  
2. Audio:  
    2.1. Check if audio works. If all audio devices (internal + external, mic + speakers) work correctly, then you can skip the next step.  
    2.2. IF some audio devices do not work correctly, follow the instructions in [this repo](https://github.com/weirdTreeThing/chromebook-linux-audio). If that link doesnt work, find the Chrultrabook community online and ask them for help.  
3. Non-audio hardware:  
    3.1. Check if all devices work (touchscreen, touchpad, keyboard, keyboard backlight, etc...). Keep in mind that not all hardware will necessarily behave 1:1 compared to ChromeOS.  
    3.2. If some device doesnt work, check your kernel config for an option to enable it.  
4. Keyboard layout. As of time of writing, [keyd](https://github.com/rvaiya/keyd) is an awesome choice to remap the keys, as not all actions translate 1:1 from ChromeOS into Linux.