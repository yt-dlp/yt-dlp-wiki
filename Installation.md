You can install yt-dlp either using one of the official releases, or with your favorite package manager

---

# Using the release binary

You can simply download the [correct binary file](https://github.com/yt-dlp/yt-dlp#release-files) for your OS

[![Windows](https://img.shields.io/badge/-Windows_x64-blue.svg?style=for-the-badge&logo=windows)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe)
[![Linux](https://img.shields.io/badge/-Linux/BSD-red.svg?style=for-the-badge&logo=linux)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp)
[![MacOS](https://img.shields.io/badge/-MacOS-lightblue.svg?style=for-the-badge&logo=apple)](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos)
[![Other variants](https://img.shields.io/badge/-Other-grey.svg?style=for-the-badge)](https://github.com/yt-dlp/yt-dlp#release-files)

In UNIX-like OSes (MacOS, Linux, BSD), you can also install the same in one of the following ways:

```bash
mkdir -p ~/bin
curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o ~/bin/yt-dlp
chmod a+rx ~/bin/yt-dlp  # Make executable
```

```bash
mkdir -p ~/bin
wget https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -O ~/bin/yt-dlp
chmod a+rx ~/bin/yt-dlp  # Make executable
```

```bash
mkdir -p ~/bin
aria2c https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp --dir ~/bin -o yt-dlp
chmod a+rx ~/bin/yt-dlp  # Make executable
```

If `~/bin` is not already in your path, you can add it
###### Linux,BSD
Edit your the appropriate file for your shell(i.e. `~/.bashrc`, `~/.zshrc`, etc) and add the following:
```bash
PATH=$PATH:~/bin
export PATH
```

###### MacOS
Create a file `/etc/path.d/80_bin` with the following contents
```text
~/bin
```

To update, run: 
```bash
yt-dlp -U
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

### [pacman](https://archlinux.org/packages/community/any/yt-dlp/)

Arch Linux users can install it from the official community repository:
```bash
sudo pacman -Syu yt-dlp
```

pacman will now automatically download the correct dependencies and keep the package up-to-date whenever you update your system with:
```bash
sudo pacman -Syu
```

### [APT](https://en.wikipedia.org/wiki/APT_(software))

You can download and install yt-dlp for Ubuntu and other related Debian-based distributions by adding the [stable PPA](https://launchpad.net/~yt-dlp/+archive/ubuntu/stable)
```bash
sudo add-apt-repository ppa:yt-dlp/stable    # Add ppa repo to apt
sudo apt update                              # Update package list
sudo apt install yt-dlp                      # Install yt-dlp
```

If you wish to use pre-compiled bleeding edge daily snapshot packages, use the [unstable PPA](https://code.launchpad.net/~yt-dlp/+archive/ubuntu/unstable) instead:
```bash
sudo add-apt-repository ppa:yt-dlp/unstable  # Add ppa repo to apt
sudo apt update                              # Update package list
sudo apt install yt-dlp                      # Install yt-dlp
```

Your system's package manager will now automatically download the correct dependencies and keep the package updated with the rest of your system whenever you run:
```bash
sudo apt update
sudo apt install yt-dlp
```
The [Debian package](https://salsa.debian.org/debian/yt-dlp) is upstream for the Ubuntu ppa.

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

## Android

You can use yt-dlp on Android using [Termux](https://termux.dev). Once Termux is installed, open it and run the following commands:
```bash
termux-setup-storage       # Allow termux to download files into your phone's storage
pkg update && pkg upgrade  # Update all packages
pkg install python         # Install python
pip install -U yt-dlp      # Install yt-dlp
pkg install ffmpeg         # OPTIONAL: Install ffmpeg
```

To update, run:
```bash
pip install -U yt-dlp
```
