#New Mac Provision
For OSX 10.10.2 Yosimite

This repository containst the steps, scripts, and files necessary to set up and provision a new mac computer to my personal specifications.

###Overview
The default OSX install lacks many key binary utitlities and is rather clunky with many unecessary settings. Additionally, installing software can be a real time consuming process, and wrangling all those installations is a real chore.

##References
Much of this guide is based on Lapwing Lab's guide for setting up you mac. It can be found at http://lapwinglabs.com/blog/hacker-guide-to-setting-up-your-mac.

###1. Get Homebrew
```bash
# Check for Homebrew,
# Install if we don't have it
if test ! $(which brew); then
  echo "Installing homebrew..."
  ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
fi

# Update homebrew recipes
brew update
```

###2. Update Unix Tools
```bash
# Install GNU core utilities (those that come with OS X are outdated)
brew install coreutils

# Install GNU `find`, `locate`, `updatedb`, and `xargs`, g-prefixed
brew install findutils

# Install Bash 4
brew install bash

# Install more recent versions of some OS X tools
brew tap homebrew/dupes
brew install homebrew/dupes/grep
```

###3.Update Your Path
```bash
$PATH=$(brew --prefix coreutils)/libexec/gnubin:$PATH
```

###4. Install Binaries with Homebrew
```bash
binaries=(
  wget
  ack
  imagemagick
  python
  mysql
  trash
  node
  nodebrew
  tree
  git
  hubflow
  cask
  macvim
  archey
)

echo "installing binaries..."
brew install ${binaries[@]}
```
Once They have installed with their dependecies, run:
```bash
brew cleanup
```


