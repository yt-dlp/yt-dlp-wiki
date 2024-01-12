### [How to use plugins?](https://github.com/yt-dlp/yt-dlp#plugins)

### Extractor

- [YouTube Agegate Bypass](https://github.com/pukkandan/yt-dlp-YTAgeGateBypass) by [pukkandan](https://github.com/pukkandan)
    - Bypasses YouTube age-gate using [account proxy](https://youtube-proxy.zerody.one) by [zerodytrash](https://github.com/zerodytrash)
- [YouTube nsig Proxy](https://github.com/pukkandan/yt-dlp-YTNSigProxy) by [pukkandan](https://github.com/pukkandan)
    - Uses an online solver for decrypting YouTube nsig (based on [nparams/decrypt](https://github.com/Lesmiscore/bookish-octo-barnacle/blob/master/api/youtube/nparams/decrypt.js) by [Lesmiscore](https://github.com/Lesmiscore))
- [YouTube nsig Deno](https://github.com/bashonly/yt-dlp-YTNSigDeno) by cute-sakura
    - Uses [Deno](https://deno.land) for decrypting YouTube nsig
- [TTUser](https://github.com/bashonly/yt-dlp-TTUser) by [bashonly](https://github.com/bashonly/yt-dlp-TTUser) and [redraskal](https://github.com/redraskal)
    - Uses [playwright](https://playwright.dev) to download all videos posted by a TikTok user

### Postprocessor

- [Return Youtube Dislikes](https://github.com/pukkandan/yt-dlp-returnyoutubedislike) by [pukkandan](https://github.com/pukkandan)
    - Add dislike count from [returnyoutubedislike](https://returnyoutubedislike.com) to Youtube video metadata
- [srt fixer](https://github.com/bindestriche/srt_fix) by [bindestriche](https://github.com/bindestriche)
    - Fix [duplicate lines](https://github.com/yt-dlp/yt-dlp/issues/1734) in Youtube's `--auto-subs` when converted to `srt`
- [FixupMtime](https://github.com/bradenhilton/yt-dlp-FixupMtime) by [bradenhilton](https://github.com/bradenhilton)
    - Sets the mtime of all files to a given datetime value by key
- [yt-dlp-replaygain](https://github.com/Eboreg/yt-dlp-replaygain) by [Eboreg](https://github.com/Eboreg)
    - Applies track and (optionally) album replaygain to downloaded audio playlists or songs
- [yt-dlp-dearrow](https://github.com/QuantumWarpCode/yt-dlp-dearrow) by [QuantumWarpCode](https://github.com/QuantumWarpCode)
    - Applies DeArrow community titles to YouTube content

### Other

- [yt-dlp-ChromeCookieUnlock](https://github.com/seproDev/yt-dlp-ChromeCookieUnlock) by [seproDev](https://github.com/seproDev) and [csm10495](https://github.com/csm10495)
    - Unlocks the cookie database for chromium based browsers
- [yt-dont-lock-p](https://github.com/Grub4K/yt-dont-lock-p) by [Grub4K](https://github.com/Grub4K)
    - Apply a system wake lock during yt-dlp execution

Extensions that don't use the official plugin system

- [Plugin manager](https://github.com/flashdagger/ytdlp-plugins) by [flashdagger](https://github.com/flashdagger)
    - Extends the possibilities of yt-dlp by allowing to install new extractors from python packages
- [dl-plus](https://github.com/un-def/dl-plus) by [un-def](https://github.com/un-def)
    - A youtube-dl/yt-dlp extension with pluggable extractors
    
### [More](https://github.com/topics/yt-dlp-plugins)
