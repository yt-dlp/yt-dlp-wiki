# macOS

On macOS, we recommend installing yt-dlp through the Homebrew package manager.

1. Install Homebrew (if you don't already have it).
   1. Visit [https://brew.sh/](https://brew.sh/) in your browser.
   1. Execute the command under "Install Homebrew" by copy-pasting it into your Terminal and hitting Enter.
      1. To open the Terminal, do `Command + Space` \> type "Terminal" \> click the top result.
   1. Follow the installation prompts.
   1. After installing Homebrew, reopen Terminal.
1. Install yt-dlp, FFmpeg, and Deno (required for YouTube downloads).
   1. Execute:
      ```shell
      brew install --HEAD yt-dlp ffmpeg deno
      ```
1. Download a video.
   1. In a Terminal window, execute:
      ```shell
      yt-dlp -P PATH "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](Basic&#x20;Usage.md#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.

## For common usage commands, move on to [Basic Usage](Basic&#x20;Usage.md).