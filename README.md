# remi

`remi` is a small Bash + `fzf` front end for Remmina. It discovers your saved
profiles, lets you connect without opening Remmina's profile browser, and can
add, edit, or remove profiles from the terminal.

## Requirements

- Bash 4 or newer
- [`fzf`](https://github.com/junegunn/fzf)
- [Remmina](https://remmina.org/)

## Install

Put the executable somewhere on your `PATH`, for example:

```sh
install -Dm755 remi ~/.local/bin/remi
```

Then run:

```sh
remi
```

Inside the picker, press Enter to connect, Ctrl-A to add, Ctrl-E to edit, and
Ctrl-D to remove a profile. Escape closes the picker.

The same actions are available as commands:

```sh
remi list
remi connect                 # select with fzf
remi connect "Work desktop"  # use an exact profile name
remi add
remi edit
remi remove
```

`add` creates a minimal Remmina profile and asks for its group. The profile name
is shown as its label in listings. Remmina asks for the password when you
connect, so the script never reads or stores passwords. `edit` opens a temporary
copy in `$VISUAL`, `$EDITOR`, or `vi` and only replaces the profile after basic
validation. `remove` uses the desktop trash through `gio` when available.

Profiles are discovered in the common XDG, legacy, Flatpak, and Snap locations.
Set `REMMINA_PROFILE_DIR` to use another directory; new profiles are written
there as mode `0600` files.
