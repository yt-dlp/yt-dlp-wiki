You can install yt-dlp either using one of the official releases, or with your favorite package manager

---

# Using the release binary

You can simply download the [correct binary file](https://github.com/yt-dlp/yt-dlp#release-files) for your OS

[![Windows](https://img.shields.io/badge/-Windows_x64-blue.svg?style=for-the-badge&logo=windows)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe)
[![Linux](https://img.shields.io/badge/-Linux/BSD-red.svg?style=for-the-badge&logo=linux)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp)
[![MacOS](https://img.shields.io/badge/-MacOS-lightblue.svg?style=for-the-badge&logo=apple)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos)
[![Other variants](https://img.shields.io/badge/-Other-grey.svg?style=for-the-badge)](#release-files)

In UNIX-like OSes (MacOS, Linux, BSD), you can also install the same in one of the following ways:

```bash
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

```bash
sudo wget https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -O /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

```bash
sudo aria2c https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp --dir /usr/local/bin -o yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

To update, run: 
```bash
sudo yt-dlp -U
```


# With [PIP](https://pypi.org/project/pip)

You can install the [PyPI package](https://pypi.org/project/yt-dlp) with:
```bash
python3 -m pip install -U yt-dlp
```

You can install without any of the optional dependencies using:
```bash
python3 -m pip install --no-deps -U yt-dlp
```

If you want to be on the cutting edge, you can also install the master branch with:
```bash
python3 -m pip install --force-reinstall https://github.com/yt-dlp/yt-dlp/archive/master.tar.gz
```

On some systems, you may need to use `py` or `python` instead of `python3`

To update, run:
```bash
python3 -m pip install -U yt-dlp
```


# Third-party package managers

**Note**: These packages are manitained by third-parties and may not be up-to-date. Please report any issues to the respective package maintainers

## Linux/MacOS

### [Homebrew](https://formulae.brew.sh/formula/yt-dlp)

macOS or Linux users that are using Homebrew can also install it by:
```bash
brew install yt-dlp
```

To update, run:
```bash
brew upgrade yt-dlp
```

### [AUR](https://aur.archlinux.org/packages/yt-dlp-git)

Arch Linux users can install it from the AUR:
```bash
pacman -Sy yt-dlp
```

To update, run:
```bash
pacman -Syu yt-dlp
```

### [APT](https://en.wikipedia.org/wiki/APT_(software))

You can download and install yt-dlp for Ubuntu and other related Debian-based distributions by adding the [stable PPA](https://launchpad.net/~yt-dlp/+archive/ubuntu/stable)
```
sudo add-apt-repository ppa:yt-dlp/stable
sudo apt update
sudo apt install yt-dlp
```

If you wish to use pre-compiled bleeding edge daily snapshot packages, use the [unstable PPA](https://code.launchpad.net/~yt-dlp/+archive/ubuntu/unstable) instead:
```
sudo add-apt-repository ppa:yt-dlp/unstable
sudo apt update
sudo apt install yt-dlp
```

Your system's package manager will now automatically download the correct dependencies and keep the package updated with the rest of your system whenever you run:
```bash
sudo apt update
sudo apt install yt-dlp
```

### [MacPorts](https://ports.macports.org/port/yt-dlp/)

You can install yt-dlp on macOS using MacPorts:
```bash
sudo port install yt-dlp
```

To update, run:
```bash
sudo port selfupdate
sudo port upgrade yt-dlp
```


## Windows

### [Scoop](https://scoop.sh)

```powershell
scoop install yt-dlp
```

To update, run:
```powershell
scoop update yt-dlp
```

### [Chocolatey](https://community.chocolatey.org/packages/yt-dlp)

```powershell
choco install yt-dlp
```

To update, run:
```powershell
choco upgrade yt-dlp
```

### [winget](https://docs.microsoft.com/en-us/windows/package-manager/winget/)

```powershell
winget install yt-dlp
```

To update, run:
```powershell
winget upgrade yt-dlp
```
