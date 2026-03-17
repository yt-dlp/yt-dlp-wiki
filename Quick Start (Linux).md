# Linux

1. Download FFmpeg and Deno.  
   - FFmpeg and Deno can be installed from your distribution's package manager. Outdated versions served by package managers are generally okay to use.  
     - Debian-based (e.g. Debian, Ubuntu, or Mint):
       ```shell
       sudo apt update && sudo apt install ffmpeg
       ```
       If your package manager doesn't have Deno, install Node.js instead:
       ```shell
       sudo apt install nodejs
       ```
     - Arch-based (e.g. Arch or Manjaro):
       ```shell
       sudo pacman -Syu ffmpeg deno
       ```
1. Download yt-dlp.
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
        uv tool install --pre "yt-dlp[default]"
        ```
1. Download a video.
   1. Execute:
      ```shell
      yt-dlp -P PATH "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](Common&#x20;Usage.md#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.

> [!IMPORTANT]
> If you needed to install Node.js, add `--js-runtimes node` to your command. Consider adding this parameter to your config, so you don't have to manually add it to each yt-dlp invocation. To learn more, see [How to create a config](Common&#x20;Usage.md#how-to-create-a-config).

For common usage commands, move on to [Common Usage](Common&#x20;Usage.md).
