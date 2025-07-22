# Are We Linux Yet

This project is meant to keep track of the viability of the (GNU/)Linux desktop for various use cases.


## Index
<!-- vim-markdown-toc GFM -->

* [General Desktop Usage](#general-desktop-usage)
    * [Note: X11 vs Wayland:](#note-x11-vs-wayland)
* [Misc Graphics Things](#misc-graphics-things)
* [Misc Audio Things](#misc-audio-things)
    * [Note: the audio stack](#note-the-audio-stack)
* [Office](#office)
* [Recording](#recording)
* [Gaming](#gaming)
    * [Note: WINE Is Not an Emulator](#note-wine-is-not-an-emulator)
* [Art](#art)
* [Technical](#technical)
* [Appendix](#appendix)
    * [General Notes](#general-notes)
        * [NVIDIA](#nvidia)
        * [GNOME](#gnome)
    * [I want to switch, what should I keep in mind?](#i-want-to-switch-what-should-i-keep-in-mind)
        * [Do distros matter? Which one is the best?](#do-distros-matter-which-one-is-the-best)
        * [Linux isn't Windows](#linux-isnt-windows)
        * [Window Manager... Desktop Environment... Compositor...](#window-manager-desktop-environment-compositor)

<!-- vim-markdown-toc -->

## General Desktop Usage

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| OS Ads | Not a thing | [KDE added a once per year donation notification](https://invent.kde.org/plasma/plasma-workspace/-/merge_requests/4490), and that was controversial |
| Terminal | Incomparably better than Windows | If the AI craze has proven anything, it's that the CLI interaction method isn't obsolete. Give the terminal with [Zsh](https://zsh.sourceforge.io/) or [Fish](https://fishshell.com/) a genuine try. |
| Window Management | Better than Windows | |
| File Management | Better than Windows | |
| Video/Audio Playing | Comparable to Windows | |
| Web Browsing | Comparable to Windows | |
| Watching Streams | Comparable to Windows | May be gatekept by vendors, but the ones who do may gatekeep everything that isn't a phone or a TV anyway |
| [MIME Types](https://en.wikipedia.org/wiki/Media_type) | Supported | If you want to open a MIME type in a terminal application, there's still no accepted standard way to pick the terminal emulator, the most common MIME openers use and hardcoded list |
| Touch/Gestures | Supported (most DEs have better support on Wayland than on X11) | |

### Note: X11 vs Wayland:
Your graphical session can use one of two protocols to display itself: X11 and Wayland. X11 is about as old as computer graphics, and despite that it only has two effective implementations: [X.Org](https://www.x.org/wiki/), is unmaintained and de facto deprecated, and [XLibre](https://x11libre.org), which has been forked from X.Org and promises to add new feature while not breaking compatibility, but the project is still young and it's controversial for entirely non-technical reasons.

Meanwhile, the much newer [Wayland](https://wayland.app) protocol is still beta quality, will likely never add basic features that are available in every other platform, it has sever implementations, each supporting a different subset of Wayland with still no agreement to what a minimum expected feature set looks like, creating a vast fragmentation, and some popular environments only have at best experimental support for it.


## Misc Graphics Things

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Variable Refresh Rate | Supported | |
| No Screen Tearing | Default (Wayland/XLibre) / Supported (X.Org) | |
| Mixed Refresh Rate | Supported (Wayland) / Eventually (XLibre) / Not planned (X.Org) | |
| Color Management | Supported | Implementations are still being rolled out on Wayland |
| HDR | Supported (Wayland) / Eventually (XLibre) / Not planned (X.Org) | Implementations are still being rolled out on Wayland |
| Lock Screen | Secure (Wayland) / Hack (X11) | |
| Fractional Scaling | Mostly works (Wayland) / Bad (X11) | |
| Screen Saver | Theoretical (Wayland) / Supported (X11) | It's possible to make a screen saver on Wayland by using the same protocol as the lock screen, but nobody seems to care enough to actually do it |


## Misc Audio Things

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Low Latency | Supported ( Linux >= 6.12 ) / Latency spikes (Linux <= 6.11 ) | |
| Midi I/O | Supported | |
| Bluetooth | May require manual configuration | |
| General MIDI playback | Requires manual configuration | If your use case for general MIDI is Windows/DOS games with MIDI soundtrack, good luck |
| Surround | Needs work | |

### Note: the audio stack
[ALSA](https://www.alsa-project.org/wiki/Main_Page) (Advanced Linux Sound Architecture) is the one audio driver on Linux, but using it directly, without painstaking manual configuration, is extremely limited and not even supported by all applications. Applications, instead, interface with a sound server running on top of ALSA, historically [PulseAudio](https://www.freedesktop.org/wiki/Software/PulseAudio/) for general audio and [Jack](https://jackaudio.org/) for low latency audio, but [PipeWire](https://www.pipewire.org/) can easily handle mixed latency audio, and is a drop-in replacement for both.


## Office

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Word Processing | Comparable to Windows | Collaborating with Microsoft Office users may be rough |
| Spreadsheets | Comparable to Windows | Collaborating with Microsoft Office users may be rough |
| Presentations | Comparable to Windows | Collaborating with Microsoft Office users may be rough |
| Email | Competitive | There's Thunderbird and forks, but not much else that's really great |
| Scanners | Possible hardware incompatibility | But the scanners that work, work very well |
| Printers | Possible hardware incompatibility | But the printers that work, work very well |


## Recording

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Screen | Comparable to Windows | A guy left [OBS](https://obsproject.com/) because it doesn't use the GPU efficiently on Linux and started [GPU Screen Recorder](https://git.dec05eba.com/gpu-screen-recorder/about/), use that |
| Window | Comparable to Windows | - Individual window capture isn't supported on [wlroots](https://gitlab.freedesktop.org/wlroots/wlroots)-based Wayland compositors - Some closed source chat programs (namely Discord) may still be using an ancient version of Electron than doesn't support individual window capture on Wayland |
| Webcam | Possible hardware incompatibility | Webcams are generally supported, as long as they are standards compliant |
| Microphone | Possible hardware incompatibility | USB microphones, audio interfaces, and mixers are supported as long as they are standards compliant |
| Streaming | Needs work | The choice is between OBS, which is inefficient, and GPU Screen Recorder, which lacks scenes and compositing |


## Gaming

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Steam (Single player) | Comparable to Windows | It just needs the extra step of enabling Proton Experimental and you're good to go |
| Retrogaming/Emulation | Comparable to Windows | |
| Game Controllers (Wired) | Supported | |
| Virtual Reality | Supported | |
| Non-Steam (Single Player) | Hit or miss, usually hit | |
| Game Controllers (Wireless) | Hit or miss | |
| Multiplayer | Increasingly more gatekept by vendors | Due to the increasing adoption of kernel-level anti-cheat, which will never be supported for several reasons: it's unenforceable with Free Software, the kernel just isn't the place for an arms race, and programs shouldn't have direct access to the computer's inner sanctum without a very good reason. These reasons are good enough that plenty of users that have gaming as primary use case say that non supporting kernel-level anti-cheat isn't a bug, but a feature |

### Note: WINE Is Not an Emulator
[WINE](https://www.winehq.org/) (short for "WINE Is Not an Emulator") is the program that allows Windows software to run on (GNU/)Linux, and, despite how much some software houses might like to claim, WINE is not an emulator, it's a compatibility layer, and it's plain to see to everyone who has even a vague idea that emulation leaves a ton of performance on the table, while games run through WINE at near-native performance. Valve's [Proton](https://github.com/ValveSoftware/Proton) is a software bundle that's mostly WINE, [DXVK](https://github.com/doitsujin/dxvk) and [VKD3D](https://gitlab.winehq.org/wine/vkd3d), together with a wrapper that makes it nicer to use for Steam games.


## Art

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Painting | Comparable to Windows | As long as you like [Krita](https://krita.org/) |
| 3D | Comparable to Windows | As long as you like [Blender](https://www.blender.org/) |
| Image Editing (Vector) | Comparable to Windows | As long as you like [Inkscape](https://inkscape.org/) |
| Raw Editing | Competitive | |
| Video Editing (Proprietary Video Editor) | Competitive | Assuming you can actually get [DaVinci Resolve](https://www.blackmagicdesign.com/products/davinciresolve) to work |
| Pen Tables | Supported | |
| Audio Production (Proprietary DAW) | Not quite there | Decent choice of DAWs, plugins are an headache |
| Image Editing (Raster) | Partially Destructive | [GIMP](https://gimp.org) is the only notable image editor. Effects are non-destructive, but transforms still are. |
| Video Editing (Libre Video Editor) | Needs work | |
| Audio Production (Libre DAW, Linear) | Needs work | Quality Libre plugins are very limited, support for MIDI controllers is limited |
| Audio Production (Libre DAW, Nonlinear) | Needs work | The only real choice of DAW is [Ardour](https://ardour.org/), and the effects workflow needs UI improvements |


## Technical

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Programming | Way better than Windows | Except is you're targeting Windows or the Apple ecosystem, for obvious reasons |
| Slicing | Comparable to Windows | |
| MATLAB | Needs work | [GNU Octave](https://octave.org/) is a thing, but it's not a perfect drop-in replacement |
| CAD | Unviable | [FreeCAD](https://www.freecad.org/) still needs a lot of work before it does anything good enough, [OpenSCAD](https://openscad.org/) is cool concept, but little more than a toy |
| Random Scientific Program | Probably unsupported | |


## Appendix

### General Notes

#### NVIDIA
- Starting from [Mesa](https://mesa3d.org) 25.1, [NVK](https://docs.mesa3d.org/drivers/nvk.html) is enabled by default, making installing the proprietary drivers not as important, although performance as still lackluster.
- It's on your distro to decide if to ship the NVIDIA proprietary drivers or not. If it's important to you, pick a distro that ships them: building them yourself takes a lot of time and it's error prone.
- There may still be graphical glitches on Wayland with the proprietary drivers, but they've been mostly fixed as of the 570 driver, most of those fixes happened between the 555 and 560 drivers.
- Currently, NVIDIA only officially support X.Org as X11 server, it does work with XLibre but it requires [a small configuration](https://github.com/X11Libre/xserver/wiki/Compatibility-of-XLibre#nvidia-proprietary-driver). A distro that ships XLibre as its X11 server may or many not ship that configuration file by default.

#### GNOME
[GNOME](https://www.gnome.org/) on Wayland does not support drawing borders, drop shadows, title bars, etc. (or, in short "Decorations"): it expects the window to draw them by itself (client-side decorations). As you may imagine, this "design choice" (read "Obvious bug they won't fix no matter how much people complain at their doorstep") is controversial because it leads to windows that do not support client-side decorations being drawn without any decorations. GNOME is also a desktop that very much lets perfect be the enemy of good (and thus the main responsible for the slowness of Wayland's development).

The X11 session has been dropped from GNOME 49.

### I want to switch, what should I keep in mind?

#### Do distros matter? Which one is the best?
See [Choosing my First Distro](choosing_my_first_distro.md)

#### Linux isn't Windows
Said like that it sounds obvious, but it can be much harder for it to sink in that it may seem at first glance: a lifetime of habits, assumptions, and conditioning doesn't go away the moment you switch to another OS. If anything, under the hood, (GNU/)Linux is more similar to Mac: the former is a (much improved, and Free as in "free speech") clone of UNIX, and the latter is a true descendant of AT&T UNIX.

And even if moving from Mac to (GNU/)Linux may have less technical challenges (unless you're doing that on a Mac), the biggest challenges go far beyond simply getting used to a new OS: you'll likely have to use new tools for your professional work, and you'll need to get used to interacting directly with community projects rather than yelling on the internet, praying that some corporate people listen to you.

#### Window Manager... Desktop Environment... Compositor...
The terminology is different whether we're talking about an X11 session or a Wayland one.

On X11, you have a graphical server (XLibre or X.Org), which is the part that handles the low level things you don't want to think about, a window manager, which simply keeps track of where the windows are and how big they are, and optionally a compositor, which handles graphical effects and animations. On Wayland, the server, the window manager, and the compositor are merged in a single program, simply called Wayland compositor.

A Desktop Environment (DE for short) is simply a bundle of a Wayland compositor/X11 window manager, some sort of system UI a.k.a shell (you know Window's start menu, the taskbar, and the Windows notifications? Basically, that's the shell), and an application suite.
