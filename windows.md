# My Windows Web Development Setup

Table of Contents:

- Git and GitHub
- Windows Terminal
- Fancy your Terminal
- Visual Studio Code

If you run into any issues, update to the latest version of windows, including 'optional' updates. If you still have issues, contact me!


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
git config --global user.email typeyouremail@email.com
```
Double check the above information and change again if needed:
```powershell
git config --global --list
```

Generate a git ssh keygen to link to your github
```powershell
ssh-keygen -t ed25519 -C "<comment>"
```

It might ask you to enter which file to save the keygen in. DO NOT TYPE ANYTHING, just press enter, and it will generate a file for you.

It might ask you to make a password for the file, I personally leave it blank.

It should have generated a file `C:\Users\(your user)/.ssh/id_ed25519.pub`. Navigate to it, open it with notepad or something and copy the keygen from the generated file.
The keygen should be 1 line and begin with 'ssh-ed25519'
Paste the keygen into github: https://github.com/settings/ssh/new
Call the title whatever you want.

You can now test it by cloning a repository, go to any github repo and copy the SSH of the repo. (For example, this one is `git@github.com:So1ene/my-setup.git`)
Navigate to your desktop 
```powershell
cd ~/Desktop
```
And clone it there so you can easily delete it after. The first time you will have to confirm, type `yes`
```powershell
git clone <paste SSH KEY>
```
Here are some useful git commands if you ever feel stuck: https://dzone.com/articles/top-20-git-commands-with-examples


## Windows Terminal

Download and install Windows Terminal from the Microsoft Store

Open it then click on the arrow next to the tab and click on "Settings". Find the line that contains 'powershell.exe' and add `-noLogo` so that the line looks something like this: `"commandline": "powershell.exe -noLogo",`
You can also change the starting directory if you like. I set mine to my work folder so that it is much easier to use every day. `"startingDirectory": "C:/whatever/you/want"` If you're putting this at the end of the lines, add a comma to the line before it. Here's an example of what it can look like:
```
{
    // Make changes here to the powershell.exe profile.
    "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
    "name": "Windows PowerShell",
    "commandline": "powershell.exe -noLogo",
    "hidden": false,
    "startingDirectory": "C:/%UserProfile%/Documents"
},
```
Save the file and close.


## Fancy your Terminal

I use oh-my-posh! It's a windows version of oh-my-zsh, this will make your windows terminal look like linux zsh terminal!

Open windows terminal **as administator**.

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
```
Import-Module posh-git -DisableNameChecking
Import-Module oh-my-posh -DisableNameChecking
Set-Theme Robbyrussell
function home { cd ~ }
function desktop { cd ~/Desktop }
function documents { cd ~/Documents }
function wamp { cd C:\wamp64\www }
clear
```

You can also choose a different theme than Robbyrussell, but that is my favorite. 
Browse themes here: https://github.com/JanDeDobbeleer/oh-my-posh

I added functions to quick-travel between places in the command line, feel free to add your own. That way you can just type `desktop` and you will easily change directory to your desktop.


## Visual Studio Code

I use Visual Studio Code because it has a built-in terminal and lots of really amazing extensions.

1. Download [Visual Studio Code](https://code.visualstudio.com/download) 
2. Download and install useful extensions:
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Sublime Text Keymapping](https://marketplace.visualstudio.com/items?itemName=ms-vscode.sublime-keybindings)
- [Sass](https://marketplace.visualstudio.com/items?itemName=Syler.sass-indented)
- [CSS Peek](https://marketplace.visualstudio.com/items?itemName=pranaygp.vscode-css-peek)
- [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass)
- [Color Highlight](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)
- [CSS Class Name Completion](https://marketplace.visualstudio.com/items?itemName=Zignd.html-css-class-completion)
- [My favorite theme](https://marketplace.visualstudio.com/items?itemName=dustinsanders.an-old-hope-theme-vscode)
- [My 2nd favorite theme](https://marketplace.visualstudio.com/items?itemName=ryanolsonx.solarized)

Press `Ctrl ,` to go to settings, click extensions and click "Live sass compiler". Click 'edit in settings.json' and change the save path to `"savePath": "~/.."` This will save the css file outside of the sass folder, wherever you place it. 
We also want browser support, so look for `liveSassCompile.settings.autoprefix` and change it to this:
```
"liveSassCompile.settings.autoprefix": [
    "defaults",
    "> 1%",
    "last 2 versions"
],
```
Save the file and close it.
On the bottom of the window there is a 'Watch Sass' button, whenever you are coding in sass/scss you can compile it live by clicking on that button.

Press `Ctrl ,` to go to settings, type 'php' in the search bar and look for `PHP › Validate: Executable Path` and click'edit in settings.json'.
Add in the path to php.exe (mine is `C:/wamp64/bin/php/php7.4.9/php.exe`)

Press `Ctrl K` then `Ctrl T` and it will open a list of your installed themes. Cycle through them with the arrow keys and choose one that you like!

If you click on new terminal, a powershell terminal will appear with the same styling that you set up. Cool feature right? You can push to github directly from there! Also uing the 'output' tab for the live sass compiler is extremely useful to view errors.


You are now ready to code! You can click on the leftmost icons to travel between 'files', 'search', 'source control' (this is git! you can view your changes here), 'run' (you can run scripts etc, never used it personally), and 'extensions'.
