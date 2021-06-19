# hazel-heic2jpg

Use Hazel and a Shell Script to convert HEIC files to JPG


# How to use

## First: Install the Shell Script

1. Download [heic2jpg.sh](https://raw.githubusercontent.com/tjluoma/hazel-heic2jpg/main/heic2jpg.sh). Make sure your browser doesn’t rename it by adding an extension like `.txt` or something. (Looking at you, Safari.)

2. Move it to `/usr/local/bin/heic2jpg.sh`. If you’ve never used `/usr/local/bin/` before you will need to create it:

		sudo mkdir -p /usr/local/bin/

		sudo chown “$LOGNAME” /usr/local/bin/

3. Make it executable:

		chmod 755 /usr/local/bin/heic2jpg.sh

You can install it somewhere else, but you’ll have to change the Hazel rule below:

## Second: Setup the Hazel rule

You should be able to [Download my Hazel rule](https://github.com/tjluoma/hazel-heic2jpg/raw/main/Downloads-HEIC2jpg.hazelrules.zip), unzip it, and import it into Hazel, but it’s good to understand how it works.

![Hazel Overview](https://raw.githubusercontent.com/tjluoma/hazel-heic2jpg/main/img/Hazel-Rule-Overview.png)

**Name:** The name can be whatever you want.

### The “If” Section…

The top section says that it will only match files which have `HEIC` as an extension (note that you do not include the `.` when matching extensions).

I also limit it to matching HEIC files which start with `IMG_` as that is how files are named when I use AirDrop to send a photo from my iPhone to my Mac, but since I never want HEIC files, I guess this part is superfluous.

### The “Do” Section…

**Rename** changes the filename from something like `IMG_8137.heic` and renames it to the date and (24h) time that the picture was taken, such as **”2021-06-18 at 22-35-44.heic”**.

**Run Shell Script** is where we need to tell Hazel to use our script. Click the `i` next to “Edit script” and enter this line:

		/usr/local/bin/heic2jpg.sh "$1"

Hazel will replace `"$1"` with the name of the file which matched. Obviously if you saved the script somewhere other than `/usr/local/bin/heic2jpg.sh` then you’ll need to use that path instead.

(Note that while you _could_ copy the shell script into the Hazel window, I prefer having my scripts external, because it means I can use them _outside_ of Hazel, too.)

Hazel’s embed shell script window should look like this:

![Embedded Shell Script](https://raw.githubusercontent.com/tjluoma/hazel-heic2jpg/main/img/Hazel-Embedded-Shell-Script.png)

**Move to folder “Trash”** will, as you have probably guessed, move the HEIC file to the trash. The `heic2jpg.sh` script will make a _copy_ of the HEIC image as a JPG, so if you don’t send the HEIC file to the trash, it will just sit there.

Note that the JPG will be named something like **2021-06-18 at 22-35-44.jpg** and be placed in the same folder as the original, unless there is already a file with that name in the folder, in which case it will be skipped.

## Questions/Problems/Compliments?

You can find me on [@tjluoma on Twitter](https://twitter.com/tjluoma).

## Disclaimer

Use at your own risk.

This works as far as I know and should definitely not reformat your hard drive and post your taxes and nude selfies to the Dark Web, but if it does that or anything else, well, as the man said…

!["It's not my fault."](https://raw.githubusercontent.com/tjluoma/hazel-heic2jpg/main/img/han.jpg)

