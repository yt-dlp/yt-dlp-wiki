# YouTube

> [!IMPORTANT]
> YouTube is gradually enforcing the use of a "PO Token" to be able to download videos. Due to the nature of these tokens, yt-dlp cannot generate them and they must be provided externally.
> 
> By default, yt-dlp will attempt to download videos using clients that do not currently require a PO Token. However, some formats and features may not be available without the token(s).
> 
> At this time, if you are having issues with the default clients, it is suggested to use the `mweb` client with a PO Token. Refer to the [PO Token Guide](https://github.com/yt-dlp/yt-dlp/wiki/PO-Token-Guide) on how to set up yt-dlp for this.

## Clients information

| Client          | Cookies      | JS Runtime | PO tokens required for | SABR        | Notes                                                                                                                                                                                                                                                                                                                                                                                                            |
| --------------- | ------------ | ---------- | ---------------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `web`           | Supported    | Required   | GVS, Subs              | Only        |                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `web_safari`    | Supported    | Required   | GVS, Subs\*            | Supported   | HLS (`m3u8`) formats do not require PO tokens. However, these formats are limited to 1080p avc1/H.264 video and AAC audio. All other formats (`sabr`) require PO tokens. Only manually-uploaded, `vtt` subtitles are available for download without PO tokens - these subtitles are obtained from the HLS manifest. Auto-translated, auto-generated, and other subtitle formats (e.g. `srv3`) require PO tokens. |
| `web_embedded`  | Supported    | Required   |                        | Supported   | Only available for [embeddable videos](https://support.google.com/youtube/answer/6301625).                                                                                                                                                                                                                                                                                                                       |
| `web_music`     | Supported    | Required   | GVS                    | Supported   | Only available for videos present in https://music.youtube.com. No AV1 or 8K formats are available.                                                                                                                                                                                                                                                                                                              |
| `web_creator`   | Required     | Required   | GVS                    | Supported   | Can be used to bypass the account age-verification requirement for age-restricted videos, given you pass any account cookies.                                                                                                                                                                                                                                                                                    |
| `mweb`          | Supported    | Required   | GVS                    | Supported   | Has "low" and "ultralow" qualities for audio. Overdownloading or random A/B experiments may lead SABR-only formats. Does not have the 10MB throttling limitations other clients have; this is useful for quicker downloads using `--download-sections` or faster seeking within `mpv`'s yt-dlp integration.                                                                                                      |
| `tv`            | Required\*   | Required   |                        | Supported\* | Without account cookies, DRM-only formats are returned. Overdownloading or random A/B experiments may lead SABR-only formats. Note: You can also bypass the DRM-only formats _without_ signing in by using guest-session cookies aged for ~1+ days, e.g. `yt-dlp --cookies "guestcookies.txt" "YouTube video URL"` > wait ~1 day > download with `tv` client + aged cookies.                                     |
| `tv_downgraded` | Required\*   | Required   |                        | No          | Without account cookies, a "Sign in to confirm you're not a bot" error will appear, even if other clients are not hit with the bot check. Note: If other clients are usable, you can bypass the sign-in requirement by using guest-session cookies aged for ~1+ days, e.g. `yt-dlp --cookies "guestcookies.txt" "YouTube video URL"` > wait ~1 day > download with `tv_downgraded` client + aged cookies.        |
| `tv_simply`     | Unsuppoorted | Required   | GVS                    | Supported   |                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `android`       | Unsuppoorted | No         | GVS                    | Only        | There is no PO token plugin that allows PO token generation for this client.                                                                                                                                                                                                                                                                                                                                     |
| `android_vr`    | Unsuppoorted | No         |                        | No          | "Made for kids" videos are not available. Poor multi-audio language support.                                                                                                                                                                                                                                                                                                                                     |
| `ios`           | Unsuppoorted | No         | GVS                    | Supported   | There is no PO token plugin that allows PO token generation for this client.                                                                                                                                                                                                                                                                                                                                     |

GVS = Google Video Server (used to stream audio and video)

Note: PO tokens for GVS are not required for YouTube Premium subscribers.

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
2. In same window and same tab from step 1, navigate to `https://www.youtube.com/robots.txt` (this should be the **only** private/incognito browsing tab open)
3. Export `youtube.com` cookies from the browser, then **close the private browsing/incognito window** so that the session is never opened in the browser again.

> [!NOTE]
> Do **NOT** use the `--cookies COOKIEFILE --cookies-from-browser BROWSER` method (as described in the above FAQ link) to export your cookies to a cookiefile. This will export **all** of your regular browser cookies, but **not** the cookies from this private/incognito YouTube session. Instead, use one of the browser extensions recommended in the [FAQ](https://github.com/yt-dlp/yt-dlp/wiki/FAQ#how-do-i-pass-cookies-to-yt-dlp).


## Passing Visitor Data without cookies

In some cases, you may not want to use cookies and instead pass Visitor Data to use in Innertube API requests. 

> [!WARNING]
> This method is **not recommended** for most cases. It requires skipping webpage requests so that the `VISITOR_INFO1_LIVE` cookie does not interfere. This results in more requests needing to be sent as well as less stable extraction.

You can do this with:

    --extractor-args "youtubetab:skip=webpage" --extractor-args "youtube:player_skip=webpage,configs;visitor_data=VISITOR_DATA_VALUE_HERE"

## Common YouTube Errors

#### `This content isn't available, try again later`

This error is caused by your YouTube guest session or account exceeding the YouTube video request rate limit. 

It is recommended to add a delay of around 5-10 seconds between downloads with `-t sleep` or [with the sleep options](https://github.com/yt-dlp/yt-dlp#workarounds).

With the default yt-dlp settings, the rate limit for guest sessions is ~300 videos/hour (~1000 webpage/player requests per hour). For accounts, it is ~2000 videos/hour (~4000 webpage/player requests per hour).


## PO Token Guide

[This section has been moved to a dedicated page](https://github.com/yt-dlp/yt-dlp/wiki/PO-Token-Guide)

## Logging in with OAuth

> [!CAUTION]
> Due to new restrictions enacted by YouTube, logging in with OAuth no longer works with yt-dlp. [You should use cookies instead.](#exporting-youtube-cookies)
