# docker-mpd-0.19

This image is based on https://github.com/gutmensch/docker-mpd and https://github.com/Tob1as/docker-mpd

### What is MPD?
Music Player Daemon (MPD) is a free and open music player server. It plays audio files, organizes playlists and maintains a music database. In order to interact with it, a client program is needed. The MPD distribution includes mpc, a simple command line client.
> [wikipedia.org/wiki/Music_Player_Daemon](https://en.wikipedia.org/wiki/Music_Player_Daemon) 

### About these images:
* It uses latest mpd v0.19 - latest version with support `id3v1_encoding` config option.
* Based on official [alpine](https://hub.docker.com/_/alpine) image.

#### Docker-Compose

```yaml
services:
  mpd:
    image: mpd-0.19
    container_name: mpd
    restart: unless-stopped
    ports:
      - 6600:6600  # MPD Client
      - 8000:8000  # HTTP Stream
    volumes:
      - mpd.conf:/etc/mpd.conf:ro
      - /Music:/var/lib/mpd/music:ro
      - playlists:/var/lib/mpd/playlists
```
