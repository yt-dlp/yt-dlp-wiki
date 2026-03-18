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
> [!NOTE]
> For Arch Linux users, it is recommended to install the [yt-dlp-git](https://aur.archlinux.org/packages/yt-dlp-git) package from the [AUR](https://wiki.archlinux.org/title/Arch_User_Repository). However, instructions for installing from the AUR are outside the scope of this guide. If you don't already know how (or don't want to) install from the AUR, then follow the general Linux instructions.
   1. Install uv from [https://github.com/astral-sh/uv/releases](https://github.com/astral-sh/uv/releases). You'll likely need to download [the x64 binary](https://github.com/astral-sh/uv/releases/latest/download/uv-x86_64-unknown-linux-gnu.tar.gz).
      1. Extract the tarball. You can do this by executing:
         ```shell
         tar -xf ~/Downloads/uv-x86_64-unknown-linux-gnu.tar.gz -C ~/Downloads/
         ```
      1. Change your terminal's current working directory into the extracted folder:
         ```shell
         cd ~/Downloads/uv-x86_64-unknown-linux-gnu/
         ```
      1. Install `uv` onto your local system:
         ```shell
         ./uv tool install uv
         ```
      1. Ensure `uv` is in your PATH, so you can execute your local system's `uv` and tools installed via `uv` later:
         ```shell
         ./uv tool update-shell
         ```
         Close and reopen your terminal. After this point, you can delete the downloaded `.tar.gz` file and all extracted files.
   1. Install yt-dlp by executing:
      ```shell
      uv tool install --prerelease allow "yt-dlp[default,deno]"
      ```
1. Download a video.
   1. Execute:
      ```shell
      yt-dlp -P PATH "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](Common&#x20;Usage.md#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.

For common usage commands, move on to [Common Usage](Common&#x20;Usage.md).
