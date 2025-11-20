## Android

On Android, we recommend installing yt-dlp through Termux.

1. Install and setup [Termux](https://github.com/termux/termux-app/releases)
   1. Ensure Termux can download files into your phone by executing
      ```
      termux-setup-storage
      ```
   2. Update the list of packages by executing
      ```
      pkg update && pkg upgrade
      ```
2. Install python, pip, FFmpeg, and Deno (required for YouTube downloads) by executing
   ```
   pkg install python python-pip ffmpeg deno
   ```
3. Install yt-dlp by executing
   ```
   pip install --pre -U "yt-dlp[default]"
   ```
4. Download a video by executing
   ```
   yt-dlp "URL"
   ```
   Replace `URL` with the actual video URL you want to download. Your video will start downloading.