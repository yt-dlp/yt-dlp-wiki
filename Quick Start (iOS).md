## iOS/iPadOS

On iOS, we recommend installing yt-dlp through a-Shell.

1. Install [a-Shell](https://apps.apple.com/us/app/a-shell/id1473805438).
2. Install yt-dlp.
   1. Execute the following command by copy-pasting it into a-Shell and tap return:
      ```
      pip install --pre -U yt-dlp[default] yt-dlp-apple-webkit-jsi
      ```
      Note: [yt-dlp-apple-webkit-jsi](https://github.com/grqz/yt-dlp-apple-webkit-jsi) is a 3rd-party plugin used to solve YouTube's JavaScript challenges. To learn more, visit the [EJS wiki page](https://github.com/yt-dlp/yt-dlp/wiki/EJS).
3. Download a video.
   1. Execute:
      ```
      yt-dlp "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading.
   2. You can find the downloaded video in the Files app \> On My iPhone/iPad \> a-Shell \> your downloaded video.