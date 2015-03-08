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

###3. Update Your Path
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
  archey
)

echo "installing binaries..."
brew install ${binaries[@]}
```
Once They have installed with their dependecies, run:
```bash
brew cleanup
```
###5. Installing Applications with Homebrew Cask

First, get the caskroom:
```bash
brew install caskroom/cask/brew-cask
```
Then enable app versions:
```bash
brew tap caskroom/versions
```
Then install all the apps!
```bash
# Apps
apps=(
  1password
  alfred
  adobe-creative-cloud
  appcleaner
  burn
  codekit
  dropbox
  evernote
  firefox
  flash
  fluid
  flux
  google-chrome
  google-drive
  hipchat
  invisionsync
  iterm2
  keyboardcleantool
  macvim
  mindnode-pro
  minecraft
  origin
  phpstorm
  quicklook-json
  sketchup
  sketch-toolbox
  skype
  slack
  spotify
  steam
  sublime-text3
  teleport
  tower
  transmission
  tunnelblick
  vagrant
  virtualbox
)

# Install apps to /Applications
# Default is: /Users/$user/Applications
echo "installing apps..."
brew cask install --appdir="/Applications" ${apps[@]}
```

Homebrew symlinks apps by default, so to use alfred with your homebrew apps, you will need to run:
```bash
brew cask alfred link
```
Don't foget to brew doctor when you're done installing!
```bash
brew doctor
```
###6. Installing Other Apps
Thanks to the Mac App Store & Adobe, not all apps can be installed via homebrew.
####Launch The Mac App Store:
Sign in with you Apple ID to install
+ xcode
+ airmail
+ screenflow 5
+ better snap tool
+ pages
+ numbers
+ keynote
+ sketch 3
+ twitter
+ sip
+ clear

####Launch Creative Cloud:
Sign In with your Adobe ID to install
* Photoshop
* Illustrator
* Media Encoder
* Acrobat Pro
* Premeire
* Lightroom
* Fonts From Typekit
*Creative Cloud Files

####Download Avocode:
https://manager.avocode.com/downloads/
-Get Avocode for MAc
-Get The Photoshop Plugin
-Get The Sketch Plugin

####Get InvisionApp Liveshare:
http://www.invisionapp.com/lsps-download

####Get Steam Games:
Sign In with Steam ID and install
- Hearts of Iron 3
- Kerbal Space Program
- Tabletop Simulator

####Get Origin Games:
Sign In with Origin ID and install
- Sim City

####Get Blizard Games:
Sign In with Blizzard ID and install
- Diablo III
- Starcraft II
