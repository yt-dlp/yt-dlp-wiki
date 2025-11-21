# Basic Usage

The following subsections explain what parameters to use for common scenarios. You can concatenate several parameters to specify more than one option.



<details>
<summary>

## How to update yt-dlp

</summary>

Before panicking and wondering what's wrong with yt-dlp, make sure it's up to date. **Fast-changing websites, like YouTube, require frequent yt-dlp updates in order to download properly.**

To update, execute the following command for your operating system (assuming you've installed yt-dlp based on the recommended installation instructions).

1) Windows:
   ```shell
   yt-dlp -U
   ```  
2) macOS:
   ```shell
   brew upgrade yt-dlp
   ```
3) Linux:
   ```shell
   uv tool upgrade yt-dlp
   ```  
4) iOS:
   ```shell
   pip install -U yt-dlp[default] yt-dlp-apple-webkit-jsi
   ```
5) Android:
   ```
   pip install -U yt-dlp[default]
   ```

### **How to update yt-dlp's external dependencies**

Although not as important or urgent as updating yt-dlp itself, it's good practice to update its external dependencies (FFmpeg and Deno) **as older versions may become unsupported by yt-dlp**. Internal dependencies, like yt-dlp-ejs, are updated with every yt-dlp update.

1. Windows:  
   1. `winget` installation:
      ```shell
      winget upgrade yt-dlp
      ```
   1. Manual yt-dlp.exe installation:
      1. Update Deno by executing:
         ```shell
         deno upgrade
         ```
      1. You will need to redownload `ffmpeg.exe` and `ffprobe.exe` [here](idk how the actual link would look like to `Quick Start (Windows).md`)
1. macOS:
   ```shell
   brew upgrade ffmpeg deno
   ```  
1. Linux
	1. Depending on (todo)
1. iOS: FFmpeg is updated when a-Shell updates.
1. Android:
   ```shell
   pkg update && pkg upgrade && pkg upgrade ffmpeg deno
   ```

</details>



<details>
<summary>

## How to download files to a specific folder

</summary>

```shell
yt-dlp -P PATH "URL"
```
Replace `PATH` with the absolute path to your folder.

For example, to download to a folder named Videos inside your yt-dlp folder on Windows, execute:
```shell
yt-dlp -P "C:\yt-dlp\Videos" "URL"
```

To download to your Downloads folder, execute:
```shell
yt-dlp -P "%USERPROFILE%\Downloads" URL
```

**Tip:** Consider adding this parameter to your config, so you don't have to manually add it to each yt-dlp invocation. To learn more, see [How to create a config](#how-to-create-a-config).

</details>



<details>
<summary>

## How to download files without the numbers and letters (video ID) at the end

</summary>

```shell
yt-dlp -o "%(title)s.%(ext)s" "URL"
```

**Tip:** Consider adding this parameter to your config, so you don't have to manually add it to each yt-dlp invocation. To learn more, see [How to create a config](#how-to-create-a-config).

</details>



<details>
<summary>

## How to download `.mp4`

</summary>

```shell
yt-dlp -t mp4 "URL"
```

**NOTE:** On YouTube, this will limit the maximum possible quality to 1080p. You may also end up downloading **formats with inferior quality** and/or formats with a **higher filesize**. This happens because you are specifying a combination of codecs (H.264, aka. AVC, for video and AAC for audio) that may serve inferior quality. Because of this, it's not recommended to "download mp4" unless it's truly necessary. 

