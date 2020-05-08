# FFMPEG

## Install

`brew remove ffmpeg`

`brew reinstall ffmpeg --with-faac --with-fdk-aac --with-ffplay --with-freetype --with-frei0r --with-libass --with-libvo-aacenc --with-libvorbis --with-libvpx --with-opencore-amr --with-openjpeg --with-opus --with-rtmpdump --with-schroedinger --with-speex --with-theora --with-tools`

## Basic Usage

`ffmpeg -i movie.mp4 song.mp3`

## Trim Video

`ffmpeg -i movie.mp4 -ss 00:00:03 -t 00:00:08 -async 1 cut.mp4`

## Check version

`ffmpeg -version`

## Reference

* [https://www.ffmpeg.org/](https://www.ffmpeg.org/)