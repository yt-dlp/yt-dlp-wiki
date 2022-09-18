### Known issues

See [this pinned issue](https://github.com/yt-dlp/yt-dlp/issues/3766) for a list of some important currently known issues and the [bugtracker](https://github.com/yt-dlp/yt-dlp/issues) for a full list of issues.


### The yt-dlp in my Package Manager is outdated/broken

Unfortunately, there is nothing we can do if your distribution serves an outdated/broken version. You should report this to the package maintainer or your distribution in their bugtracker or support forum.

As a last resort, you can also uninstall the version installed by your package manager and follow [our installation instructions](Installation) to install the latest version.


### Do I need any other programs?

yt-dlp works reasonably well on its own on most sites. However, some sites - most notably YouTube - serve higher quality formats as separate audio and video. You will need [ffmpeg](https://www.ffmpeg.org/) to download and merge such formats. yt-dlp also uses many other optional dependencies for additional features. See [Dependencies](
https://github.com/yt-dlp/yt-dlp#dependencies) for more information.


### I extracted a video URL, but it does not play on another machine / in my web browser

It depends a lot on the service. In many cases, requests for the video (to download/play it) must come from the same IP address and with the same cookies and/or HTTP headers. Use the `--cookies` option to write the required cookies into a file, and advise your downloader to read cookies from that file. Some sites also require a common user agent to be used; manually pass a desired User-Agent to yt-dlp with `--add-headers`. You should also look at any headers/options yt-dlp adds to the download with `--print http_headers`/`--print downloader_options`. Notably, YouTube throttles any request with an http chunk size of > 10MB.

Please bear in mind that some download protocols are **not** supported by browsers out of the box. If you wish to download such URLs without yt-dlp, your own downloader must support these.

If you want to play the video on a machine that is not running yt-dlp, you can relay the video content from the machine that runs yt-dlp. You can use `-o -` to let yt-dlp stream a video to stdout, or simply allow the player to download the files written by yt-dlp in turn. 


### Video URL contains an ampersand `&` and I'm getting some strange output `[1] 2839` or `'v' is not recognized as an internal or external command`

That's actually the output from your shell. Since ampersand is one of the special shell characters it's interpreted by the shell preventing you from passing the whole URL to yt-dlp. To disable your shell from interpreting the ampersands (or any other special characters) you have to either put the whole URL in quotes or escape them with a backslash (which approach will work depends on your shell).

For example if your URL is https://www.youtube.com/watch?t=4&v=BaW_jenozKc you should end up with following command:

```yt-dlp "https://www.youtube.com/watch?t=4&v=BaW_jenozKc"```

or

```yt-dlp https://www.youtube.com/watch?t=4\&v=BaW_jenozKc```

Similar quoting is needed for other options that contain special characters or spaces.


### Output template and Windows batch files

If you are using an output template inside a Windows batch file then you must escape plain percent characters (`%`) by doubling, so that `-o "%(title)s-%(id)s.%(ext)s"` should become `-o "%%(title)s-%%(id)s.%%(ext)s"`. However you should not touch `%`'s that are not plain characters, e.g. environment variables for expansion should stay intact: `-o "C:\%HOMEPATH%\Desktop\%%(title)s.%%(ext)s"`


### File name too long

Each OS and filesystem has a limit to the the length of a filename. If you are getting this error, then the filename you are trying to save has exceeded this limit. To fix this, use [output template](https://github.com/yt-dlp/yt-dlp#output-template) to set a smaller filename. The [Python string formatting operations](https://docs.python.org/3/library/stdtypes.html#printf-style-string-formatting) will be helpful here. For example, `%(uploader).30B - %(title).200B.%(ext)s` will shorten the uploader name to 30 bytes and the title to 200 bytes. If you want this for all of your downloads, put the option into your [configuration file](https://github.com/yt-dlp/yt-dlp#configuration).


### Downloading clips and cutting out Sponsor sections is inaccurate

Video files cannot be cut at exact timestamps without re-encoding. yt-dlp does not re-encode the video by default, even when cutting is required. You can use `--force-keyframes-at-cuts` to force re-encoding; however, this process is slow - there is no way around this.


### HTTP Error 429: Too Many Requests or 402: Payment Required

These two error codes indicate that the service is blocking your IP address because of overuse. Usually this is a soft block meaning that you can gain access again after solving CAPTCHA. Just open a browser and solve a CAPTCHA the service suggests you and after that [pass cookies](#how-do-i-pass-cookies-to-yt-dlp) to yt-dlp. Note that if your machine has multiple external IPs then you should also pass exactly the same IP you've used for solving CAPTCHA with [`--source-address`](https://github.com/yt-dlp/yt-dlp#network-options). Also you may need to pass a `User-Agent` HTTP header of your browser with [`--user-agent`](https://github.com/yt-dlp/yt-dlp#workarounds).

If this is not the case (no CAPTCHA suggested to solve by the service) then you can contact the service and ask them to unblock your IP address, or - if you have acquired a whitelisted IP address already - use the [`--proxy` or `--source-address` options](https://github.com/yt-dlp/yt-dlp#network-options) to select another IP address.


### On Windows, how should I set up ffmpeg and yt-dlp? Where should I put the exe files?

If you put yt-dlp and ffmpeg in the same directory that you're running the command from, it will work, but that's rather cumbersome.

To make a different directory work - either for ffmpeg, or for yt-dlp, or for both - simply create the directory (say, `C:\Users\<User name>\bin`), put all the executables directly in there, and then [set your PATH environment variable](https://www.java.com/en/download/help/path.xml) to include that directory.

From then on, after restarting your shell, you will be able to access both yt-dlp and ffmpeg (and yt-dlp will be able to find ffmpeg) by simply typing `yt-dlp` or `ffmpeg`, no matter what directory you're in.


### How do I put downloads into a specific folder?

Use the `-P "path/to/folder"` to specify a path and an `-o` to specify an [output template](https://github.com/yt-dlp/yt-dlp#output-template). If you want this for all of your downloads, put the option into your [configuration file](https://github.com/yt-dlp/yt-dlp#configuration).


### How do I download a video starting with a `-`?

Either prepend `https://www.youtube.com/watch?v=` or separate the ID from the options with `--`:

    yt-dlp -- -wNyEUrxzFU
    yt-dlp "https://www.youtube.com/watch?v=-wNyEUrxzFU"


### How do I pass cookies to yt-dlp?

Passing cookies to yt-dlp is a good way to workaround login when a particular extractor does not implement it explicitly. Another use case is working around [CAPTCHA](https://en.wikipedia.org/wiki/CAPTCHA) some websites require you to solve in particular cases in order to get access (e.g. YouTube, CloudFlare).

The easiest way to pass cookies is to let yt-dlp extract it from your browser (say, Chrome) using `--cookies-from-browser chrome`.

If you wish to manually pass cookies, use the `--cookies` option, for example `--cookies /path/to/cookies/file.txt`.

In order to extract cookies from browser use any conforming browser extension for exporting cookies. For example, [Get cookies.txt](https://chrome.google.com/webstore/detail/get-cookiestxt/bgaddhkoddajcdgocldbbfleckgcbcid/) (for Chrome) or [cookies.txt](https://addons.mozilla.org/en-US/firefox/addon/cookies-txt/) (for Firefox).

Note that the cookies file must be in Mozilla/Netscape format and the first line of the cookies file must be either `# HTTP Cookie File` or `# Netscape HTTP Cookie File`. Make sure you have correct [newline format](https://en.wikipedia.org/wiki/Newline) in the cookies file and convert newlines if necessary to correspond with your OS, namely `CRLF` (`\r\n`) for Windows and `LF` (`\n`) for Unix and Unix-like systems (Linux, macOS, etc.). `HTTP Error 400: Bad Request` when using `--cookies` is a good sign of invalid newline format.

### How do I stream directly to media player?

You will first need to tell yt-dlp to stream media to stdout with `-o -`, and also tell your media player to read from stdin (it must be capable of this for streaming) and then pipe former to latter. For example, streaming to [VLC](https://www.videolan.org/) can be achieved with:

    yt-dlp -o - "https://www.youtube.com/watch?v=BaW_jenozKcj" | vlc -
    
If you have ffmpeg, you may want to use `-o - --downloader ffmpeg -f "bv*+ba/b"` when streaming to stdout to get the best available quality.


### How do I download only new videos from a playlist?

Use download-archive feature. With this feature you should initially download the complete playlist with `--download-archive /path/to/download/archive/file.txt` that will record identifiers of all the videos in a special file. Each subsequent run with the same `--download-archive` will download only new videos and skip all videos that have been downloaded before. Note that only successful downloads are recorded in the file.

For example, at first,

    yt-dlp --download-archive archive.txt "https://www.youtube.com/playlist?list=PLwiyx1dc3P2JR9N8gQaQN_BCvlSlap7re"

will download the complete `PLwiyx1dc3P2JR9N8gQaQN_BCvlSlap7re` playlist and create a file `archive.txt`. Each subsequent run will only download new videos if any:

    yt-dlp --download-archive archive.txt "https://www.youtube.com/playlist?list=PLwiyx1dc3P2JR9N8gQaQN_BCvlSlap7re"


### How can I detect whether a given URL is supported by yt-dlp?

For one, have a look at the [list of supported sites](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md). Note that it can sometimes happen that the site changes its URL scheme (say, from https://example.com/video/1234567 to https://example.com/v/1234567) and yt-dlp reports an URL of a service in that list as unsupported. In that case, simply report a site-bug.

It is *not* possible to detect whether a URL is supported or not. That's because yt-dlp contains a generic extractor which matches **all** URLs. You may be tempted to disable the generic extractor, but the generic extractor not only allows users to extract videos from lots of websites that embed a video from another service, but may also be used to extract video from a service that it's hosting itself. Therefore, we don't recommend disabling it. However, if you still wish to, you can disable it using `--ies default,-generic`.

If you want to find out whether a given URL is supported, simply call yt-dlp with it. If you get no videos back, chances are the URL is either not referring to a video or unsupported. You can find out which by examining the output (if you run yt-dlp on the console) or catching an `UnsupportedError` exception if you run it from a Python program.


### Why do I need to go through that much red tape when filing bugs?

Despite the extensive [bug reporting instructions](https://github.com/yt-dlp/yt-dlp/blob/master/CONTRIBUTING.md#opening-an-issue), Many of the issue reports we get are useless, for instance because people used ancient versions, because of simple syntactic errors (not in yt-dlp but in general shell usage), because the problem was already reported multiple times before, because people did not actually read an error message, even if it said "please install ffmpeg", because people did not mention the URL they were trying to download and many more simple, easy-to-avoid problems, many of whom were totally unrelated to yt-dlp. So the issue template forces people to go through the red tape to make sure that they actually read the instructions and that they are not wasting our time.

yt-dlp is an open-source project manned by too few volunteers, so we'd rather spend time fixing bugs where we are certain none of those simple problems apply, and where we can be reasonably confident to be able to reproduce the issue without asking the reporter repeatedly. As such, the output of `yt-dlp -Uv <rest of your comamnd>` is really all that's required to file an issue. The issue template also guides you through some basic steps you can do, such as checking that your version of yt-dlp is current.


### How can I speed up work on my issue?

(Also known as: Help, my important issue not being solved!)

The yt-dlp core developer team is quite small. While we do our best to solve as many issues as possible, sometimes that can take quite a while. To speed up your issue, here's what you can do:

First of all, please do report the issue [at our issue tracker](https://github.com/yt-dlp/yt-dlp/issues?q=). That allows us to coordinate all efforts by users and developers, and serves as a unified point. Bug reports will not be accepted by any other communication channel.

Please make sure to read the [bug reporting instructions](https://github.com/yt-dlp/yt-dlp/blob/master/CONTRIBUTING.md#opening-an-issue). A lot of bug reports lack the necessary information. At the time of writing this, over 25% of all issues have been closed as invalid/duplicates. A lot of developer time is wasted triaging and answering such issues.

You are always welcome to take matters into your own hands and submit a pull request (or pay somebody else to do so). Make sure to read the [contributing guidelines](https://github.com/yt-dlp/yt-dlp/blob/master/CONTRIBUTING.md#developer-instructions) when you do.
