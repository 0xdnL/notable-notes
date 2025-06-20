---
tags: [python]
title: youtube-dl
created: '2019-07-30T06:19:49.267Z'
modified: '2025-06-07T08:51:45.391Z'
---

# youtube-dl

> download videos from youtube.com or other video platforms

[[yt-dlp]]

## install

```sh
brew install youtube-dl

pip install --upgrade youtube-dl

curl -LO https://yt-dl.org/downloads/latest/youtube-dl # move to path and chmod a+rx FILE
```

## option

```sh
# General Options
-h, --help                              # Print this help text and exit
    --version                           # Print program version and exit
-U, --update                            # Update this program to latest version. Make sure that you have sufficient permissions (run with sudo if needed)
-i, --ignore-errors                     # Continue on download errors, for example to skip unavailable videos in a playlist
    --abort-on-error                    # Abort downloading of further videos (in the playlist or the command line) if an error occurs
    --dump-user-agent                   # Display the current browser identification
    --list-extractors                   # List all supported extractors
    --extractor-descriptions            # Output descriptions of all supported extractors
    --force-generic-extractor           # Force extraction to use the generic extractor
    --default-search PREFIX             # prefix for unqualified URLs. For example "gvsearch2:" downloads two videos from google videos for youtube-dl "large apple"
    --ignore-config                     # Do not read configuration files
    --config-location PATH              # Location of the configuration file; either the path to the config or its containing directory.
    --flat-playlist                     # Do not extract the videos of a playlist, only list them.
    --mark-watched                      # Mark videos watched (YouTube only)
    --no-mark-watched                   # Do not mark videos watched (YouTube only)
    --no-color                          # Do not emit color codes in output

# Video Selection
    --playlist-start NUMBER             # Playlist video to start at (default is 1)
    --playlist-end NUMBER               # Playlist video to end at (default is last)
    --playlist-items ITEM_SPEC          # Playlist video items to download. Specify indices in playlist separated by commas: "--playlist-items 1,2,5,8", specify range: "--playlist-items 1-3,7,10-13"
    --match-title REGEX                 # Download only matching titles (regex or caseless sub-string)
    --reject-title REGEX                # Skip download for matching titles (regex or caseless sub-string)
    --max-downloads NUMBER              # Abort after downloading NUMBER files
    --min-filesize SIZE                 # Do not download any videos smaller than SIZE (e.g. 50k or 44.6m)
    --max-filesize SIZE                 # Do not download any videos larger than SIZE (e.g. 50k or 44.6m)
    --date DATE                         # Download only videos uploaded in this date
    --datebefore DATE                   # Download only videos uploaded on or before this date (i.e. inclusive)
    --dateafter DATE                    # Download only videos uploaded on or after this date (i.e. inclusive)
    --min-views COUNT                   # Do not download any videos with less than COUNT views
    --max-views COUNT                   # Do not download any videos with more than COUNT views
    --match-filter FILTER               # Generic video filter. Specify any key (see the "OUTPUT TEMPLATE" for a list of available keys)
    --no-playlist                       # Download only the video, if the URL refers to a video and a playlist.
    --yes-playlist                      # Download the playlist, if the URL refers to a video and a playlist.
    --age-limit YEARS                   # Download only videos suitable for the given age
    --download-archive FILE             # Download only videos not listed in the archive file. Record the IDs of all downloaded videos in it.
    --include-ads                       # Download advertisements as well (experimental)

# Download Options
    -r, --limit-rate RATE               # Maximum download rate in bytes per second (e.g. 50K or 4.2M)
    -R, --retries RETRIES               # Number of retries (default is 10), or "infinite".
    --fragment-retries RETRIES          # Number of retries for a fragment (default is 10), or "infinite" (DASH, hlsnative and ISM)
    --skip-unavailable-fragments        # Skip unavailable fragments (DASH, hlsnative and ISM)
    --abort-on-unavailable-fragment     # Abort downloading when some fragment is not available
    --keep-fragments                    # Keep downloaded fragments on disk after downloading is finished; fragments are erased by default
    --buffer-size SIZE                  # Size of download buffer (e.g. 1024 or 16K) (default is 1024)
    --no-resize-buffer                  # Do not automatically adjust the buffer size. By default, the buffer size is automatically resized from an initial value of SIZE.
    --http-chunk-size SIZE              # Size of a chunk for chunk-based HTTP downloading (e.g. 10485760 or 10M) (default is disabled). May be useful for bypassing bandwidth throttling imposed by a webserver (experimental)
    --playlist-reverse                  # Download playlist videos in reverse order
    --playlist-random                   # Download playlist videos in random order
    --xattr-set-filesize                # Set file xattribute ytdl.filesize with expected file size
    --hls-prefer-native                 # Use the native HLS downloader instead of ffmpeg
    --hls-prefer-ffmpeg                 # Use ffmpeg instead of the native HLS downloader
    --hls-use-mpegts                    # Use the mpegts container for HLS videos, allowing to play the video while downloading (some players may not be able to play it)
    --external-downloader COMMAND       # Use the specified external downloader. Currently supports aria2c,avconv,axel,curl,ffmpeg,httpie,wget
    --external-downloader-args ARGS     # Give these arguments to the external downloader

# Filesystem Options
-a, --batch-file FILE                   # File containing URLs to download ('-' for stdin), one URL per line. Lines starting with '#', ';' or ']' are considered as comments and ignored.
    --id                                # Use only video ID in file name
-o, --output TEMPLATE                   # Output filename template, see the "OUTPUT TEMPLATE" for all the info
    --output-na-placeholder PLACEHOLDER # Placeholder value for unavailable meta fields in output filename template (default is "NA")
    --autonumber-start NUMBER           # Specify the start value for %(autonumber)s (default is 1)
    --restrict-filenames                # Restrict filenames to only ASCII characters, and avoid "&" and spaces in filenames
-w, --no-overwrites                     # Do not overwrite files
-c, --continue                          # Force resume of partially downloaded files. By default, youtube-dl will resume downloads if possible.
    --no-continue                       # Do not resume partially downloaded files (restart from beginning)
    --no-part                           # Do not use .part files - write directly into output file
    --no-mtime                          # Do not use the Last-modified header to set the file modification time
    --write-description                 # Write video description to a .description file
    --write-info-json                   # Write video metadata to a .info.json file
    --write-annotations                 # Write video annotations to a .annotations.xml file
    --load-info-json FILE               # JSON file containing the video information (created with the "   --write-info-json" option)
    --cookies FILE                      # File to read cookies from and dump cookie jar in
    --cache-dir DIR                     # Location in the filesystem where youtube-dl can store some downloaded information permanently
    --no-cache-dir                      # Disable filesystem caching
    --rm-cache-dir                      # Delete all filesystem cache files

# Thumbnail Options
    --write-thumbnail                    Write thumbnail image to disk
    --write-all-thumbnails               Write all thumbnail image formats to disk
    --list-thumbnails                    Simulate and list all available thumbnail formats

# Verbosity / Simulation Options
-q, --quiet                          Activate quiet mode
    --no-warnings                    Ignore warnings
-s, --simulate                       Do not download the video and do not write anything to disk
    --skip-download                  Do not download the video
-g, --get-url                        Simulate, quiet but print URL
-e, --get-title                      Simulate, quiet but print title
    --get-id                         Simulate, quiet but print id
    --get-thumbnail                  Simulate, quiet but print thumbnail URL
    --get-description                Simulate, quiet but print video description
    --get-duration                   Simulate, quiet but print video length
    --get-filename                   Simulate, quiet but print output filename
    --get-format                     Simulate, quiet but print output format
-j, --dump-json                      Simulate, quiet but print JSON information. See the "OUTPUT TEMPLATE" for a description of available keys.
-J, --dump-single-json               Simulate, quiet but print JSON information for each command-line argument. If the URL refers to a playlist, dump the whole playlist information in a single line.
    --print-json                     Be quiet and print the video information as JSON (video is still being downloaded).
    --newline                        Output progress bar as new lines
    --no-progress                    Do not print progress bar
    --console-title                  Display progress in console titlebar
-v, --verbose                        Print various debugging information
    --dump-pages                     Print downloaded pages encoded using base64 to debug problems (very verbose)
    --write-pages                    Write downloaded intermediary pages to files in the current directory to debug problems
    --print-traffic                  Display sent and read HTTP traffic
-C, --call-home                      Contact the youtube-dl server for debugging
    --no-call-home                   Do NOT contact the youtube-dl server for debugging

# Video Format Options
-f, --format FORMAT                  Video format code, see the "FORMAT SELECTION" for all the info
    --all-formats                    Download all available video formats
    --prefer-free-formats            Prefer free video formats unless a specific one is requested
-F, --list-formats                   List all available formats of requested videos
    --youtube-skip-dash-manifest     Do not download the DASH manifests and related data on YouTube videos
    --merge-output-format FORMAT     If a merge is required (e.g. bestvideo+bestaudio), output to given container format. One of mkv, mp4, ogg, webm, flv. Ignored if no merge is required

# Subtitle Options
    --write-sub                          Write subtitle file
    --write-auto-sub                     Write automatically generated subtitle file (YouTube only)
    --all-subs                           Download all the available subtitles of the video
    --list-subs                          List all available subtitles for the video
    --sub-format FORMAT                  Subtitle format, accepts formats preference, for example: "srt" or "ass/srt/best"
    --sub-lang LANGS                     Languages of the subtitles to download (optional) separated by commas, use --list-subs for available language tags

# Authentication Options
-u, --username USERNAME              Login with this account ID
-p, --password PASSWORD              Account password. If this option is left out, youtube-dl will ask interactively.
-2, --twofactor TWOFACTOR            Two-factor authentication code
-n, --netrc                          Use .netrc authentication data
    --video-password PASSWORD        Video password (vimeo, youku)

# Adobe Pass Options
    --ap-mso MSO                         Adobe Pass multiple-system operator (TV provider) identifier, use --ap-list-mso for a list of available MSOs
    --ap-username USERNAME               Multiple-system operator account login
    --ap-password PASSWORD               Multiple-system operator account password. If this option is left out, youtube-dl will ask interactively.
    --ap-list-mso                        List all supported multiple-system operators

# Post-processing Options
-x, --extract-audio                      Convert video files to audio-only files (requires ffmpeg/avconv and ffprobe/avprobe)
    --audio-format FORMAT                Specify audio format: "best", "aac", "flac", "mp3", "m4a", "opus", "vorbis", or "wav"; "best" by default; No effect without -x
    --audio-quality QUALITY              Specify ffmpeg/avconv audio quality, insert a value between 0 (better) and 9 (worse) for VBR or a specific bitrate like 128K (default 5)
    --recode-video FORMAT                Encode the video to another format if necessary (currently supported: mp4|flv|ogg|webm|mkv|avi)
    --postprocessor-args ARGS            Give these arguments to the postprocessor
-k, --keep-video                         Keep the video file on disk after the post-processing; the video is erased by default
    --no-post-overwrites                 Do not overwrite post-processed files; the post-processed files are overwritten by default
    --embed-subs                         Embed subtitles in the video (only for mp4, webm and mkv videos)
    --embed-thumbnail                    Embed thumbnail in the audio as cover art
    --add-metadata                       Write metadata to the video file
    --metadata-from-title FORMAT         parse additional metadata like song title / artist from the video title. The format syntax is the same as --output. Regular expression with named capture groups may also be used. The parsed parameters replace existing values. Example: --metadata-from-title
                                         "%(artist)s - %(title)s" matches a title like "Coldplay - Paradise". Example (regex): --metadata-from-title "(?P<artist>.+?) - (?P<title>.+)"
    --xattrs                             Write metadata to the video file's xattrs (using dublin core and xdg standards)
    --fixup POLICY                       Automatically correct known faults of the file. One of never (do nothing), warn (only emit a warning), detect_or_warn (the default; fix file if we can, warn otherwise)
    --prefer-avconv                      Prefer avconv over ffmpeg for running the postprocessors
    --prefer-ffmpeg                      Prefer ffmpeg over avconv for running the postprocessors (default)
    --ffmpeg-location PATH               Location of the ffmpeg/avconv binary; either the path to the binary or its containing directory.
    --exec CMD                           Execute a command on the file after downloading and post-processing, similar to find's -exec syntax. Example: --exec 'adb push {} /sdcard/Music/ && rm {}'
    --convert-subs FORMAT                Convert the subtitles to other format (currently supported: srt|ass|vtt|lrc)
```

