# Common Usage

The following subsections explain what parameters to use for common scenarios. **You can use multiple parameters in a single command.**



<details>
<summary>

## How to update yt-dlp

</summary>

Before panicking and wondering what's wrong with yt-dlp, make sure it's up to date. **Fast-changing websites, like YouTube, require frequent yt-dlp updates in order to download properly.**

To update, execute the following command for your operating system (assuming you've installed yt-dlp based on the recommended installation instructions):

1. Windows:
   ```shell
   yt-dlp -U
   ```
1. macOS:
   ```shell
   brew upgrade yt-dlp
   ```
1. Linux:
   - Debian-based (e.g. Debian, Ubuntu, or Mint):
     ```shell
     uv tool upgrade yt-dlp
     ```
   - Arch:
     ```shell
     yay
     ```
1. iOS/iPadOS:
   ```shell
   pip install -U --pre yt-dlp[default] yt-dlp-apple-webkit-jsi
   ```
1. Android:
   ```shell
   pip install -U --pre yt-dlp[default]
   ```


<details>
<summary>

### How to update yt-dlp's external dependencies

</summary>

Although not as important or urgent as updating yt-dlp itself, it's good practice to update its external dependencies (FFmpeg and Deno) **as older versions may become unsupported by yt-dlp**. Internal dependencies, like yt-dlp-ejs, are updated with every yt-dlp update.

1. Windows:
   1. `winget` installation:
      ```shell
      winget upgrade -e --id yt-dlp.yt-dlp.nightly --source winget
      ```
   1. Manual yt-dlp.exe installation:
      1. Update Deno by executing:
         ```shell
         deno upgrade
         ```
      1. You will need to redownload `ffmpeg.exe` and `ffprobe.exe` from [here](https://github.com/yt-dlp/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip).
1. macOS:
   ```shell
   brew upgrade ffmpeg deno
   ```
1. Linux:
   - Debian-based (e.g. Debian, Ubuntu, or Mint):
     ```shell
     sudo apt update && sudo apt upgrade && sudo apt install ffmpeg deno
     ```
     - If you've installed Node.js:
       ```shell
       sudo apt update && sudo apt upgrade && sudo apt install ffmpeg nodejs
       ```
   - Arch-based (e.g. Arch or Manjaro):
   ```shell
   sudo pacman -Syu
   ```
1. iOS/iPadOS: FFmpeg is updated when a-Shell updates. Instead of Deno, you're using [yt-dlp-apple-webkit-jsi](https://github.com/grqz/yt-dlp-apple-webkit-jsi), which is updated with the yt-dlp update command above.
1. Android:
   ```shell
   pkg update && pkg upgrade && pkg upgrade ffmpeg deno
   ```

</details>

---

</details>



<details>
<summary>

## How to download files to a specific folder

</summary>

```shell
yt-dlp -P "PATH" "URL"
```

Replace `PATH` with the absolute path to your folder.

For example, to download to a folder named Videos inside your yt-dlp folder on Windows, execute:

```shell
yt-dlp -P "C:\yt-dlp\Videos" "URL"
```

To download to your Downloads folder on Windows, execute:

```shell
yt-dlp -P "%USERPROFILE%\Downloads" "URL"
```

**Tip:** Consider adding this parameter to your config, so you don't have to manually add it to each yt-dlp invocation. To learn more, see [How to create a config](#how-to-create-a-config).

---

</details>



<details>
<summary>

## How to download files without the numbers and letters (video ID) at the end

</summary>

```shell
yt-dlp -o "%(title)s.%(ext)s" "URL"
```

**Tip:** Consider adding this parameter to your config, so you don't have to manually add it to each yt-dlp invocation. To learn more, see [How to create a config](#how-to-create-a-config).

---

</details>



<details>
<summary>

## How to download `.mp4`

</summary>

```shell
yt-dlp -t mp4 "URL"
```

**NOTE:** On YouTube, this will limit the maximum possible quality to 1080p. This happens because you are specifying a combination of codecs (H.264/AVC for video and AAC for audio) that may serve **formats with inferior quality** and/or **higher filesizes**. Because of this, it's not recommended to "download mp4" unless it's truly necessary.

Valid reasons include importing videos to use in video editors (like Premiere Pro), but generally not because "my media player doesn't support webm files". We recommend players like [VLC](https://www.videolan.org/vlc/) or [MPV](https://mpv.io/installation/).

It's important to note that video ≠ `.mp4`. `.mp4` is just one of several containers ("formats") that support video.

There are specific cases \- like using a video in DaVinci Resolve or embedding a video in Telegram \- where the container format matters more than the codec downloaded. In these situations, you can use:

```shell
yt-dlp --merge mp4 --remux mp4 "URL"
```

This will ensure you get the highest available quality while still producing a `.mp4` file.

***If you don't know what "containers" or "codecs" are, feel free to download a video with `-t mp4` then redownload with `--merge mp4 –remux mp4` and see what works best for your needs.***

---

</details>



<details>
<summary>

## How to download audio

</summary>

```shell
yt-dlp -x "URL"
```

This will download the highest-quality audio available.

---

</details>



<details>
<summary>

## How to download MP3

</summary>

```shell
yt-dlp -t mp3 "URL"
```

**NOTE:** This will download the MP3 given directly by the site if available; if MP3 is not available (e.g. on YouTube), this will download the highest-quality audio stream available and re-encode it to MP3, which will reduce audio quality.

If you're downloading from YouTube, this is **not recommended** unless you are using a device where Opus or AAC (`.aac`/`.m4a`) audio is not playable through any available audio player.

---

</details>



<details>
<summary>

## How to download AAC (`.aac`/`.m4a`)

</summary>

```shell
yt-dlp -t aac "URL"
```

**NOTE:** This will download the AAC audio given directly by the site if available (e.g. on YouTube); if AAC is not available, this will download the highest-quality audio stream available and re-encode it to AAC, which will reduce audio quality.

If you're downloading from YouTube, this should be used only on devices where Opus audio is not playable through any available audio player. YouTube's Opus audio provides better audio quality than its AAC counterpart.

---

</details>



<details>
<summary>

## How to embed the thumbnail (cover art) to a video or audio

</summary>

```shell
yt-dlp --embed-thumbnail "URL"
```

### How to crop the thumbnail into a square

```shell
yt-dlp --embed-thumbnail --convert-thumbnails jpg --ppa "ThumbnailsConvertor+ffmpeg_o:-vf crop=ih" "URL"
```

---

</details>



<details>
<summary>

## How to embed metadata (uploader, album, etc.) to a video or audio

</summary>

```shell
yt-dlp --embed-metadata "URL"
```

---

</details>



<details>
<summary>

## How to download in a specific quality

</summary>

```shell
yt-dlp -S res:X "URL"
```

Replace `X` with your desired resolution (e.g. 144, 240, 360, 480, 720, 1080, 1440, or 2160).

**NOTE:** If there isn't a video stream at your specified resolution, yt-dlp will download the next lower-resolution video.

---

</details>



<details>
<summary>

## How to download from `X` time to `Y` time of a video

</summary>

```shell
yt-dlp --download-sections "*START-FINISH" "URL"
```

Replace `START` and `FINISH` with your desired timestamps in `HH:MM:SS.MS` (or `MM:SS`) format. You can also use `inf` to indicate the end of the video. For example, to download from the 10-second mark to the end, execute `yt-dlp --download-sections "*00:10-inf" "URL"`.

**NOTE:** If the downloaded video has issues (e.g. desynchronized audio/video, frozen/black frames at the start and/or end, or a few extra seconds at the start and/or end), you can try adding the `--force-keyframes-at-cut` parameter:

```shell
yt-dlp --download-sections "*START-FINISH" --force-keyframes-at-cut "URL"
```

This may take awhile depending on your system's specifications, and the duration and resolution of the video. This also re-encodes the video, which will result in quality loss.

---

</details>



<details>
<summary>

## How to download a playlist/channel

</summary>

```shell
yt-dlp -t sleep "URL"
```

Remember to quote your URL (surround it with `"`) to prevent [unexpected behaviors](https://github.com/yt-dlp/yt-dlp/wiki/FAQ#video-url-contains-an-ampersand--and-im-getting-some-strange-output-1-2839-or-v-is-not-recognized-as-an-internal-or-external-command). `-t sleep` helps prevent yt-dlp from exceeding rate limits on sites like [YouTube](https://github.com/yt-dlp/yt-dlp/wiki/Extractors#common-youtube-errors).

If you're going to download the playlist/channel again, use `--download-archive` to avoid unnecessary network requests of already-downloaded videos in the future:

```shell
yt-dlp -t sleep --download-archive archive.txt "URL"
```

Use `--download-archive archive.txt` again the next time you download the playlist/channel.

The order is the same as it appears in the site (e.g. YouTube sorts videos from newest to oldest). To flip the order (e.g. oldest to newest for YouTube), add `-I ::-1`.

---

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

Download backwards with `-` and another `:`:

```shell
yt-dlp -I -3:-7:-1 "URL"
```

This will download from the third-to-last video to the seventh-to-last video, and the trailing `-1` means stepping backwards by 1.

---

</details>



<details>
<summary>

## How to use my account to download (how to use the cookies of my account)

</summary>

```shell
yt-dlp --cookies-from-browser BROWSER "URL"
```

**CAUTION:** You shouldn't always use your account's cookies, but only in specific scenarios:

1. The content is age-restricted (and you can watch the age-restricted content with your account).
1. The content is paywalled/members-only (and you have paid access to the content).
1. Your account has a premium subscription (e.g. YouTube Premium or Soundcloud Go) and you want to download premium formats.
1. You have been IP-restricted and you want to continue downloading without changing your IP (YouTube rate limits explained [here](https://github.com/yt-dlp/yt-dlp/wiki/Extractors#common-youtube-errors)).

In cases where you need to use your account's cookies, avoid using an important account's cookies, as this may result in the account being restricted. DO NOT log in to Instagram/Facebook, as they can detect yt-dlp downloads with your account and may ban your account after a few downloads.

**NOTE:** `--cookies-from-browser` <ins>**does not work for Chromium-based browsers**</ins> (e.g. Chrome, Edge, Brave, or Opera) <ins>**on _Windows_**</ins>. You must manually export cookies. If you encounter `The provided YouTube account cookies are no longer valid.`, we also recommend manually exporting cookies.

<details>
<summary>

### How to manually export YouTube/TikTok cookies

</summary>

1. Install "Get cookies.txt LOCALLY" ([Chrome](https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc), [Firefox](https://addons.mozilla.org/en-US/firefox/addon/get-cookies-txt-locally/)).
1. In a tab, go to `chrome://extensions/?id=cclelndahbckbenkjhflpdbgdldlbecc` and enable "Allow in incognito".
   - If you're on a Firefox-based browser, go to `about:addons`, enter the "Get cookies.txt LOCALLY" extension's settings, and allow "Run in Private Windows".
1. Open an ***incognito window*** and log into YouTube.
1. Open [https://youtube.com/robots.txt](https://youtube.com/robots.txt) in a new incognito tab and ***close all other incognito YouTube tabs***.
   - Open [https://www.tiktok.com/robots.txt](https://www.tiktok.com/robots.txt) instead to export TikTok cookies.
1. Click on the extension's icon in the top right, click on "Export As", and save as `cookies.txt`. Then ***close all incognito windows*** (so the cookies will never rotate).
1. Pass the cookies to yt-dlp using `--cookies "PATHTOCOOKIES"`.
   - For example, if you've saved the cookies file to your Downloads folder on Windows:
     ```shell
     yt-dlp --cookies "%USERPROFILE%\Downloads\cookies.txt" "URL"
     ```

**CAUTION:** Overdownloading with your YouTube account may result in YouTube being [unplayable](https://github.com/yt-dlp/yt-dlp/issues/10085) with that account.

</details>


<details>
<summary>

### How to manually export cookies for all other sites

</summary>

1. Install "Get cookies.txt LOCALLY" ([Chrome](https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc), [Firefox](https://addons.mozilla.org/en-US/firefox/addon/get-cookies-txt-locally/)).
1. Go to the website and ensure you're logged in.
1. Click on the extension icon in the top right, click on "Export As", and save them as `cookies.txt`.
1. Pass the cookies to yt-dlp using `--cookies "PATHTOCOOKIES"`.
   - For example, if you've saved the cookies file to your Downloads folder on Windows:
     ```shell
     yt-dlp --cookies "%USERPROFILE%\Downloads\cookies.txt" "URL"
     ```

</details>

---

</details>



<details>
<summary>

## How to download subtitles

</summary>

```shell
yt-dlp --embed-subs "URL"
```

This will download English subtitles and embed them into the video file.

To write subtitle files to your disk instead:

```shell
yt-dlp --write-subs "URL"
```

You can embed and write subs together:

```shell
yt-dlp --write-subs --embed-subs "URL"
```


<details>
<summary>

### How to embed user-uploaded subtitles in specific language(s)

</summary>

```shell
yt-dlp --embed-subs --sub-langs LANGUAGECODE "URL"
```

Replace `LANGUAGECODE` with the [ISO 639 two-character language code](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes)(s) (Set 1). For example, `yt-dlp --embed-subs --sub-langs en,es "URL"` will embed English and Spanish subtitles.

**Tip:** To view the entire list of downloadable subtitles' language codes, execute:

```shell
yt-dlp --list-subs "URL"
```

</details>


<details>
<summary>

### How to embed user-uploaded subtitles in all available languages

</summary>

```shell
yt-dlp --embed-subs --sub-langs all "URL"
```

Use `-` before a language code to exclude language(s). For example:

```shell
yt-dlp --embed-subs --sub-langs all,-live_chat "URL"
```

This will to embed all manual subtitles, except for YouTube's live chat replay, into the video file.

</details>


<details>
<summary>

### How to embed user-uploaded subtitles in all variants of a language

</summary>

```shell
yt-dlp --embed-subs --sub-langs "BASICLANGUAGECODE.*" "URL"
```

For example:

```
yt-dlp --embed-subs --sub-langs "en.*" "URL"
```

This will embed all the English variants' subtitles (e.g. `en`, `en-US`, `en-GB`, etc.) using regex into the video file.

</details>


<details>
<summary>

### How to download auto-generated/auto-translated subtitles

</summary>

```shell
yt-dlp --write-auto-subs "URL"
```

This will download English auto-generated subtitles; if these aren't available, English auto-translated subtitles will be downloaded instead. You can use `--sub-langs ".*orig"` to only download auto-generated subtitles.

You can use this option with `--embed-subs` to embed the auto-generated subtitles into the video file.

**NOTE:** On YouTube, auto-translated subtitles are highly restricted, likely due to AI-scrapers mass downloading. You may encounter HTTP 429 errors despite using `-t sleep` or other sleep-related parameters. See [https://github.com/yt-dlp/yt-dlp/issues/13831](https://github.com/yt-dlp/yt-dlp/issues/13831) for more information.

</details>

---

</details>



<details>
<summary>

## How to download different audio languages

</summary>

```shell
yt-dlp -f bv+ba[language=LANGUAGECODE]/b[language=LANGUAGECODE] --embed-metadata "URL"
```

Replace `LANGUAGECODE` with the [ISO 639 two-character language code](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) (Set 1). For example, `yt-dlp -f bv+ba[language=es]/b[language=es] --embed-metadata "URL"` will download Spanish audio.

`--embed-metadata` is required in order to ensure the appropriate language code is tagged with its respective audio track. Otherwise, all audio tracks may be incorrectly marked as English.


<details>
<summary>

### How to download more than 1 audio language

</summary>

```shell
yt-dlp -f bv+ba[language=LANGUAGECODE1]+ba[language=LANGUAGECODE2] --audio-multistreams --embed-metadata "URL".
```

For example, `yt-dlp -f bv+ba[language=es]+ba[language=en]+ba[language=fr] --audio-multistreams --embed-metadata "URL"` would download the video with Spanish, English, and French audio.

</details>


<details>
<summary>

### How to download all audio languages

</summary>

There is no universal way to download all the audio languages without downloading all formats (which may include lower-quality duplicates for sites like YouTube). However, on YouTube, this can be achieved with:

```shell
yt-dlp -f "bv+mergeall[format_id^=251][format_id!*=drc]" --audio-multistreams --embed-metadata "URL"
```

</details>

---

</details>



<details>
<summary>

## How to create a config

</summary>

If you want to always use certain parameters with yt-dlp without writing them every single time, create a configuration file. The file's stored parameters are automatically applied whenever you run yt-dlp. This is useful for setting a [default download directory](#how-to-download-files-to-a-specific-folder) or [defining a specific naming format for your downloads](#how-to-download-files-without-the-numbers-and-letters-video-id-at-the-end).

If you're on **Windows**:
   1. Open a `cmd` terminal.
   1. Execute:
      ```shell
      notepad "%USERPROFILE%\yt-dlp.conf"
      ```
   1. Notepad will open with a warning saying the file doesn't exist. Press "Yes" to create it.
   1. Add your parameters. Don't forget to save the file.

If you're on **macOS or Linux**:
   1. Create a file named `yt-dlp.conf` (not `yt-dlp.conf.txt`, but `yt-dlp.conf`) inside your home directory and add your parameters inside using a text editor. Don't forget to save the file.

If you're on **Android**:  
   1. Execute the following to create a `yt-dlp.conf` file in your home directory (where your terminal opens):
      ```shell
      nano yt-dlp.conf
      ```
   1. Add your parameters.
   1. Use `CTRL + O`, press enter, and use `CTRL + X`.

If you're on **iOS/iPadOS**:
   1. Execute:
      ```shell
      pico yt-dlp.conf
      ```
   1. Add your parameters.
   1. Press 🔼 above the keyboard and `x` to quit, then press `y` to confirm saving.
   1. Press `return` on your keyboard to confirm saving the file as `yt-dlp.conf`.

---

</details>



# Need Help?

Ensure you're on the [latest version](#how-to-update-yt-dlp) before asking for help. If you encounter any issues using yt-dlp despite being on the latest version, feel free to [open a GitHub issue](https://github.com/yt-dlp/yt-dlp/issues/new/choose). For quick assistance, join our [Discord server](https://discord.gg/H5MNcFW63r).
