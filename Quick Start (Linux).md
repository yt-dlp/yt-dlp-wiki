## Linux

TODO/finish

1. Download ffmpeg and deno  
- Deno and ffmpeg can be installed from your distribution's package manager. Outdated versions served by package managers are generally okay to use.  
  * Ubuntu: `sudo apt-get ffmpeg deno`  
  * Arch-based: `sudo pacman -S ffmpeg deno`  
  * Other distros `[insert instructions]`  
2. Download yt-dlp  
- If you are using Arch Linux you can install yt-dlp-git from AUR ([https://aur.archlinux.org/packages/yt-dlp-git](https://aur.archlinux.org/packages/yt-dlp-git)).  
- For all other users (e.g. Ubuntu and Debian) we recommend installing yt-dlp via `uv`:  
  1. Download `uv` from [https://github.com/astral-sh/uv/releases](https://github.com/astral-sh/uv/releases)  
     2. Extract `uv` and `uvx` from the tar.  
     3. Execute `uv tool install uv`   
     4. Execute `uv tool install --pre "yt-dlp[default]"`  
3. Download a video  
   1. In a terminal window, execute `yt-dlp -P PATH "URL"`. Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.
