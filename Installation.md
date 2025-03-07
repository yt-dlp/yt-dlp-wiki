You can install yt-dlp either using one of the official releases, or with your favorite package manager

> If you are unfamiliar with the command line, you may use one of the many third-party GUIs available

---

# Installing the release binary

You can simply download the [correct binary file](https://github.com/yt-dlp/yt-dlp#release-files) for your OS

[![Windows](https://img.shields.io/badge/-Windows_x64-blue.svg?style=for-the-badge&logo=windows)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe)
[![Linux](https://img.shields.io/badge/-Linux/BSD-red.svg?style=for-the-badge&logo=linux)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp)
[![MacOS](https://img.shields.io/badge/-MacOS-lightblue.svg?style=for-the-badge&logo=apple)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos)
[![Other variants](https://img.shields.io/badge/-Other-grey.svg?style=for-the-badge)](https://github.com/yt-dlp/yt-dlp#release-files)

In UNIX-like OSes (MacOS, Linux, BSD), you can also install the application into a location in your `$PATH`, such as `~/.local/bin`, in one of the following ways:

```bash
curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o ~/.local/bin/yt-dlp
chmod a+rx ~/.local/bin/yt-dlp  # Make executable
```

```bash
wget https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -O ~/.local/bin/yt-dlp
chmod a+rx ~/.local/bin/yt-dlp  # Make executable
```

```bash
aria2c https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp --dir ~/.local/bin -o yt-dlp
chmod a+rx ~/.local/bin/yt-dlp  # Make executable
```

To update, run: 
```bash
yt-dlp -U
```

To use shell completion (autocomplete), look for the completion files in the [source tarball](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.tar.gz). It comes with bash, fish & zsh support.

# With [pip](https://pypi.org/project/pip)

You can install the [PyPI package](https://pypi.org/project/yt-dlp) with:
```bash
python3 -m pip install -U "yt-dlp[default]"
```

You can install without any of the optional dependencies using:
```bash
python3 -m pip install --no-deps -U yt-dlp
```
<a id="pip-nightly"></a>

You can also install the nightly version of yt-dlp with:
```bash
python3 -m pip install -U --pre "yt-dlp[default]"
```

<a id="pip-master"></a>

If you want to be on the bleeding edge, you can also install the master branch with:
```bash
python3 -m pip install -U pip hatchling wheel
python3 -m pip install --force-reinstall "yt-dlp[default] @ https://github.com/yt-dlp/yt-dlp/archive/master.tar.gz"
```

On some systems, you may need to use `py` or `python` instead of `python3`

To update, run:
```bash
python3 -m pip install -U "yt-dlp[default]"
```


# Third-party package managers

**Note**: These packages are maintained by third-parties and may not be up-to-date. Please report any issues to the respective package maintainers

<a href="https://repology.org/project/yt-dlp/versions">
    <img src="https://repology.org/badge/vertical-allrepos/yt-dlp.svg" alt="Packaging status" align="right">
</a>

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

### [pacman](https://archlinux.org/packages/extra/any/yt-dlp/)

Arch Linux users can install it from the official community repository:
```bash
sudo pacman -Syu yt-dlp
```

pacman will now automatically download the correct dependencies and keep the package up-to-date whenever you update your system with:
```bash
sudo pacman -Syu
```

### [APT](https://en.wikipedia.org/wiki/APT_(software))

You can download and install yt-dlp for recent Ubuntu and other related Debian-based distributions by adding [this PPA](https://launchpad.net/~tomtomtom/+archive/ubuntu/yt-dlp)
```bash
sudo add-apt-repository ppa:tomtomtom/yt-dlp    # Add ppa repo to apt
sudo apt update                                 # Update package list
sudo apt install yt-dlp                         # Install yt-dlp
```
Your system's package manager will now automatically download the correct dependencies and keep the package updated with the rest of your system whenever you run:
```bash
sudo apt update
sudo apt install yt-dlp
```

### [Snap](https://snapcraft.io/yt-dlp)

You can install yt-dlp on Linux using Snap:
```bash
sudo snap install --edge yt-dlp
```

To manually update, run:
```bash
sudo snap refresh --edge yt-dlp
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

### [Alpine Linux](https://alpinelinux.org/)

Make sure you're on the latest version (or edge) - older versions don't receive updates for community repo.

To install yt-dlp on Alpine Linux:
```sh
doas apk -U add yt-dlp
```
Or alternatively, without any optional dependencies:
```sh
doas apk -U add yt-dlp-core
```

yt-dlp should upgrade with your system. If you want to do that explicitly:
```sh
doas apk -U upgrade yt-dlp
```

To uninstall:
```sh
doas apk del yt-dlp
```

On [postmarketOS](https://postmarketos.org/) you might have to use `sudo` instead of `doas`.

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

## Android

You can use yt-dlp on Android using [Termux](https://termux.dev). Once Termux is installed, open it and run the following commands:
```bash
termux-setup-storage                 # Allow termux to download files into your phone's storage
pkg update && pkg upgrade            # Update all packages
pkg install python python-pip        # Install Python and pip
pip install -U "yt-dlp[default]"     # Install yt-dlp with default dependencies
pkg install ffmpeg                   # OPTIONAL: Install ffmpeg
```

To update, run:
```bash
pip install -U "yt-dlp[default]"
```
