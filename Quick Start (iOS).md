# iOS/iPadOS

On iOS/iPadOS, we recommend installing yt-dlp through a-Shell.

1. Install [a-Shell](https://apps.apple.com/us/app/a-shell/id1473805438).
1. Install yt-dlp.
   1. Execute the following command by copy-pasting it into a-Shell and tap return:
      ```shell
      pip install --pre -U yt-dlp[default] yt-dlp-apple-webkit-jsi
      ```
      Note: [yt-dlp-apple-webkit-jsi](https://github.com/grqz/yt-dlp-apple-webkit-jsi) is a 3rd-party plugin used to solve [YouTube's JavaScript challenges](https://github.com/yt-dlp/yt-dlp/wiki/EJS).
1. Download a video.
   1. Execute:
      ```shell
      yt-dlp "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading.
   1. You can find the downloaded video in the Files app \> On My iPhone/iPad \> a-Shell \> your downloaded video.

For common usage commands, move on to [Basic Usage](Basic&#x20;Usage.md).