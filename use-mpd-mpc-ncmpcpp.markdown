title: use ncmpcpp
updated: 2015-10-10 11:11:48
description: Installing and basic configuration of mpd and ncmpcpp.
os: [macosx, linux]
tags: [mpd, mpc, ncmpcpp]
deps: [install-mpd-mpc-ncmpcpp]
contributors: ["http://www.github.com/daschwa"] 

# Music Player Daemon (mpd)

## Setup

Create a file called `~/.mpdconf` with the following:
```
music_directory         "~/Music"
playlist_directory              "~/.mpd/playlists"
db_file                 "~/.mpd/database"
pid_file                        "~/.mpd/pid"
state_file              "~/.mpd/state"
sticker_file                    "~/.mpd/sticker.sql"
port                            "6600"
auto_update     "yes"
audio_output {
        type            "osx"
        name            "My Mac Device"
        mixer_type      "software"
}
```

And these:
```
mkdir ~/.mpd
mkdir ~/.mpd/playlists
touch ~/.mpd/database
```

# mpc
Command line Music Player Client.

## Usefull Commands
Add matching search results to the current playlist.
```
mpc clear; mpc search <query> | mpc add; mpc play
```

# `mpc.el`
Emacs front end to `mpd`.

# ncmpcpp
Powerful yet lightweight `mpd` client.

## Basic Usage

- `1` View Playlist
- `4` View Library
- `p` Play / Pause
- `a` Add to Playlist
- `c` Clear Playlist
- `q` Quit
- `l` Fetch Lyrics

## Playback Modes

- `r` repeat mode `[r-----]`
- `z` random mode `[-z----]`
- `y` single mode `[--s---]`
- `R` consume mode `[---c--]`
- `x` crossfade mode `[----x-]`
