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
| OS Ads | Not a thing | KDE added a once per year donation notification, and that was controversial |
| Terminal | Incomparably better than Windows | If the AI craze has proven anything, it's that the CLI interaction method isn't obsolete. Give the terminal with Zsh or Fish a genuine try. |
| Window Management | Better than Windows | |
| File Management | Better than Windows | |
| Video/Audio Playing | Comparable to Windows | |
| Web Browsing | Comparable to Windows | |
| Watching Streams | Comparable to Windows | May be gatekept by vendors, but the ones who do may gatekeep everything that isn't a phone or a TV anyway |
| MIME Types | Supported | If you want to open a MIME type in a terminal application, there's still no accepted standard way to pick the terminal emulator, the most common MIME openers use and hardcoded list |
| Touch/Gestures | Supported (Wayland) / Hack (X11) | |

### Note: X11 vs Wayland:
Your graphical session can use one of two protocols to display itself: X11 and Wayland. X11 is about as old as computer graphics, and despite that it only has one effective implementation: X.Org, which nobody wants to develop, so it's unmaintained and de facto deprecated. Despite that, the much newer Wayland is still beta quality, and some popular environments only have at best experimental support for it.


## Misc Graphics Things

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Variable Refresh Rate | Supported | |
| Mixed Refresh Rate | Supported (Wayland) / Not planned (X11) | |
| ICC Profiles | Compositor dependant (Wayland) / Supported (X11) | On Wayland only KDE Plasma fully supports ICC profiles in a stable release |
| HDR | Compositor dependant (Wayland) / Not planned (X11) | On Wayland, it's the same exact protocol as ICC profiles, support will improve at the same rate |
| Lock Screen | Secure (Wayland) / Hack (X11) | |
| Screen Saver | Theoretical (Wayland) / Supported (X11) | It's possible to make a screen saver on Wayland by using the same protocol as the lock screen, but nobody seems to care enough to actually do it |
| Fractional Scaling | Needs work (Wayland) / Bad (X11) | Mostly, it's GTK apps that need work at the toolkit level, but GTK is also the most popular toolkit |


## Misc Audio Things

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Low Latency | Supported ( Linux >= 6.12 ) / Latency spikes (Linux <= 6.11 ) | |
| Midi I/O | Supported | |
| Bluetooth | May require manual configuration | |
| General MIDI playback | Requires manual configuration | If your use case for general MIDI is Windows/DOS games with MIDI soundtrack, good luck |
| Surround | Needs work | |

### Note: the audio stack
ALSA (Advanced Linux Sound Architecture) is the one audio driver on Linux, but using it directly, without painstaking manual configuration, is extremely limited and not even supported by all applications. Applications, instead, interface with a sound server running on top of ALSA, historically PulseAudio for general audio and Jack for low latency audio, but PipeWire can easily handle mixed latency audio, and is a drop-in replacement for both.


## Office

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Word Processing | Comparable to Windows | Collaborating with Microsoft Office users may be rough |
| Spreadsheets | Comparable to Windows | Collaborating with Microsoft Office users may be rough |
| Presentations | Comparable to Windows | Collaborating with Microsoft Office users may be rough |
| Email | Taste dependant | There's no notable 3-pane client if you're into that |
| Scanners | Possible hardware incompatibility | But the scanners that work, work very well |
| Printers | Possible hardware incompatibility | But the printers that work, work very well |


## Recording

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Screen | Comparable to Windows | A guy left OBS because it doesn't use the GPU efficiently on Linux and started GPU Screen Recorder, use that |
| Window | Comparable to Windows | - Individual window capture isn't supported on wlroots-based Wayland compositors - Some closed source chat programs (namely Discord) may still be using an ancient version of Electron than doesn't support individual window capture on Wayland |
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
WINE (short for "WINE Is Not an Emulator") is the program that allows Windows software to run on (GNU/)Linux, and, despite how much some software houses might like to claim, WINE is not an emulator, it's a compatibility layer, and it's plain to see to everyone who has even a vague idea that emulation leaves a ton of performance on the table, while games run through WINE at near-native performance. Valve's Proton is a software bundle that's mostly WINE with experimental patches, together with a wrapper that makes it nicer to use for Steam games.


