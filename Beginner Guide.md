# yt-dlp Beginners Guide
*A simple quick-start guide for new users of yt-dlp.*

This guide is designed for beginners who want to **install yt-dlp**, **download videos quickly**, and **use the most commonly needed options**, without reading the full manual.

**Helpful Wiki Pages for Beginners:**  
- [FAQ - Frequently Asked Questions](https://github.com/yt-dlp/yt-dlp-wiki/blob/master/FAQ.md)  
- [Installation Guide](https://github.com/yt-dlp/yt-dlp-wiki/blob/master/Installation.md)  

> This page is a quick-start guide only.
> For authoritative, complete documentation, please refer to the main [README](https://github.com/yt-dlp/yt-dlp/blob/master/README.md)

---
## 1. What is yt-dlp?

yt-dlp is a command-line downloader for **videos and audio** from **YouTube** and **thousands of sites**.

It features:
- Video and audio download from supported sites
- Subtitles  
- Playlist support  
- SponsorBlock integration  
- Format selection  
- Post-processing  
- Authentication support  

## 1. Installation (Beginner Friendly)

### **Windows**
1. Download:  
   https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe  
2. Run:
```bash
yt-dlp.exe "<URL>"
```

### **macOS**
```bash
brew install yt-dlp
```
Or:
```bash
pip3 install -U yt-dlp
```

### **Linux**
```bash
sudo apt install yt-dlp
```
Or:
```bash
pip3 install -U yt-dlp
```

### Linux package managers (apt, dnf, etc.) may be outdated
Most distro repositories (Ubuntu/Debian/Fedora) **update yt-dlp very slowly**, sometimes several months behind.
For the newest version, prefer:

```bash
curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o yt-dlp
chmod +x yt-dlp
sudo mv yt-dlp /usr/local/bin/
```

Or install with pip:

```bash
pip3 install -U yt-dlp
```

Arch Linux users (pacman) usually get up‑to‑date builds.

## 6 Common Download Scenarios (YouTube, Livestreams, Members-only, Subtitles, Quality)

### YouTube — Best Quality MP4
```bash
yt-dlp -S "res,ext:mp4" "<YouTube URL>"
```

### YouTube — Download Specific Resolution (e.g., 1080p)
```bash
yt-dlp -S "res:1080" "<YouTube URL>"
```

### YouTube — Download Only Audio (MP3)
```bash
yt-dlp -x --audio-format mp3 "<YouTube URL>"
```

### Livestream — Download Ongoing Stream
```bash
yt-dlp "<live URL>"
```

### ivestream — Start from Beginning (if supported)
```bash
yt-dlp --live-from-start "<live URL>"
```

### Members-only Video (Age-restricted / Private / Channel Membership)
> Requires browser cookies.

```bash
yt-dlp --cookies-from-browser chrome "<YouTube Members-only URL>"
```

If multiple profiles exist:

```bash
yt-dlp --cookies-from-browser "chrome:Profile 1" "<URL>"
```

### Download Subtitles Only
```bash
yt-dlp --skip-download --write-subs "<URL>"
```

### Download Auto-generated Subtitles
```bash
yt-dlp --write-auto-subs "<URL>"
```

### Download Subtitles in Specific Languages
```bash
yt-dlp --write-subs --sub-langs "en,ja" "<URL>"
```

### Highest Audio Quality Available
```bash
yt-dlp -f "ba" "<URL>"
```

### Force WebM / MP4 Only
WebM:
```bash
yt-dlp -S "ext:webm" "<URL>"
```

MP4:
```bash
yt-dlp -S "ext:mp4" "<URL>"
```

## Using Proxy / VPN (for users who cannot access YouTube)
Many users live in regions where YouTube cannot be accessed normally. 

yt-dlp supports proxies:

### Basic HTTP/HTTPS proxy
```bash
yt-dlp --proxy "http://127.0.0.1:8080" "<URL>"
```

### SOCKS proxy (common in VPN tools)
```bash
yt-dlp --proxy "socks5://127.0.0.1:1080" "<URL>"
```

### What is 127.0.0.1 and the port?
- `127.0.0.1` = *localhost*, meaning the VPN/proxy runs on your own computer.
- The port (`8080`, `1080`, etc.) depends on your VPN or proxy software.

### How to find the correct port?
Most VPN apps list their “local proxy port” in:
- settings → advanced → proxy
- or documentation
Examples:
- Clash/ClashX: 7890 (HTTP), 7891 (SOCKS)
- Shadowsocks: 1080 (SOCKS5)
- Some VPN apps: 8080

### Verify proxy works
```bash
yt-dlp --proxy "http://127.0.0.1:8080" --geo-bypass "<URL>"
```