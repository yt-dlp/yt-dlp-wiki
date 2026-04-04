# Android

On Android, we recommend installing yt-dlp through Termux.

1. Install and setup [Termux](https://github.com/termux/termux-app/releases).
   1. Ensure Termux can download files into your phone by executing:
      ```shell
      termux-setup-storage
      ```
   1. Update the list of packages by executing:
      ```shell
      pkg update && pkg upgrade
      ```
1. Install python, pip, FFmpeg, and Deno (required for YouTube downloads) by executing:
   ```shell
   pkg install python python-pip ffmpeg deno
   ```
1. Install yt-dlp by executing:
   ```shell
   pip install --pre -U "yt-dlp[default,curl-cffi]"
   ```
   - If you encounter errors with the installation command above, try installing yt-dlp without [curl-cffi](https://github.com/yt-dlp/yt-dlp#impersonation):
     ```shell
      pip install --pre -U "yt-dlp[default]"
     ```
1. Create a config file and instruct yt-dlp to use your downloads folder by executing:
   ```shell
   echo '-P "~/storage/downloads"' > ~/yt-dlp.conf
   ```
1. Download a video by executing:
   ```shell
   yt-dlp "URL"
   ```
   Replace `URL` with the actual video URL you want to download. Your video will start downloading.

For common usage commands, move on to [Common Usage](Common&#x20;Usage.md).
