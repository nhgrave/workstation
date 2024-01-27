# Install WSL

This document is inspired by the @eltonlk project [doc](https://github.com/eltonlk/docs).

## Prerequisites

Search for "Turn Windows features on or off" and enable the following options. Afterward, restart your machine:

- Windows Subsystem for Linux
- Virtual Machine Platform
- Enable virtualization in the BIOS (if necessary)

## Installation

Execute the command below in the Windows PowerShell:

```bash
wsl --install -d ubuntu # You can change the name of the Linux distribution to your preference
```

Configure the username and password, and then update the distribution packages:

```bash
sudo apt update
sudo apt list --upgradable
sudo apt dist-upgrade
```

## Configure your terminal with the distribution profile

Open the terminal and access the settings. In the startup section, select the distribution as the default profile.

## Install Powerline Fonts for the Terminal

Search for Windows PowerShell and click on the option to run as administrator.

Execute the following commands:

```bash
Set-ExecutionPolicy Bypass
cd c:\
mkdir tmp -Force
cd tmp
wget https://github.com/powerline/fonts/archive/master.zip -outfile "fonts-master.zip"
Expand-Archive -Path fonts-master.zip -DestinationPath C:\tmp\
cd fonts-master
./install.ps1
cd ..
rm fonts-master*
Set-ExecutionPolicy Default
```

## Set Windows Terminal to Use a Powerline Font

In the Windows Terminal settings, set it to use the "Roboto Mono for Powerline" font.

You can directly set this in each profile under the Appearance > Font face (select to show all fonts),

or open the terminal configuration file and set the font for all profiles:

```json
"defaults": {
  ...
  "fontFace" : "Roboto Mono for Powerline"
}
```

## Set Windows Terminal to Start in the User's Folder

For the Linux distribution profile, replace `<DISTO_NAME>` and `<USERNAME>` with the appropriate values.

```json
"startingDirectory": "//wsl$/<DISTO_NAME>/home/<USERNAME>/"
```
