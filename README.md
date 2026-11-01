# tunes

Music from YouTube Music into mpd's library, tagged from YouTube Music:
the music side of what [reel](../reel) is for video.

- `tunes search` finds albums and songs; quickbar's media search
  (Entertainment → Music) shows them.
- `tunes get` downloads an album, some of its tracks, or one song, in the
  background. With a download runner on PATH (`$TUNES_RUNNER`, else
  quickbar's `quickbar-download`) the runner runs it, so its downloads list
  can pause and cancel it; without one, progress is a notification.
  `tunes fetch` runs yt-dlp into a staging folder in `~/.cache/tunes/`,
  keeping YouTube's audio as it is (opus or m4a), then `tunes file` tags it
  and moves it into mpd's `music_directory`, updates mpd, and notifies with
  Play and Open folder.
- `tunes import` tags loose files from YouTube Music and files them the
  same way (a dry run without `--apply`).

It's a `uv run --script` script; ytmusicapi and mutagen are its
dependencies, yt-dlp, curl, mpc and notify-send its tools. `makepkg -si`
with the PKGBUILD installs it as `tunes`.

## Layout

```
<music>/<Album artist>/<Album> (<Year>)/NN Title.ext   with cover.jpg
<music>/<Artist>/Singles/Title.ext                      a song with no album
```

Tags: title, artist, album, album artist, date, track number and total,
the cover, and `YTMUSIC_VIDEO_ID`.

## Use

```sh
tunes search --json QUERY
tunes tracks --json ALBUM_ID
tunes get ALBUM_ID [--tracks 1,3]
tunes get --song VIDEO_ID [--album ALBUM_ID]
tunes import [--apply] [FILE...]
```
