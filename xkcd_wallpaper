#!/bin/bash

#TODO: Automatic update when new comic, display title, center image

# /random/comic redirects to random comic. Wget gets the index.html of the comic.
wget http://dynamic.xkcd.com/random/comic/

echo $(pwd)

#Searches the line in the index.html file that points to the url where the actual comic is placed.
#The image urls are of the form: http://imgs.xkcd.com/comics/.'name of comic'.(png | jpg)
url=$(cat index.html | grep -o -m 1 http://imgs.xkcd.com/comics/.*\.png)

#Assuming picture format is .png. Gets the name of the image file by only matching what comes after the last forward slash.
name_pic=$(echo $url | grep -o [^/]*\.png)
is_png=1


#Sets url and name_pic in the case of the picture being in .jpg format.
if [ -z "$url" ]
then
    url=$(cat index.html | grep -o -m 1 http://imgs.xkcd.com/comics/.*\.jpg)
    name_pic=$(echo $url | grep -o [^/]*\.jpg)
    is_png=0   
fi     


#Downloads the image and saves it under its appropriate name.
wget --output-document="$name_pic"  "$url"

#Sets the desktop background
gconftool-2 --set --type=string /desktop/gnome/background/picture_filename $(pwd)/"$name_pic"

#Cleans up
rm index.html

#For some reason, if the image is moved to fast (e.g without a wait) the background does not get set.
sleep 1
 
#The current wallpaper can always be found under "current_xkcd_wallpaper.png" or "current_xkcd_wallpaper.jpg". Also prevents cluttering the directory with images. 
#If you want to keep all the pictures you downloaded, uncomment the following lines.

#Cleans up. Makes sure that there is only one current_xkcd_wallpaper image file.
#rm current_xkcd_wallpaper.*

rm current_xkcd_wallpaper.*

if [ $is_png = 1 ] ; then
    mv $(pwd)/"$name_pic" $(pwd)/current_xkcd_wallpaper.png
else
    mv $(pwd)/"$name_pic" $(pwd)/current_xkcd_wallpaper.jpg
fi
