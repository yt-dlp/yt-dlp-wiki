# Linux

1. Download FFmpeg.  
   - FFmpeg can be installed from your distribution's package manager. Outdated versions served by package managers are generally okay to use.  
     - Debian-based (e.g. Debian, Ubuntu, or Mint):
       ```shell
       sudo apt update && sudo apt install ffmpeg
       ```
     - Arch-based (e.g. Arch or Manjaro):
       ```shell
       sudo pacman -Syu ffmpeg
       ```
1. Download yt-dlp and deno.
   - If you are using an Arch-based distribution, you can install yt-dlp-git from the AUR: [https://aur.archlinux.org/packages/yt-dlp-git](https://aur.archlinux.org/packages/yt-dlp-git)
   - For all other users (e.g. Ubuntu and Debian), we recommend installing yt-dlp via `uv`:
     1. Download `uv` from [https://github.com/astral-sh/uv/releases](https://github.com/astral-sh/uv/releases)
     1. Extract `uv` and `uvx` from the tarball.
     1. Execute:
        ```shell
        uv tool install uv
        ```
     1. Execute:
        ```shell
        uv tool install --pre "yt-dlp[default,deno]"
        ```
1. Download a video.
   1. Execute:
      ```shell
      yt-dlp -P PATH "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](Common&#x20;Usage.md#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.

For common usage commands, move on to [Common Usage](Common&#x20;Usage.md).
