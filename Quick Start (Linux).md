# Linux

On Linux, we recommend installing yt-dlp through `pipx`.

Before starting, ensure you have removed any pre-existing yt-dlp installations from your system's package manager:
- Debian-based (e.g. Debian, Ubuntu, or Mint):
  ```shell
  sudo apt remove yt-dlp
  ```
- Arch-based (e.g. Arch or Manjaro):
  ```shell
  sudo pacman -Rs yt-dlp
  ```

---

1. Install FFmpeg.
   - FFmpeg can be installed from your distribution's package manager. Outdated versions served by package managers are generally okay to use.  
     - Debian-based:
       ```shell
       sudo apt update && sudo apt install ffmpeg
       ```
     - Arch-based:
       ```shell
       sudo pacman -Syu ffmpeg
       ```
> [!NOTE]
> For Arch Linux users, it is recommended to install the [yt-dlp-git](https://aur.archlinux.org/packages/yt-dlp-git) package from the [AUR](https://wiki.archlinux.org/title/Arch_User_Repository). However, instructions for installing from the AUR are outside the scope of this guide. If you don't already know how (or don't want to) install from the AUR, then follow the general Linux instructions below.
2. Install `pipx` from your distribution's package manager.
     - Debian-based:
       ```shell
       sudo apt install pipx
       pipx ensurepath
       ```
     - Arch-based:
       ```shell
       sudo pacman -Syu python-pipx
       pipx ensurepath
       ```
   Restart your terminal after installing `pipx`.
3. Install yt-dlp and Deno (required for YouTube downloads) by executing:
   ```shell
   pipx install --pip-args=--pre "yt-dlp[default,deno]"
   ```
4. Download a video.
   1. Execute:
      ```shell
      yt-dlp -P PATH "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](Common&#x20;Usage.md#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.

For common usage commands, move on to [Common Usage](Common&#x20;Usage.md).
