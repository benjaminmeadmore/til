# Default Screenshot Location

You can use various keyboard shortcuts on your Mac to take pictures of your screen. These files are defacto saved to the desktop.

- To capture the entire screen, hold down the shortcut `cmd+shift+3`.
- To capture a portion of the screen, hold down the shortcut `cmd+shift+4`.
- To open the Screenshot editor on macOS, hold down the shortcut `cmd+shift+5`.

Now whilst it can be painful to watch your desktop fill up with clutter this way, screenshots can be dumped somewhere else. For instance, if you'd like your screenshots to be saved in the `~/screenshots` directory, then enter the following commands:

```bash
$ mkdir ~/screenshots
$ defaults write com.apple.screencapture location ~/screenshots
$ killall SystemUIServer
```

[source](http://osxdaily.com/2011/01/26/change-the-screenshot-save-file-location-in-mac-os-x/)