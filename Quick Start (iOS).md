# iOS/iPadOS

On iOS/iPadOS, we recommend installing yt-dlp through a-Shell.

1. Install [a-Shell](https://apps.apple.com/us/app/a-shell/id1473805438) or [a-Shell mini](https://apps.apple.com/us/app/a-shell-mini/id1543537943) (for a smaller storage footprint).
1. Install yt-dlp.
   1. Execute the following command by copy-pasting it into a-Shell and tap return:
      ```shell
      pip install --pre -U yt-dlp[default] yt-dlp-apple-webkit-jsi
      ```
      Tip: To easily paste something into a-Shell, press the clipboard icon above the keyboard. Note: [yt-dlp-apple-webkit-jsi](https://github.com/grqz/yt-dlp-apple-webkit-jsi) is a 3rd-party plugin used to solve [YouTube's JavaScript challenges](https://github.com/yt-dlp/yt-dlp/wiki/EJS).
1. Download a video.
   1. Execute:
      ```shell
      yt-dlp "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading.
   1. You can find the downloaded video in the Files app \> On My iPhone/iPad \> a-Shell \> your downloaded video.
   1. If you want to automatically open the "share sheet" after downloading each video, add `--exec open` to the end of your command (or run `echo --exec open >> yt-dlp.conf` to create a [config file](Common&#x20;Usage.md#how-to-create-a-config) and enable it permanently).
   1. iOS' default video player has very limited video support. We recommend playing downloaded media using [VLC](https://apps.apple.com/us/app/vlc-media-player/id650377962).

For common usage commands, move on to [Common Usage](Common&#x20;Usage.md).