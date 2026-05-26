# yt-dlp

| | |
|---|---|
| **Status** | Maintained |
| **First release** | 2021-01-07 |
| **Language** | [Python](https://python.org) |
| **Developers** | [yt-dlp maintainers](https://github.com/orgs/yt-dlp/people) |
| **Website** | [github.com/yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) |

**yt-dlp** is a [command-line](https://en.wikipedia.org/wiki/Command-line_interface) audio/video downloader that supports [thousands of sites](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md) including [YouTube](https://youtube.com). It is a fork of [youtube-dl](https://github.com/ytdl-org/youtube-dl)[^1], originally forked via [youtube-dlc](https://github.com/yt-dlc/youtube-dlc). It uses [calendar versioning](https://calver.org/), so a release tag like `2026.03.17` is literally the date of that release. It is released under [The Unlicense](https://unlicense.org/), a public-domain dedication.

[^1]: yt-dlp contributors. "yt-dlp github page". github.com/yt-dlp/yt-dlp. Retrieved 2026-05-24.

---

## History

### youtube-dl

[youtube-dl](https://github.com/ytdl-org/youtube-dl) was written by Ricardo García in August 2006 and became the de facto standard tool for video archival, eventually supporting over 1,000 websites. Maintainership changed hands several times — from García to Philipp Hagemeister, then to dstftw, and finally to dirkf in 2021. By 2020 the project had slowed significantly, with pull requests accumulating unmerged for months and YouTube compatibility fixes arriving weeks late.

In October 2020, the RIAA issued a DMCA takedown notice to GitHub, arguing that youtube-dl circumvented YouTube's rolling cipher (a form of DRM) under Section 1201 of US copyright law. GitHub initially complied and removed the repository. After intervention from the [EFF](https://www.eff.org/) and significant community backlash, GitHub restored the project in November 2020 and announced a $1 million legal defense fund for future similar situations. Despite reinstatement, development on youtube-dl did not recover meaningfully.

### youtube-dlc

In mid-2020, while youtube-dl was still alive but slow, a GitHub user named `blackjack4494` forked it as [youtube-dlc](https://github.com/yt-dlc/youtube-dlc) (the "c" standing for "community"). The backlog of unmerged PRs was cleared within days. However, youtube-dlc itself went semi-inactive by late 2020, as projects led by a single maintainer are fragile by nature.

### yt-dlp

yt-dlp was created on October 26, 2020 — three days into the RIAA takedown of youtube-dl — as a re-fork of youtube-dlc. Its name reflects its original lead maintainer, `pukkandan`. By January 2021, it had absorbed youtube-dlc's contributor base and become the dominant fork of youtube-dl, focused on features, rapid fixes, and a multi-maintainer governance model designed to avoid the single-point-of-failure problems of its predecessors.

yt-dlp was included in Ubuntu starting with the 22.04 release. Debian 12.0 removed youtube-dl entirely, replacing it with an empty package that depends on yt-dlp.

---

## Maintainers

yt-dlp is governed by the [yt-dlp GitHub organization](https://github.com/orgs/yt-dlp/people) under a collective maintainer model rather than a single lead. Current and past core maintainers include:

| Handle | Role |
|---|---|
| `pukkandan` | Original creator and owner; drove the early feature surge |
| `bashonly` | Core maintainer; major contributor to YouTube extractor fixes and infrastructure |
| `coletdjnz` | Core maintainer; deep YouTube Innertube client work |
| `Grub4K` | Core maintainer |
| `seproDev` | Core maintainer; active across many extractors |
| `shirt-dev` | Maintainer |
| `Ashish0804` | Maintainer |
| `dirkf` | Contributor; also current maintainer of upstream youtube-dl |

The official contact for the maintainer team is [maintainers@yt-dlp.org](mailto:maintainers@yt-dlp.org).

---

## Differences from youtube-dl

yt-dlp diverges from youtube-dl in several significant ways.

### Speed of fixes

yt-dlp ships extractor fixes within hours of a YouTube breakage; youtube-dl can take weeks. This is the most practically important difference for day-to-day use.

A full list of options can be found by running `yt-dlp --help` or in the [official README](https://github.com/yt-dlp/yt-dlp#usage-and-options).

---

## See also

- [youtube-dl](https://github.com/ytdl-org/youtube-dl) — the original project yt-dlp is forked from
- [FFmpeg](https://ffmpeg.org/) — used by yt-dlp for post-processing
- [SponsorBlock](https://sponsor.ajay.app/) — community-driven sponsor segment database integrated into yt-dlp
