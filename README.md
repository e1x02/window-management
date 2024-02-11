Window Manager for MacOS
==========================

Fast, fully animated *minimal* window management in less than 0.5mb. Each script toggles between its original position/size and the new position and size with a built-in animation (with no extra permissions).

Requirements
--------------------------

- [skhd](https://github.com/koekeishiya/skhd)
- AppleScript (which is still good)

Setup
--------------------------

1. Download the scripts
2. [Install skhd](https://github.com/koekeishiya/skhd#install)
3. Edit the skhd configuration
4. Start the skhd service with `skhd --install-service; skhd --start-service`
4. Done!

Example skhd configuration
--------------------------

This example uses the keynames for `fn + arrow` keys:

	# Window Resizing
	pagedown : osascript [PATH-TO-SCRIPT]/Center.scpt
	pageup : osascript [PATH-TO-SCRIPT]/Zoom.scpt
	home : osascript [PATH-TO-SCRIPT]/Left.scpt
	end : osascript [PATH-TO-SCRIPT]/Right.scpt


This example uses the keynames for `cmd + arrow` keys 

	# Window Resizing
	cmd - down : osascript [PATH-TO-SCRIPT]/Center.scpt
	cmd - up : osascript [PATH-TO-SCRIPT]/Zoom.scpt
	cmd - left : osascript [PATH-TO-SCRIPT]/Left.scpt
	cmd - right : osascript [PATH-TO-SCRIPT]/Right.scpt


[Examples](https://github.com/koekeishiya/skhd/blob/master/examples/skhdrc) and [keynames](https://github.com/koekeishiya/skhd/issues/1) are available at the [skhd repository](https://github.com/koekeishiya/skhd#configuration). 

Center window
--------------------------

This is the only script that uses the classic AppleScript-style window management (it actually uses the much clunkier AppleScriptObjC bridge to get more accurate screen size information). As a result (because I don't really care about it), there isn't a "restore" window function to this script. You could make one by saving a little `config` plist file and writing that information to it. But that seems like a whole project and this is just a little dot-file exercise.

Fullscreen
--------------------------

There is also a fullscreen script which uses GUI Menu scripting to toggle between fullscreen and otherwise. You may be familiar with Apple's fullscreen window tiling, and you may even be tempted to modify these scripts to support it, but on MacOS Monterey, that is a horrible and buggy experience. 

Why?
--------------------------

I got frustrated with existing window managers (like [Magnet](https://magnet.crowdcafe.com) and [Rectangle](https://rectangleapp.com)) always running in the menubar, and also ranging from 6mb to 30mb just so I could center a window every now and again. [Yabai](https://github.com/koekeishiya/yabai) seems good, but I like animations and System Integrity Protection, so this sacrifices configurability in favor of sleekness.