Valid reasons include importing videos to use in video editors (like Premiere Pro), but generally not because "my media player doesn't support webm files". We recommend players like [VLC](https://www.videolan.org/vlc/) or [MPV](https://mpv.io/installation/).

It's important to note that video ≠ `.mp4`. `.mp4` is just one of several containers ("formats") that support video.

There are specific cases \- like using a video in DaVinci Resolve or embedding a video in Telegram \- where the container format matters more than the codec downloaded. In these situations, you can use:
```shell
yt-dlp --merge mp4 --remux mp4 "URL"
```
This will ensure you get the highest available quality while still producing a `.mp4` file.

***If you don't know what "containers" or "codecs" are, feel free to download a video with `-t mp4` then redownload with `--merge mp4 –remux mp4` and see what works best for your needs.***

</details>



<details>
<summary>

## How to download audio

</summary>

```shell
yt-dlp -x "URL"
```
This will download the highest-quality audio available.

</details>



<details>
<summary>

## How to download `.mp3`

</summary>

```shell
yt-dlp -t mp3 URL
```
**NOTE:** This will download the best audio quality available and re-encodes it to `.mp3`, a process that loses quality. This is **not recommended** unless you are using a device that does not support playingback `.opus` or `.aac` (`m4a`). 

</details>



<details>
<summary>

## How to download `.aac` (`.m4a`)

</summary>

```shell
yt-dlp -t aac URL
```
**NOTE:** This should be used only on devices where `.opus` audio is not playable through any available audio player.

</details>



<details>
<summary>

## How to download the thumbnail (cover art) of a video or audio

</summary>

```shell
yt-dlp --embed-thumbnail "URL"
```

### How to crop the thumbnail into a square

```shell
yt-dlp --embed-thumbnail --convert-thumbnails jpg --ppa "ThumbnailsConvertor+ffmpeg_o:-vf crop=ih" "URL"
```

</details>



<details>
<summary>

## How to download the metadata (uploader, album, etc.) of a video or audio

</summary>

```shell
yt-dlp --embed-metadata "URL"
```

</details>



<details>
<summary>

## How to download in a specific quality

</summary>

```shell
yt-dlp -S res:X "URL"
```

Replace `X` with your desired resolution (e.g. 144, 240, 360, 480, 720, 1080, 2k, or 4k).

**NOTE:** If there isn't a video stream at your specified resolution, yt-dlp will download the next lower-resolution video.

</details>



<details>
<summary>

## How to download from `x` time to `y` time of a video

</summary>

```shell
yt-dlp --download-sections "*START-FINISH" "URL"
```

Replace `START` and `FINISH` with your desired timestamps in `HH:MM:SS.MS` (or `MM:SS`) format. You can also use `inf` to indicate the end of the video. For example, to download from the 10-second mark to the end, execute `yt-dlp --download-sections "*00:10-inf" URL`.

**NOTE:** If the downloaded video has issues (e.g. desynchronized audio/video or frozen/black frames at the beginning and/or end), you can try adding the `--force-keyframes-at-cut` parameter:
```shell
yt-dlp --download-sections "*START-FINISH" --force-keyframes-at-cut URL
```
This may take awhile depending on your system's specifications, and the duration and resolution of the video. This also re-encodes the video, which will result in quality loss.

</details>



<details>
<summary>

## How to download a playlist/channel

</summary>

```shell
yt-dlp -t sleep "URL"
```

Remember to quote your URL (surround it with `"`) to prevent [unexpected behaviors](https://github.com/yt-dlp/yt-dlp/wiki/FAQ#video-url-contains-an-ampersand--and-im-getting-some-strange-output-1-2839-or-v-is-not-recognized-as-an-internal-or-external-command). `-t sleep` helps prevent temporary restrictions on sites like YouTube.

If you're going to download the playlist/channel again, use `--download-archive` to avoid unnecessary network requests of already-downloaded videos in the future:
```shell
yt-dlp -t sleep --download-archive archive.txt "URL"
```

</details>



<details>
<summary>

## How to download a specific video (or several) from a playlist/channel

</summary>

```shell
yt-dlp -I POSITION "URL"
```

Replace `POSITION` with the video's position in the playlist/channel.

Download several videos by separating their positions with `,`:
```shell
yt-dlp -I 3,6 "URL"
```
This will download the 3rd and 6th video of the playlist.

Download a range of videos with `:`:
```shell
yt-dlp -I 3:7 "URL"
```
This will download from the 3rd to 7th video (3rd, 4th, 5th, 6th and 7th). 

The order is the same as it appears in the site (e.g. YouTube sorts videos from newest to oldest). To flip the order, (e.g. oldest to newest for YouTube), add `--playlist-reverse`.

</details>



<details>
<summary>

## How to use my account to download (how to use the cookies of my account)

</summary>

```shell
yt-dlp --cookies-from-browser BROWSER "URL"
```

**CAUTION:** You shouldn't always use your account's cookies, but only in specific scenarios:

1. The video is age-restricted (and you can watch age-restricted videos with your account). 
1. The video is paywalled/members-only (and you have a membership in that channel with your account).
1. Your account has a premium subscription (e.g. YouTube Premium or Soundcloud Go(+)) and you want to download premium formats.
1. You have been IP restricted and you want to continue downloading without changing your IP (explained [here](https://github.com/yt-dlp/yt-dlp/wiki/Extractors#common-youtube-errors) for YouTube).

In cases where you need to use your account's cookies, avoid using an important account's cookies, as this may result in the account being restricted.

**NOTE:** `--cookies-from-browser` <ins>**does not work for Chromium-based browsers**</ins> (e.g. Chrome, Edge, Brave, Opera) <ins>**on _Windows_**</ins>. You must manually export cookies. If you encounter `The provided YouTube account cookies are no longer valid.`, we also recommend manually exporting cookies.

<details>
<summary>

How to manually export YouTube cookies

</summary>

If you want to use the cookies of your YouTube account:

1. Install [Get cookies.txt LOCALLY](https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc).
   1. If you're on a Firefox-based browser, install [https://addons.mozilla.org/en-US/firefox/addon/cookies-txt](https://addons.mozilla.org/en-US/firefox/addon/cookies-txt) instead.
1. In a tab, go to `chrome://extensions/?id=cclelndahbckbenkjhflpdbgdldlbecc` and enable "Allow in incognito"
   1. If you're on a Firefox-based browser, go to `about:addons`, enter the `cookies.txt` extension's settings, and allow "Run in Private Windows".
1. Open an ***incognito window*** and log into YouTube.
1. Open [https://youtube.com/robots.txt](https://youtube.com/robots.txt) in a new tab and ***close all other incognito YouTube tabs***..
1. Click on the extension icon in the top right, click on "Export As" and save them as "cookies.txt". Then close the incognito window (so the cookies will never rotate).
   1. If you're on a Firefox-based browser, click on the extension icon, click on "Current Container and Site", and ensure you're saving the file prenamed `cookies.firefox-private.txt`.
1. Pass the cookies to yt-dlp using `--cookies "PATHTOCOOKIES"`.
   1. For example, if you've saved the cookies file to your Downloads folder on Windows:
      ```shell
      yt-dlp --cookies "%USERPROFILE%\Downloads\cookies.txt" "URL"
      ```

</details>

<details>
<summary>

How to manually export cookies for all other sites

</summary>

1. Install [Get cookies.txt LOCALLY](https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc)
   1. If you're on a Firefox-based browser, install [cookies.txt](https://addons.mozilla.org/en-US/firefox/addon/cookies-txt) instead
1. Go to the website and ensure you're logged in
1. Click on the extension icon in the top right, click on "Export As" and save them as "cookies.txt".
1. Pass the cookies to yt-dlp using `--cookies "PATHTOCOOKIES"`
   1. For example, if you've saved the cookies file to your Downloads folder on Windows:
      ```shell
      yt-dlp --cookies "%USERPROFILE%\Downloads\cookies.txt" "URL"
      ```

</details>

</details>



<details>
<summary>

## How to download subtitles

</summary>

```shell
yt-dlp --embed-subs "URL"
```

This will download the video's original language subtitles and embed them into the video file.

To download the subtitle files to your disk instead:
```shell
yt-dlp --write-subs "URL"
```

You can embed and write subs together:
```shell
yt-dlp --write-subs --embed-subs "URL"
```

<details>
<summary>

### How to download subtitles in specific language(s)

</summary>

```shell
yt-dlp --embed-subs --sub-langs LANGUAGECODE "URL"
```

Replace `LANGUAGECODE` with the [ISO 639 two-character language code](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes)(s) (Set 1). For example, `yt-dlp --embed-subs --sub-langs en,es URL` will download English and Spanish subtitles.

**TIP:** To view the entire list of downloadable subtitles' language codes:
```shell
yt-dlp --list-subs "URL"
``` 

</details>


<details>
<summary>

### How to download subtitles in all available languages

</summary>

```shell
yt-dlp --embed-subs --sub-langs all "URL"
```

Use `-` before a language code to exclude language(s). For example:
```shell
yt-dlp --embed-subs --sub-langs all,-live_chat URL
```
This will to download all available subtitles, except for YouTube's live chat replay.

</details>


<details>
<summary>

### How to download all variants of a language

</summary>

```shell
yt-dlp --embed-subs --sub-langs "BASICLANGUAGECODE.*" "URL"
```

For example:
```
yt-dlp --embed-subs --sub-langs "en.*" URL
```
This will download all English variants' subtitles (en, en-US, en-GB, etc.) using regex.

</details>


<details>
<summary>

### How to download auto-generated subtitles

</summary>

```shell
yt-dlp --write-auto-subs "URL"
```
You can use this option with `--embed-subs` to embed the auto-generated subtitles into the video file.

**NOTE:** On YouTube, auto-generated subtitles are highly restricted, likely due to AI-scrapers mass downloading. You may encounter HTTP 429 errors despite using `-t sleep` or other sleep-related parameters. See [https://github.com/yt-dlp/yt-dlp/issues/13831](https://github.com/yt-dlp/yt-dlp/issues/13831) for more information.

</details>

</details>



<details>
<summary>

## How to download audio from different languages

</summary>

```shell
yt-dlp -f bv+ba[language=LANGUAGECODE]/b[language=LANGUAGECODE] --embed-metadata "URL"
```

Replace `LANGUAGECODE` with the [ISO 639 two-character language code](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes)(s) (Set 1). For example, `yt-dlp -f bv+ba[language=es]/b[language=es] --embed-metadata URL` will download Spanish audio. 

`--embed-metadata` is required in order to ensure the appropriate language code is tagged with its respective audio track. Otherwise, all audio tracks may be incorrectly marked as English.


<details>
<summary>

### How to download more than 1 language

</summary>

```shell
yt-dlp -f bv+ba[language=LANGUAGECODE1]+ba[language=LANGUAGECODE2] --audio-multistreams --embed-metadata "URL".
``` 

For example, `yt-dlp -f bv+ba[language=es]+ba[language=en]+ba[language=fr] --audio-multistreams --embed-metadata URL` would download the video with Spanish, English and French audio.

</details>


<details>
<summary>

### How to download all languages

</summary>

There is no universal way to download all the audio languages without downloading all formats (which may include lower-quality duplicates for sites like YouTube). However, on YouTube, this can be achieved with:
```shell
yt-dlp -f "bv+mergeall[format_id^=251]" --audio-multistreams "URL"
```

</details>

</details>



<details>
<summary>

## How to create a config

</summary>

If you want to always use certain parameters (options) with yt-dlp without writing them every single time, you should create a configuration file. This file stores your preferred parameters, which are automatically applied whenever you run yt-dlp. This is useful for setting a default download directory (where your files are downloaded) or defining a specific naming format for your downloads.

If you're on **Windows** and installed yt-dlp via **`winget`**:
1. Open Windows Explorer
1. In the location bar (top of Explorer), type `%appdata%` and press Enter
1. Create a file named `yt-dlp.conf` (not `yt-dlp.conf.txt`, but `yt-dlp.conf`)
   1. You can do this by right clicking an empty space in the folder \> click "New" in the context menu \> click "Text document"
   1. To confirm that you didn't create `yt-dlp.conf.txt`, ensure that you have enabled file name extensions. To do this, press the Windows key, search for "File Explorer options" \> go to the "View" tab \> **uncheck** "Hide extensions for known file types"
   1. Using Notepad, add your parameters inside.

If you're on **Windows** and **manually installed** `yt-dlp.exe`:  
1. Create a file named `yt-dlp.conf` (not `yt-dlp.conf.txt`, but `yt-dlp.conf`) in the same folder where your yt-dlp.exe is located.
   1. You can do this by right clicking an empty space in the folder \> click "New" in the context menu \> click "Text document"
      1. To confirm that you didn't create `yt-dlp.conf.txt`, ensure that you have enabled file name extensions. To do this, press the Windows key, search for "File Explorer options" \> go to the "View" tab \> **uncheck** "Hide extensions for known file types"
   1. Using Notepad, add your parameters inside.

<!-- need to add more to linux -->

If you're on **Mac or Linux**:  
   1. Create a file named `yt-dlp.conf` (not `yt-dlp.conf.txt`, but `yt-dlp.conf`) inside your home directory and add your parameters inside using a text editor.  

If you're on **Android**:  
   1. Execute `nano yt-dlp.conf` to create a `yt-dlp.conf` file in your home directory (where your terminal opens)  
   1. Add your parameters inside  
   1. Use `CTRL + O`, press enter, and use `CTRL + X`

<!-- how does one use vim for iOS in a-Shell -->

After creating a config file, you can add useful parameters like `-P PATH`  or `-o "%(title)s.%(ext)s"`. To learn more, see [How to download files to a specific folder](#how-to-download-files-to-a-specific-folder) and [How to download files without the numbers and letters (IDs) at the end](#how-to-download-files-without-the-numbers-and-letters-video-id-at-the-end).

</details>



# Need Help?

Ensure you're on the [latest version](#how-to-update-yt-dlp) before asking for help. If you encounter any issues using yt-dlp despite being on the latest version, feel free to [open a GitHub issue](https://github.com/yt-dlp/yt-dlp/issues/new/choose). For quick assistance, join our [Discord server](https://discord.gg/H5MNcFW63r).