## Art

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Painting | Comparable to Windows | As long as you like Krita |
| 3D | Comparable to Windows | As long as you like Blender |
| Image Editing (Vector) | Comparable to Windows | As long as you like Inkscape |
| Raw Editing | Competitive | |
| Video Editing (Proprietary Video Editor) | Competitive | Assuming you can actually get DaVinci Resolve to work |
| Pen Tables | Supported | |
| Audio Production (Proprietary DAW) | Not quite there | Decent choice of DAWs, plugins are an headache |
| Image Editing (Raster) | Destructive | GIMP is the only notable image editor. Stable is entirely destructive, experimental has non-destructive layer effects, but it still needs several workflow improvements and some tools on top of finishing the transition to a non-destructive workflow to be competitive against proprietary software |
| Video Editing (Libre Video Editor) | Needs work | |
| Audio Production (Libre DAW, Linear) | Needs work | Quality Libre plugins are very limited, support for MIDI controllers is limited |
| Audio Production (Libre DAW, Nonlinear) | Needs work | The only real choice of DAW is Ardour, d, and the effects workflow needs UI improvements |


## Technical

| Use Case | Readiness | Notes |
| :------- | :---------| :-----|
| Programming | Way better than Windows | Except is you're targeting Windows, for obvious reasons |
| Slicing | Comparable to Windows | |
| MATLAB | Needs work | GNU Octave is a thing, but it's not a perfect drop-in replacement |
| CAD | Unviable | FreeCAD still needs a lot of work before it does anything good enough, OpenSCAD is cool concept, but little more than a toy |
| Random Scientific Program | Probably unsupported | |


## Appendix

### General Notes

#### NVIDIA
- Starting from Mesa 24.1, the NVK driver is shipped by default, so, on Turing (20xx/16xx) and later cards, you only really need to care about the proprietary drivers if you care about compute, as long as the distro ships a recent-enough version of Mesa. (The latest Debian (Debian 12) and Ubuntu LTS (Ubuntu 24.04 LTS) and derivatives have not received the update yet)
- It's on your distro to decide if to ship the NVIDIA proprietary drivers or not. If it's important to you, pick a distro that ships them: building them yourself takes a lot of time and it's error prone.
- There may still be graphical glitches on Wayland with the proprietary drivers, but they've been mostly fixed as of the 570 driver, most of those fixes happened between the 555 and 560 drivers.

#### GNOME
GNOME on Wayland does not support drawing borders, drop shadows, title bars, etc. (or, in short "Decorations"): it expects the window to draw them by itself (client-side decorations). As you may imagine, this "design choice" (read "Obvious bug they won't fix no matter how much people complain at their doorstep") is controversial because it leads to windows that do not support client-side decorations being drawn without any decorations. GNOME is also a desktop that very much lets perfect be the enemy of good (and thus the main responsible for the slowness of Wayland's development).

### I want to switch, what should I keep in mind?

#### Do distros matter? Which one is the best?
See [Choosing my First Distro](choosing_my_first_distro.md)

#### Linux isn't Windows
Said like that it sounds obvious, but it can be much harder for it to sink in that it may seem at first glance: a lifetime of habits, assumptions, and conditioning doesn't go away the moment you switch to another OS. If anything, under the hood, (GNU/)Linux is more similar to Mac: the former is a (much improved, and Free as in "free speech") clone of UNIX, and the latter is a true descendant of AT&T UNIX.

And even if moving from Mac to (GNU/)Linux may have less technical challenges (unless you're doing that on a Mac), the biggest challenges go far beyond simply getting used to a new OS: you'll likely have to use new tools for your professional work, and you'll need to get used to interacting directly with community projects rather than yelling on the internet, praying that some corporate people listen to you.

#### Window Manager... Desktop Environment... Compositor...
The terminology is different whether we're talking about an X11 session or a Wayland one.

On X11, you have a graphical server (X.Org), which is the part that handles the low level things you don't want to think about, a window manager, which simply keeps track of where the windows are and how big they are, and optionally a compositor, which handles graphical effects and animations. On Wayland, the server, the window manager, and the compositor are merged in a single program, simply called Wayland compositor.

A Desktop Environment (DE for short) is simply a bundle of a Wayland compositor/X11 window manager, some sort of system UI a.k.a shell (you know Window's start menu, the taskbar, and the Windows notifications? Basically, that's the shell), and an application suite.