## usage

```sh
youtube-dl --continue --extract-audio --audio-format mp3 --embed-thumbnail h3Q12OkBTHk

youtube-dl --continue --extract-audio --audio-format mp3 --embed-thumbnail --batch-file FILE

youtube-dl --skip-download --write-thumbnail VIDEO_ID    # download just the thumbnail from a youtube video

youtube-dl \
  --extract-audio \
  -f bestaudio \
  -o '/PATH/FILE.mp3' \
  --metadata-from-title "%(artist)s - %(title)s" \
  YOUTUBE_ID 2>&1

youtube-dl `# extract audio from playlist starting at playlist-index: 17` \
  --no-overwrites \
  --continue \
  --extract-audio \
  --audio-format mp3 \
  --playlist-start 17 \
  LIST_ID

youtube-dl -j --flat-playlist LIST_ID | jq  -r --arg START 00 '($START | tonumber) as $s | "\($s) - \(.title)-\(.id)"'
```

## output template

```sh

youtube-dl -o "%(playlist_index)02d - %(title)s.%(ext)s"            LIST_ID
youtube-dl -o "%(playlist)s\%(playlist_index)s - %(title)s.%(ext)s" LIST_ID
youtube-dl -o "%(playlist_index)s-%(title)s.%(ext)s"                LIST_ID
youtube-dl -o "%(autonumber)s-%(title)s.%(ext)s"                    LIST_ID

# checkout: -j, --dump-json 
```

[github.com/ytdl-org/youtube-dl/README.md#output-template](https://github.com/ytdl-org/youtube-dl/blob/master/README.md#output-template)

## see also

- [[jq]]
- [[imagemagick]]
- [[ffmpeg]]
- [[eyed3]]
- [[pip]]
- [[curl]]
- [[chmod]]
