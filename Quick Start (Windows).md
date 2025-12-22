# Windows

On Windows, we recommend installing yt-dlp through WinGet. WinGet **will also automatically download FFmpeg and Deno (required for YouTube downloads).**

1. Install yt-dlp.
   1. Open a terminal.
      1. Press the Windows key, type "cmd" and click the top result.
   1. Execute the following command by copy-pasting it into your Terminal and hitting Enter:
      ```shell
      winget install -e --id yt-dlp.yt-dlp.nightly --source winget
      ```
      1. Follow the on-screen instructions.
   1. Restart your terminal (close it and open it again).
   1. Execute:
      ```shell
      yt-dlp -U
      ```
1. Download a video.
   1. Execute:
      ```shell
      yt-dlp -P PATH "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](Common&#x20;Usage.md#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.

> [!NOTE]
> WinGet is preinstalled on Windows 11 and newer versions of Windows 10 (after build 1709). If you don't have WinGet (if your terminal says `'winget' is not recognized[...]`), follow these instructions to install WinGet:
1. Open PowerShell with administrator permissions.
   1. Press the Windows key, type "powershell", right click "Windows PowerShell", and click "Run as Administrator".
1. Execute:
   ```powershell
   Add-AppxPackage -RegisterByFamilyName -MainPackage Microsoft.DesktopAppInstaller_8wekyb3d8bbwe
   ```
1. Reboot your PC.

<details>
<summary>

#### Can't install yt-dlp through WinGet?

</summary>

You can follow the manual installation guide below.

1. Download yt-dlp, FFmpeg, and Deno.
   1. Download [yt-dlp.exe](https://github.com/yt-dlp/yt-dlp-nightly-builds/releases/latest/download/yt-dlp.exe).
   1. Download [ffmpeg.exe and ffprobe.exe](https://github.com/yt-dlp/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip).
   1. (Required for YouTube downloads) Download [deno.exe](https://github.com/denoland/deno/releases/latest/download/deno-x86_64-pc-windows-msvc.zip).
   1. Create a yt-dlp folder for the files above. For example, in your `C` drive: `C:\yt-dlp`
   1. Put `yt-dlp.exe`, `ffmpeg.exe` and `ffprobe.exe` (extracted from the bin folder inside [ffmpeg-master-latest-win64-gpl.zip](https://github.com/yt-dlp/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip), downloaded in step 1ii), and `deno.exe` (extracted from [deno-x86\_64-pc-windows-msvc.zip](https://github.com/denoland/deno/releases/latest/download/deno-x86_64-pc-windows-msvc.zip), downloaded in step 1iii) inside the yt-dlp folder.
      1. After extraction, you can delete the all remaining files, including the `.zip` files.
1. Add yt-dlp to your PATH.
   1. Press the Windows key, type "environment variables for your account", and click the top result.
   1. Double click on the "Path" variable under "User variables for \[your PC username\]".
   1. Click on "New".
   1. Type `C:\yt-dlp` (or the location of your yt-dlp folder, if you chose to create it somewhere else) and click "OK" on every window.  
1. Download a video.
   1. Open a terminal (`cmd` or PowerShell), and execute:
      ```shell
      yt-dlp -P PATH "URL"
      ```
      Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](Common&#x20;Usage.md#How-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter.

</details>

For common usage commands, move on to [Common Usage](Common&#x20;Usage.md).
