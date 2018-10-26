#New Mac Provision
For OSX 10.13.X High Sierra

This repository contains the steps, scripts, and files necessary to set up and provision a new mac computer to my personal specifications.

##Overview
The default OSX install lacks many key binary utils and is rather clunky with many unnecesary settings. Additionally, installing software can be a real time consuming process, and wrangling all those installations is a real chore.

##References
Much of this guide is based on Lapwing Lab's guide for setting up you mac. It can be found at http://lapwinglabs.com/blog/hacker-guide-to-setting-up-your-mac.

##1. Get Homebrew
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

##2. Update Unix Tools
```bash
# Install GNU core utilities (those that come with OS X are outdated)
brew install coreutils

# Install GNU `find`, `locate`, `updatedb`, and `xargs`, g-prefixed
brew install findutils

# Install Bash 4
brew install bash
```

##3. Update Your Path
```bash
PATH=$(brew --prefix coreutils)/libexec/gnubin:$PATH
```

##4. Install Binaries with Homebrew
```bash
binaries=(
  ack
  freetype
  go
  jq
  libmpc
  mono
  redis
  wxmac
  adns
  gcc
  grafana
  mpfr
  p11-kit
  xz
  awscli
  gdbm
  htop
  libtasn1
  mysql
  pcre2
  scons
  zsh-syntax-highlighting
  boost
  gettext
  icu4c
  libffi
  libtiff
  nettle
  pinentry
  sqlite
  ckan
  git
  imagemagick
  libgcrypt
  libtool
  npth
  postgresql
  terraform
  coreutils
  gmp
  influxdb
  libgpg-error
  libunistring
  nvm
  python
  tmux
  erlang
  elixir
  gnupg
  isl
  libidn2
  libusb
  oniguruma
  python3
  watch
  gnutls
  jpeg
  libksba
  mongodb@3.4
  openssl
  readline
  wget
)

echo "installing binaries..."
brew install ${binaries[@]}
```
Once They have installed with their dependecies, run:
```bash
brew cleanup
```
##5. Installing Applications with Homebrew Cask

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
  atom
  alfred
  adobe-creative-cloud
  appcleaner
  burn
  codekit
  dropbox
  evernote
  firefox
  fluid
  google-chrome
  google-drive
  hipchat
  invisionsync
  iterm2
  keyboardcleantool
  macvim
  minecraft
  quicklook-json
  sketch
  sketchup
  sketch-toolbox
  skype
  slack
  spotify
  steam
  tower
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
##6. Installing Other Apps
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

##7. Install Fonts
There are so many Fonts....
####Homebrew Fonts
A full list of of homebrew fonts is found at https://github.com/caskroom/homebrew-fonts/tree/master/Casks

You can also search for fonts:
```bash
brew cask search /font-*FONTNAME*
```
First, tap the font cask:
```bash
brew tap caskroom/fonts
```
Then install all the fonts:
```bash
# fonts
fonts=(
  font-m-plus
  font-clear-sans
  font-roboto
)

# install fonts
echo "installing fonts..."
brew cask install ${fonts[@]}
```
##8. Upgrade to ZSH
Time to go Pro:
```bash
$ curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```
##9. Restoring App Settings with Mackup
First, Open Dropbox and sign in.

Next, install Mackup with pip:
```bash
pip install mackup
```
Once installed, run:
```bash
mackup restore
```


