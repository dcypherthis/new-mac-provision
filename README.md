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
```
