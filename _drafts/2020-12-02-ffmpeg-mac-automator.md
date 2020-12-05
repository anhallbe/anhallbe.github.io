---
layout: post
title:  Playing around with FFmpeg & Automator
date:   2020-12-02 20:00:00 +0100
tags:   personal technology
---
I recently got to play around with [FFmpeg](https://ffmpeg.org) and the Mac [Automator](https://support.apple.com/guide/automator/welcome/mac). It was a fun little project to work on, and I learned some things that I thought I'd share. It was also one of those times where I got to apply my knowledge and Google-foo to a real-world problem, and make life just a little bit easier for myself and those around me, which was very rewarding.

## Background
My SO likes to record her remote university lectures. The university does not provide these recordings for some reason, my guess is that it would involve an extra step for the teaching staff which would ultimately only lead to reduced attendance. Or there's another completely valid reason, I'm not sure. In any case, if the students want recordings, they'll have to set it up themselves.

The lectures are done over a video conferencing tool that doesn't provide an easy way to record the stream directly, so the natural quick solution was to just record the entire screen using **THE MAC SCREENSHOT PROGRAM**. This worked out just fine for a couple of lectures, but...

## The Problem
The screen recordings from **THE MAC SCREENSHOT PROGRAM** are *HUGE*. These high-resolution, high-framerate screen recordings look beautiful, and they have many use-cases. But showing 4 hours of mostly static PowerPoint slides with a tiny low-res image of a talking head in the corner isn't one of them.

Needless to say, at 8GB per recorded lecture it didn't take long until the Macbook Pro ran out of disk space.

## FFmpeg to the rescue
```bash
ffmpeg -i Screen\ Recording\ 2020-12-02\ at\ 10.00.00.mov -r 10 -s 1280x720 Screen\ Recording\ 2020-12-02\ at\ 10.00.00.mp4
```

```bash
for f in "$@" do
    /usr/local/bin/ffmpeg -i "$f" -r 10 -s 1280x720 "${f%.*}.mp4"
done
```
## That UX, though...