## Windows

On Windows, we recommend installing yt-dlp through `winget`:
1. Open a terminal (`cmd` or powershell)  
2. Type `winget install -e --id yt-dlp.yt-dlp`, hit Enter and follow the instructions on screen  
3. Restart your terminal (close it and open it again)  
4. Run `yt-dlp --update-to nightly`  
5. Execute `yt-dlp -P PATH "URL"`. Replace `URL` with the actual video URL you want to download. Your video will start downloading. Check [How to download files to a specific folder](#how-to-download-files-to-a-specific-folder) for more info about the `-P` parameter. 

Note: `winget` is preinstalled in Windows 11 and newer versions of Windows 10 (after 1709). If you don't have `winget` (if your terminal says `'winget' is not recognized[...]`), follow these instructions to install `winget`:
1. Open Powershell with administrator permissions.  
2. Execute `Add-AppxPackage -RegisterByFamilyName -MainPackage Microsoft.DesktopAppInstaller_8wekyb3d8bbwe`  
3. Reboot your PC.  
   
<details>
<summary>

Can't install yt-dlp through winget?

</summary>

You can manually download and install `yt-dlp.exe`, `ffmpeg`, and `deno`.

1. Download yt-dlp, FFmpeg, and Deno  
   1. Download yt-dlp.exe from [https://github.com/yt-dlp/yt-dlp-nightly-builds/releases/latest/download/yt-dlp.exe](https://github.com/yt-dlp/yt-dlp-nightly-builds/releases/latest/download/yt-dlp.exe)  
   2. Download FFmpeg from [https://github.com/yt-dlp/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip](https://github.com/yt-dlp/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip).   
   3. (Required for YouTube downloads) Download Deno from [https://github.com/denoland/deno/releases/latest/download/deno-x86\_64-pc-windows-msvc.zip](https://github.com/denoland/deno/releases/latest/download/deno-x86_64-pc-windows-msvc.zip)   
   4. Create a yt-dlp folder with the above files somewhere e.g., in your `C` drive: `C:\yt-dlp`  
   5. Put `yt-dlp.exe` there along with `ffmpeg.exe` (extracted from the bin folder inside the [ffmpeg-master-latest-win64-gpl.zip](https://github.com/yt-dlp/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip) file downloaded in step 1b) and `deno.exe` (extracted from the [deno-x86\_64-pc-windows-msvc.zip](https://github.com/denoland/deno/releases/latest/download/deno-x86_64-pc-windows-msvc.zip) file in step 1c).  
      1. After extraction, you can delete the remaining files (and the `.zip`s).  
2. Add yt-dlp to your PATH  
   1. Press the Windows key, type "environment variables for your account” and click the top result  
   2. Double click on "Path” in the area under "User variables for \[your PC username\]”  
   3. Click on "New”  
   4. Type `C:\yt-dlp` (or the location of your yt-dlp folder, if you chose to create it somewhere else) and click "OK” on every window.  
3. Download a video  
   1. Open a terminal (`cmd` or powershell), and execute `yt-dlp -P PATH "URL"`. Replace `URL` with the actual video URL you want to download. Your video will start downloading. See [How to download files to a specific folder](#how-to-download-files-to-a-specific-folder) to learn more about the `-P` parameter. 
</details>
