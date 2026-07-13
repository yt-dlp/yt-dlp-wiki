# YouTube

> [!IMPORTANT]
> YouTube is gradually enforcing the use of a "PO Token" to be able to download videos. Due to the nature of these tokens, yt-dlp cannot generate them and they must be provided externally.
> 
> By default, yt-dlp will attempt to download videos using clients that do not currently require a PO Token. However, some formats and features may not be available without the token(s).
> 
> At this time, if you are having issues with the default clients, it is suggested to use the `mweb` client with a PO Token. Refer to the [PO Token Guide](https://github.com/yt-dlp/yt-dlp/wiki/PO-Token-Guide) on how to set up yt-dlp for this.

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

#### `Video unavailable. This content isn't available`
This is a slightly more severe variant of the previous error, and is displayed when the YouTube (googlevideo) CDN returns an HTTP status 403 (Forbidden) to your YouTube client after attempting to load a video. This error is triggered in response to a policy violation, such as exceeding the YouTube video request rate limit, or the API request rate limit.

If **cookies** were in use when the error was triggered, this violation will be associated with the constituent YouTube account. Attempting to watch any video content using the affected account will trigger this error, regardless of the device, IP address, or location.

YouTube has acknowledged this error as being an '_enforcement_' of the YouTube Terms of Service, or in effect, a temporary ban. User reports suggest these bans may last anywhere from a few minutes, to hours, days, and in some cases, even months. The median duration of user reported bans is typically around a week.

There is significant discussion regarding this error ([reddit thread](https://www.reddit.com/r/youtube/comments/1f4n18h/video_unavailable_this_content_isnt_available/), [google forum](https://support.google.com/youtube/thread/294302773/video-unavailable-this-content-isn-t-available-cannot-watch-anything-on-pc-browsers)), with much speculation into potential workarounds of varying legitimacy. Users have observed that the error does not occur when logged in to other YouTube channel accounts (even within the same Google account), as well as when logged out. There is also some speculation that creating a support request asking for the ban to be lifted may yield some success, though this has not been conclusively proven.

The recommendations for preventing this error are the same, particularly the use of a 5-10 second delay between downloads with `-t sleep` or [with the sleep options](https://github.com/yt-dlp/yt-dlp#workarounds). Furthermore, using cookies should be avoided unless absolutely necessary, such as when a 'Liked Videos' or 'Favorites' playlist needs to be downloaded. For other playlists, changing the playlist visibility to 'unlisted' and downloading as a guest is the safer alternative to reduce the risk of the above errors / bans.

## PO Token Guide

[This section has been moved to a dedicated page](https://github.com/yt-dlp/yt-dlp/wiki/PO-Token-Guide)

## Logging in with OAuth

> [!CAUTION]
> Due to new restrictions enacted by YouTube, logging in with OAuth no longer works with yt-dlp. [You should use cookies instead.](#exporting-youtube-cookies)
