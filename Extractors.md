# YouTube

> [!IMPORTANT]
> YouTube is gradually enforcing the use of a "PO Token" to be able to download videos. Due to the nature of these tokens, yt-dlp cannot generate them and they must be provided externally.
> 
> By default, yt-dlp will attempt to download videos using clients that do not currently require a PO Token. However, some formats and features may not be available without the token(s).
> 
> At this time, it is **recommended** to use provide a PO Token to use with the `web` client. Refer to the [PO Token Guide](https://github.com/yt-dlp/yt-dlp/wiki/PO-Token-Guide) on how to set up yt-dlp for this.

## Exporting YouTube cookies

> [!CAUTION]
> By using your account with yt-dlp, you run the risk of it being banned (temporarily or permanently).
> Be mindful with the request rate and amount of downloads you make with an account. Use it only when necessary, or consider using a throwaway account.

> [!NOTE]
> This is only necessary for content that requires an account to access, such as private playlists, age-restricted videos and members-only content.

If you are unfamiliar with the basics of exporting cookies and passing them to yt-dlp, then first see [How do I pass cookies to yt-dlp?](https://github.com/yt-dlp/yt-dlp/wiki/FAQ#how-do-i-pass-cookies-to-yt-dlp)

YouTube rotates account cookies frequently on open YouTube browser tabs as a security measure.
To export cookies that will remain working with yt-dlp, you will need to export cookies in such a way that they are never rotated. 

One way to do this is through a private browsing/incognito window:
1. Open a new private browsing/incognito window and log into YouTube
2. Open a new tab and **close the YouTube tab**
3. Export `youtube.com` cookies from the browser then **close the private browsing/incognito window** so the session is never opened in the browser again.


## Passing Visitor Data without cookies

In some cases, you may not want to use cookies and instead pass Visitor Data to use in Innertube API requests. 

> [!WARNING]
> This method is **not recommended** for most cases. It requires skipping webpage requests so that the `VISITOR_INFO1_LIVE` cookie does not interfere. This results in more requests needing to be sent as well as less stable extraction.

You can do this with:

    --extractor-args "youtubetab:skip=webpage" --extractor-args "youtube:player_skip=webpage,configs;visitor_data=VISITOR_DATA_VALUE_HERE"

## Common YouTube Errors

#### `This content isn't available, try again later`

This error is caused by the YouTube session (guest or account) hitting the YouTube video request rate limit. With the default yt-dlp settings, the session rate limit is ~300 videos/hour. 
Note if using account cookies, the limit includes videos watched in the browser with that account.

It is recommended to add a delay of around 5-10 seconds between downloads with `-t sleep` or [with the sleep options](https://github.com/yt-dlp/yt-dlp#workarounds).

Other options include:
- using only `web` client (`--extractor-args "youtube:player-client=web"`) which will increase the rate limit to a maximum of ~1000 videos/hour. Note that this client requires a [PO Token](https://github.com/yt-dlp/yt-dlp/wiki/PO-Token-Guide) to get working formats.
- splitting up downloads into multiple sessions (i.e. multiple yt-dlp processes). If you are not using an account, yt-dlp creates a temporary guest session to download videos. It lasts for the lifetime of the yt-dlp process (or `YoutubeDL` instance for API users) if you are not persisting this session with cookies.

## PO Token Guide

[This section has been moved to a dedicated page](https://github.com/yt-dlp/yt-dlp/wiki/PO-Token-Guide)

## Logging in with OAuth

> [!CAUTION]
> Due to new restrictions enacted by YouTube, logging in with OAuth no longer works with yt-dlp. [You should use cookies instead.](#exporting-youtube-cookies)
