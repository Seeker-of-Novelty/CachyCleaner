# CachyCleaner for Fish Shell, the default for CachyOS
Version: 4.0

A safe, thorough system cleaner for CachyOS / Arch Linux.
Designed to run interactively in Konsole (or any terminal).

Inspired by maclean (cscs).
Rewritten from scratch for the Fish shell.

# Safety rules:
  - Never touches Downloads, Documents, Desktop, Pictures, Music, Videos, etc.
  - Dry-run mode simulates everything without deleting a single file.
  - Age-based cleanup defaults to files older than 3 days.
  - Broken symlinks are detected and offered for removal.
  - Every action is explained and requires confirmation (unless --auto).

# Usage:
  cachycleaner.fish [options]

##   Options:
    -h / --help          Show this help
    -n / --dry-run       Simulate only — nothing is deleted
    -b / --basic         Run basic cleanup (cache, trash, logs, crash dumps)
    -p / --packages      Run package management cleanup
    -c / --containers    Run container cleanup (Flatpak, Snap)
    -j / --junk          Run custom junk directory cleanup
    -d / --developers    Run developer cache cleanup
    -k / --broken        Find and remove broken symlinks in $HOME
    -l / --list          List matched files before each prompt
    -a / --auto          Auto-confirm all prompts (cannot combine with --dry-run)
    -g / --aggressive    Aggressive mode (GPU caches, Steam shaders, etc.)
    -r / --report        Report-only mode (scan and show sizes, no prompts)
    --no-age / --nuke    Remove the age filter — clean ALL eligible files
    --paste              Upload output to paste.cachyos.org and print link
    --all                Run every section (basic + packages + containers + junk + dev + broken)

##   Defaults:
    No options     => runs --basic --packages --containers
    Only --dry-run => runs dry-run of --basic --packages --containers

#   Config file:
    ~/.config/cachycleaner/cachycleaner.conf

###   Examples:
>    cachycleaner.fish --dry-run --list     # preview with file listing
>    cachycleaner.fish -d -n                # preview developer cache cleanup
>    cachycleaner.fish --all --dry-run      # preview everything
>    cachycleaner.fish -r --paste           # report and share via paste.cachyos.org
