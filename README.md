What this script does
---------------------
It downloads a random xkcd comic from xkcd.com and sets it as your desktop background. The image file gets saved under `current_xkcd_wallpaper.(png | jpg)`. 

How to use it
-------------
Get `xkcd_wallpaper.sh` either by cloning or downloading the file. Run it from the terminal, with a keyboard shortcut or with a custom application launcher. You can run the script with `sh xkcd_wallpaper.sh` or `./xkcd_wallpaper.sh`. The file `current_xkcd_wallpaper.(png | jpg)` gets saved in the current working directory of the shell. So if you run it from a keyboard shortcut or a custom application launcher this will be your HOME directory. 

Additional remarks
-----------------
* I have only tested this script on ubuntu 10.04 and 10.10.
* To see which file is currently set as wallpaper. Run `gconf-editor` and have a look at the value `/desktop/gnome/background/picture_filename`. This file will not exist anymore though, as it gets moved to `current_xkcd_wallpaper.(png | jpg)`
* Running the script with a keyboard shortcut set in the ubuntu Keyboard Shortcuts menu does not work for the moment. It does work with compiz keyboard shortcuts though. 
* Running it with cron did not work either when I tested it. I will look into this issue as well. Please let me know if it works on your computer.
* If you have any feedback (negative or positive) drop me an e-mail at basil.philipp@gmail.com
