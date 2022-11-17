# UwUDOS: the worst operating system ever created (or is it?)

## The premise:
- high performance on low-end hardware
- the user has ring 0 permissions by default
- a minimal system, most stuff is optional
- simple, an average person can understand what's going on under the hood.
- is unique, not a UNIX or MS-DOS clone.
- a textual GUI with pixel-perfect graphics support (for idk, viewing images)
- doesn't practice hardware discrimination (made without a specific computer in mind)
- is FUN to use

## the root directory:

- system:
    contains the kernel, the bootloader, basically everything that's needed for the system to work.

    in the system directory will be:
        - boot
        - kernel
        - pagefile
        - drivers
        - devices (contains files for stuff like drives, printers etc.)
        - services
        - binutil (a utility system binary folder, in PATH)
        - bingui (a gui system binary folder, in PATH)
        - init

- home:
    has user data, a combination of linux's /home, /usr and /etc

    every user has a specific folder here, like in linux.
    since a user authentication system is basically optional, it can be enabled via a service (just like permissions)

    in the account folder there will be:
        - .etc (a standard config folder, hidden)
        - nothing else, since the home directory should be clean and simple, without clutter.
          and it would be easier to copy the dotfiles this way

- temp:
    temporary files. directory is wiped on shutdown.
- mount:
    contains every drive, every directory can be a symlink to a mounted drive, symbolized by a letter like in windows.
    unlike windows, the root drive will always be the A: drive.
    UwUDOS will support up to 36 devices, A-Z + 0-9
    the A: drive folder is basically a symlink that takes you back to /

    these folders will be "special", they will have the drive name as their description, that will display in the "lf" command

## the sheww :3 (shell)

- case insensitive
- simple, doesn't have loops and other stuff. if you want to program - there will be a (optional) C compiler to install
- syntax like the POSIX shell, just without most of the features
- the "PS1" variable will be customizable

## the human interface guidelines:

- getting rid of the bars, docks etc.
- fully themeable, user should be able change every color used in the GUI.
- everything is a window, the clock is a window, the system monitor is a window, the task manager is a window
- right click to get a customized menu, like idk, openbox
- options in the window bar, no stupid in-app menu bar bullshit
- window titlebars handle like in BeOS (fullscreen mode is the exception, the titlebars are expanded there)
- tabbing functionality in the titlebars (optional)
- minimized / iconized apps are on the desktop as little icon windows
- to launch programs you use an MS-DOS Executive-like window, looking simpler, but mostly it's the same idea
- no notifications, and other things that could distract you. if you want it on the screen, it's a window.
- you can wind-up windows to the top, it acts as a bar, but it's temporary and made for a specific purpose. useful for, idk. music player controls. (can't move these bars, but you can have them on the bottom if you want. we'll decide later)
- support for multiple workspaces / virtual desktops.

desktop inspirations: TWM, DWM, plan9's rio, DeskMate, the GUI of TempleOS / ZealOS, Pre win-9x windows GUI

let me know if you want some other stuff here

## the commands
here is a list of most commands included in the system. these will be stored in the "binutil" folder. allowing you to update them just by replacing it.

- cd (changes directory)
- lf (list files)
- mk (makes a file / directory)
- rm (removes stuff)
- find (finds stuff)
- cp (copies stuff)
- mv (moves / renames stuff)
- ve (stands for Visual Editor, basically edits text)
- mix (audio mixer)
- rendr (manages the display)
- part (partition editor + a formatting tool)
- dpkg (an offline package manager, name stolen from debian)
- bottom (a system monitor, simillar to top)
- kill (kills a process)
- sv (manages services, mostly used in the *init* script)
- man (manual)
- cat (basically UNIX cat)
- boot (shuts down the system, reboots the system, hibernates etc)
- uwuver (shows the verion of the system)

gui programs (in the bingui folder):

- uwuverx (the gui version of uwuver)
- gclock  (a... clock, like an analog one.)
- taskmgr (a task switcher, with a list of all open applications)
- bckgrnd (a wallpaper tool, cuz why not)
- cowonky (a conky-like program, displays stats and other stuff in a window, basically a widget panel)
- gbottom (a gui process manager, with the ability to kill stuff)
- uwuterm (a terminal with full multimedia support, a "blank" window for everything)
- uwuhelp (a gui frontend to man)
- uwuexec (starts and stops stuff. oh and manages files.)
- adminya (a windows-like control panel, a frontend to various commands. has an API that will allow third-party apps to interface with it)

other commands are either a part of an optional service, or are completely independent
let me know if you want some other stuff here

## file attributes
every file / directory has some attributes assigned to them.

- name
- size
- format
- visibility
- description (can sometimes be changed by the user)
- permissions + owner (used by the "perm" service, is disabled by default)

## services
services are the components of the system.
they are mostly used to enable functionality such as permissions, the user authentication system and so on.

now i can only think of these three services.
- perm (permissions and ownership)
- auth (works with perm, adds stuff like users and groups)
- home (the home screen, enabled by default)
    at launch the user will see a very customizable home screen (either in the gui or in the pure CLI mode)
    it will have shortcuts for their favourite applications, and some other stuff defined by the user, such as mail notifications and a motd.

there will be probably more down the line.

## uwuexec
the most important program in the uwudos gui.
a graphical file manager combined with a (not so) powerful program launcher

first, you need to choose a userland PATH in the preferences menu.
probably it would be a folder made manually in home for applications.

then, all of your executables would basically show up.
obviously, filtering and sorting by category will be supported.

outside of executables, the list will also have folders that you could open, and then navigate peacefully.
connected drives will be showed on top of the list. clicking them will result in navigating to their directories.
to go back to the home screen, press the "home" button in the drive bar
