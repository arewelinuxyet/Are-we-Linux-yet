# Choosing my First Distro

## What's with all this nerd talk!? Just give me a distro!
Doing something because some dude on the internet told you, without understanding why isn't a great idea, but I digress.

### I have old hardware
**Linux Mint Cinnamon Edition**: it's beginner-friendly enough, especially for people coming Windows. May not support the newest hardware.

### I have the latest hardware
**EndeavourOS**: Less beginner-friendly, but it has higher chances of supporting the newest hardware.

### I'm using Apple Silicon
**Asahi**: Only for Apple Silicon users, and the only real choice for Apple Silicon. It's highly experimental.

## What's a distro, actually?

Might sound obvious: whoever has made into this page probably already knows that a distro is a "version" of "Linux", right? But this is actually one of the most underasked questions out there.

Linux itself is a well defined software, a kernel to be exact, with its own well defined version numbers, so, what's the point of a distro?

Well, for starters, Linux is not a complete operating system: it's a kernel, the part of the OS that manages the system's resources and talks with the hardware, a part of the OS that the user should never think about, aside of some edge cases. For how much Linus might insist that the kernel is the OS, he's just plain wrong there. But still, a distro needs to ship a complete operating system.

Historically, the GNU Project (short for "GNU is Not Unix") was the rest of the OS, and the GNU Project actually predates Linux, it's the responsible of the birth of the Free Software Movement, and indirectly of the Open Source Initiative, which is why several people insist that the OS shouldn't be called "Linux", but rather "GNU/Linux", there's even a reactionary group that calls the whole just "GNU" because, if Open Source people neglect to mention GNU, then it's fair game if Free Software people neglect to mention Linux. In actuality thanks to the success of bot the Open Source movement and Open Source, together with IBM software, via its subsidiary Red Hat, taking several important tasks in the OS, together with the GNU Project lacking manpower, the percentage of both GNU and Linux in the average distro is dwindling.

In other words, Linux is just one of the many disjointed and independently developed programs that together make a complete OS that people can't even agree on how it should be called. The job of a distro is take all those independent projects and package them in a way that's consistent, and thus, actually works. The distro also maintains its own builds of popular programs, to guarantee that those builds actually do work with the underlying system.

## What makes distros unique?

### Update Cycle
For the longest time, the biggest difference between the distros is, by far, the update cycle: some, like Debian, are glacial, and when they do update, said updates are still decently aged battle-tasted software, others, like Arch, drop updates as soon as there's something that can be updated at all without much of a ceremony and just the bare minimum amount of testing, so much they don't even bother with version numbers (we call them "rolling release").

### Traditional, Reproducible, Atomic
A traditional distro is exactly how a normal OS would work: you can change anything (as long as you have the file permissions) and once you make a change there's no trivial way to rollback, aside of having a backup. If other words, it's great for tinkering, but also full of footguns.

Examples of traditional distros:
- Debian
- Arch
- Mint

Atomic (a.k.a "Immutable" or "Image-based") try to minimize the access to footguns by making modifying system files accidentally nearly impossible, at the cost of also making it very hard to do so intentionally. Atomic distros are generally not the power user's first pick, but they can provide painless experiences in the right circumstances, as well as the ability to easily deploy the same environment to countless computers.

Examples of atomic distros:
- Vanilla OS
- Fedora Atomic Workstation series
- SteamOS

Reproducible distros allow the user to easily change system files, but also to easily rollback any changes. The catch is it's done by having to maintain a configuration file for the entire system, which always results in the same exact environment. Maintaining said configuration file can be a challenge and many users consider it to not be worth it, but the people who like reproducible distros really like reproducible distros.

Examples of reproducible distros:
- NyxOS
- GNU Guix

### Specificity
Some distros, like Kali, ChimeraOS, SteamOS, or Tails, are built specifically for a single use case, at the detriment of pretty general usage. While they are generally good at their one goal, they're generally **not a good fit** as the main boot of a primary workstation.

### Defaults
Of course, every distro is going to ship some defaults to make a decent out of the box experience, except some distros, like Arch, Void, and Gentoo, that have as shipping as little default as possible as their entire point.

### Some technical stuff

- **Free Software commitment**: Some distro commit to the Free Software mission more than other
- **Exact versions of software**: even if two distros have the same update cycle, they might still opt to ship different versions of the same software
- **Custom patches**: most distros do not commit to shipping the software they package as vanilla as possible, and several things will have custom patches
- **Package manager**: the programs you install are packaged in, well, packages, and the package manager manages which packages are installed, each base distro has its own, but derivatives usually just ship what their parent distro does
- **systemd**: The vast majority of distros ships systemd as a core system component, but the people who dislike systemd really hate it, to the point that there are plenty of distros that are just "X distro, but without systemd"
