# Running Fedora at >1080p resolutions

Here are some things you'll need to do if you want to run Fedora with a monitor at 1440p or 4k or whatever other high resolution.

## Replacing the video drivers

Fedora ships with a set of free graphics drivers called Nouveau. They get the job done, but as far as I can tell, they refuse to work at anything above 1080p. For my NVIDIA drivers, [this tutorial was a godsend](https://kaischroed.wordpress.com/howto-install-nvidia-driver-on-fedora-replacing-nouveau/) ([archived version if link goes down](https://archive.is/M2deU)). Those instructions do involve booting your computer into text-only mode, so make sure you print them or have them open on a different device than the machine you're working on.

## HiDPI scaling

If you're using a really big resolution like 4k, or your monitor is a big TV, you might find that everything is a bit too small at your screen's native resolution. You can fix this by setting GNOME to scale applications up. Open Tweak Tool (if you don't already have it, do `sudo yum install gnome-tweak-tool`), go to the Windows tab, and find the HiDPI option. Bump it up from 1 to 2, and applications will scale themselves to be a more reasonable size on your hi-res display.

If you really don't want to use Tweak Tool, it's also possible to do this from the command line:

```
gsettings set org.gnome.desktop.interface scaling-factor 2
```

Be aware that, while most popular apps handle window scaling properly, many apps will handle it awkwardly or inconsistently, or just outright ignore the scaling. There may be fixes available depending on the application; google is your friend.
