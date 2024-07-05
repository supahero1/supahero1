Be vary though that while dualboot sounds nice and all, there's one risk associated. It's that you must never access Ubuntu from Windows. Like, if you go on Windows, and you go into file explorer, NEVER try to open the Ubuntu partition in it. You will seriously screw it up by doing this. The filesystems of Windows and Linux are not compatible, which by itself is not a problem if you support both like Linux, but Windows only supports its own filesystem.

There's many dualboot tutorials online, so I won't get into the nitty-gritty here. You can do that by yourself with credible sources. I will however explain it a bit to you.

First of all, you need a USB stick, at least 8GB. Get the [Ubuntu 22.04 ISO](https://releases.ubuntu.com/jammy/ubuntu-22.04.4-desktop-amd64.iso). There's newer Ubuntu versions, but in my experience they are quite unstable, so just stick to that for now.

Get something alike [Rufus](https://github.com/pbatard/rufus/releases/download/v4.5/rufus-4.5.exe). You will need it to "burn" the Ubuntu ISO file onto your USB stick.

Once you do that, plug your USB in, reboot your PC. When it boots up, a lot of BIOSes show what key you have to press to get into it. Smash that key until you get in. If you didn't, just reboot and try again. BIOS is the software that is responsible for actually loading the operating system and starting up your computer. When inside of its settings, navigate to the boot order, and change it so that your USB stick is the first spot on it. Then save changes, quit.

Now, you will be in Ubuntu, but it's only on your USB. Any changes you make here won't affect your disk or even your USB as when you restart, all changes will be lost. However note that if you do something specific like mount your disk, then of course you can make some changes "manually".

It will offer you an installation. Proceed with it. Ubuntu will by itself detect the existing Windows installation and will offer to install itself alongside. Proceed with that.

That's basically it. Consult full tutorials online to see the nitty-gritty details. This was the outline.

As for the customization of Ubuntu, since years I'm using:

- Flat Remix ([1](https://drasite.com/flat-remix-gnome) [2](https://drasite.com/flat-remix) [3](https://drasite.com/flat-remix-gtk) [4](https://extensions.gnome.org/extension/19/user-themes/))

- Dash to Dock ([here](https://extensions.gnome.org/extension/307/dash-to-dock/))

- Gnome Tweaks (terminal: `sudo apt install gnome-tweaks`)

[←](../env/env.md)
