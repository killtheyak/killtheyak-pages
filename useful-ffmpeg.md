title: use ffmpeg
updated: 2015-10-10 11:12:14
description: Useful ffmpeg commands like speeding up video or boosting audio.
os: [macosx, linux]
tags: [ffmpeg]
deps: []
contributors: ["http://www.github.com/anschwa"] 

Helpful [ffmpeg](https://www.ffmpeg.org/) commands.

# Speeding Up
Speed video up 2x.
```
ffmpeg -i input.mkv -filter:v "setpts=0.5*PTS" output.mkv
```

# Slowing Down
Slow video down 2x
```
ffmpeg -i input.mkv -filter:v "setpts=2.0*PTS" output.mkv
```

# Add Audio track to Video
```
ffmpeg -i input.mkv -i input.mp3 -c copy -shortest -map 0:0 -map 1:0 output.mkv
```

# Boost Audio
Boost audio by 150%
```
ffmpeg -g input.mp4 -af "volume=1.5" output.mp4
```
