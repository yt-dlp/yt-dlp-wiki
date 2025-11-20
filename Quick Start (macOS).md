## macOS

On macOS, we recommend installing yt-dlp through the Homebrew package manager.

1. Install Homebrew (if you don't already have it)  
   1. Visit [https://brew.sh/](https://brew.sh/) in your browser  
   2. Copy the command under "Install Homebrew” and paste it into your Terminal  
      1. To open the Terminal, do `Command + Space` \> type "Terminal”  
   3. Follow the installation prompts  
   4. After installing brew, reopen Terminal  
2. Install yt-dlp, ffmpeg, and deno (the latter is used only for Youtube)  
   1. Execute `brew install --HEAD yt-dlp ffmpeg deno` in the Terminal window  
3. Download a video  
   1. In a Terminal window, execute `yt-dlp -P PATH "URL"`. Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.