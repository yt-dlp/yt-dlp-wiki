## Android {#android}

On Android, we recommend installing yt-dlp through Termux.

1. Install [Termux](https://github.com/termux/termux-app/releases)  
2. Ensure Termux can download files into your phone by executing `termux-setup-storage`   
3. Update the list of packages by executing `pkg update && pkg upgrade`  
4. Install python, pip, and FFmpeg by executing  `pkg install python python-pip ffmpeg`  
5. Install yt-dlp by executing `pip install --pre -U "yt-dlp[default]"`  
6. (Required for YouTube downloads) Install Deno by executing `pkg install deno`
7. Download a video by executing `yt-dlp "URL"`. Replace `URL` with the actual video URL you want to download. Your video will start downloading.