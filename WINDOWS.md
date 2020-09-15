# Windows setup

Table of Contents:

- Prerequisites
- Visual Studio Code
- Git and GitHub
- Windows Terminal
- Fancy your Terminal


## Prerequisites

Windows 10, version 2004 or higher. You will need to check that your computer has all the latest updates. This includes 'optional' updates. Keep checking after updating until it says that you have no more updates left to install.


## Visual Studio Code

I use Visual Studio Code because it has a built-in terminal and lots of really amazing extensions.

1. Download [Visual Studio Code](https://code.visualstudio.com/download) 
2. Download and install useful extensions:
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Sublime Text Keymapping](https://marketplace.visualstudio.com/items?itemName=ms-vscode.sublime-keybindings)
- [Sass](https://marketplace.visualstudio.com/items?itemName=Syler.sass-indented)
- [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass)
- [My favorite theme](https://marketplace.visualstudio.com/items?itemName=dustinsanders.an-old-hope-theme-vscode)
- [My 2nd favorite theme](https://marketplace.visualstudio.com/items?itemName=ryanolsonx.solarized)


## Git and GitHub

Download and install git bash for windows: https://gitforwindows.org/
I personally keep all the default settings, except I uncheck 'Git GUI' because I never use it, I only use git via the command line.

Run Powershell **as administrator**, type the following commands.

Check you have git and OpenSHH for windows correctly installed:
```powershell
git --version
ssh -V
```

Configure your git information:
(Change 'Firstname' and 'Lastname' to your name)
```powershell
git config --global user.name "Firstname Lastname"
```
(Change to your email)
```powershell
git config --global user.email solene.duprat@gmail.com
```
Double check the above information and change again if needed:
```powershell
git config --global --list
```

Generate a git ssh keygen to link to your github
```powershell
ssh-keygen -t ed25519 -C "<comment>"
```
Copy the keygen from the generated file 'id_ed25519.pub'
```powershell
cat ~/.ssh/id_ed25519.pub | clip
```
It should be 1 line and begin with 'ssh-ed25519'
Paste the keygen into github: https://github.com/settings/ssh/new
Call the title whatever you want.

You can now test it by cloning a repository, go to any github repo and copy the SSH key. 
```powershell
git clone <paste SSH KEY>
```


## Windows Terminal

Download and install Windows Terminal from the Microsoft Store

Open it then click on the arrow next to the tab and click on "Settings". Find the line that contains 'powershell.exe' and add `-noLogo` so that the line looks something like this: `"commandline": "powershell.exe -noLogo",`
You can also change the starting directory if you like. I set mine to my work folder so that it is much easier. `"startingDirectory": "C:/whatever/you/want",`
Save the file and close.


## Fancy your Terminal

We will use oh-my-posh! It's a windows version of oh-my-zsh, this will make your windows terminal look like linux zsh terminal!

Open windows terminal as administator

Run these commands:
```powershell
Set-ExecutionPolicy RemoteSigned
```
```powershell
Install-Module posh-git -Scope CurrentUser
```
```powershell
Install-Module oh-my-posh -Scope CurrentUser
```
```powershell
Set-Prompt
```
```powershell
if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
```
```powershell
notepad $PROFILE
```

A notepad should open up. Add these lines to the notepad and save:
```Import-Module posh-git -DisableNameChecking
Import-Module oh-my-posh -DisableNameChecking
Set-Theme Robbyrussell```

You can also choose a different theme than Robbyrussell, but that is my favorite. 
Browse themes here: https://github.com/JanDeDobbeleer/oh-my-posh
