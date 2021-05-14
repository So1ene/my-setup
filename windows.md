# My Windows Web Development Setup


## Table of Contents:

- Git and GitHub
- Windows Terminal
- Fancy your Terminal
- Visual Studio Code

If you run into any issues, update to the latest version of windows, including 'optional' updates. If you still have issues, contact me!


## Git and GitHub

Download and install VS Code

Make sure you have a github account

Download and install git bash for windows: https://gitforwindows.org/ 
This will let you clone etc using SSH. 
I personally keep all the default settings, except I uncheck 'Git GUI' because I never use it, I only use git via the command line. You can keep it checked and use the GUI if you want. Set the IDE to VS Code

Run Powershell **as administrator**, type the following commands.


Check you have git and OpenSHH for windows correctly installed:
```powershell
git --version
ssh -V
```

Congratulations, you now have simple bash commands like `cd`, `ls`, `pwd`, `cat`, `find`...

Next, configure your git information. This is used by git to track who made what changes, etc.

Change 'Firstname' and 'Lastname' to your name:

```powershell
git config --global user.name "Firstname Lastname"
```
Change to the email of your github account:
```powershell
git config --global user.email typeyouremail@email.com
```
Double check the above information and change again if needed:
```powershell
git config --global --list
```

Generate a git ssh keygen to link to your github:

Replace "comment" with whatever you want (ie: "Work laptop")
```powershell
ssh-keygen -t ed25519 -C "comment"
```

It might ask you to enter which file to save the keygen in. DO NOT TYPE ANYTHING, just press enter, and it will generate a file for you.

It might also ask you to make a password for the file.

Afterwards it should have generated a file `C:/Users/%UserName%/.ssh/id_ed25519.pub`. Navigate to it, open it with notepad or something and copy the keygen from the generated file.
The keygen should be 1 line and begin with 'ssh-ed25519'
Paste the keygen into github: https://github.com/settings/ssh/new
Call the title whatever you want.

You can now test it by cloning a repository, go to any github repo and copy the SSH of the repo. (For example, this one is `git@github.com:So1ene/my-setup.git`)
Navigate to your desktop in powershell:
```powershell
cd ~/Desktop
```
And clone it there so you can easily delete it after. The first time you will have to confirm, type `yes`
```powershell
git clone <paste SSH KEY>
```
Here are some useful git commands if you ever feel stuck: https://dzone.com/articles/top-20-git-commands-with-examples

Now that you can use git on your command line using SSH, you should now also get the github CLI because it is better in general.
https://cli.github.com/

All you have to do is install it from the link above and do `gh auth login` in your terminal and follow the instructions.



## Windows Terminal

Download and install Windows Terminal from the Microsoft Store

Open it then click on the arrow next to the tab and you should see "Settings". Click on that, then on the left you should see 'profiles' click on the first one (Windows Powershell) and in the field called 'command line' add `-noLogo` so that it looks like this `powershell.exe  -noLogo`.

You can also change the starting directory if you like. I set mine to my work folder so that it is much easier to use every day. `"startingDirectory": "C:/whatever/you/want"`.
Save settings and close.


## Fancy your Terminal

I use oh-my-posh! It's a windows version of oh-my-zsh, this will make your windows terminal look like linux zsh terminal!
https://ohmyposh.dev/docs/pwsh
Open windows terminal **as administator**.

Run these commands:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
```powershell
Install-Module posh-git -Scope CurrentUser
```
Type Y for yes twice
```powershell
Install-Module oh-my-posh -Scope CurrentUser
```
```powershell
Set-PoshPrompt
```
Your terminal will look weird for a while.
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
Set-PoshPrompt -Theme robbyrussel
function home { cd ~ }
function desktop { cd ~/Desktop }
function documents { cd ~/Documents }
function downloads { cd ~/Downloads }
clear
```
Restart your terminal

I added functions to quick-travel between places in the command line, feel free to add your own. That way you can just type "`desktop`" and you will easily change directory to your desktop from anywhere. For example, I work with WAMP and I would like a shortcut to the WAMP `www` folder which is a pain to navigate to, so I open the profile with `notepad $PROFILE` and add this line before `clear`:
```
function wamp { cd C:/wamp64/www }
```
That way I can simply type "wamp" and it will navigate me to that folder.

You can also choose a different theme than RobbyRussell, but that is my favorite. 
Browse themes here: https://ohmyposh.dev/docs/themes/

If you like the RobbyRussell theme like I do but would rather see the whole file path instead of just the current folder name, you can easily change that in theme setting, navigate to `%UserProfile%\Documents\WindowsPowerShell\Modules\oh-my-posh\`, open the version folder, open the Themes folder, and then open the file `robbyrussel.omp.json` with VSCode and change this:
```
        {
          "type": "path",
          "style": "plain",
          "foreground": "#56B6C2",
          "properties": {
            "style": "folder"
          }
        },
```
to this:
```
        {
          "type": "path",
          "style": "plain",
          "foreground": "#56B6C2",
          "properties": {
            "style": "full"
          }
        },
```

You can also mess around with colors etc while you're in there if you want. I personally love the default colors of that theme.


## Visual Studio Code

I use Visual Studio Code because it has a built-in terminal and lots of really amazing extensions.

1. Download [Visual Studio Code](https://code.visualstudio.com/download) 
2. Download and install useful extensions

Here are the extentions I use as a web developer:
- Dark theme:
[An Old Hope Theme](https://marketplace.visualstudio.com/items?itemName=dustinsanders.an-old-hope-theme-vscode)
- Light theme just in case: 
[Newbie Light Color Theme](https://marketplace.visualstudio.com/items?itemName=lunakoly.newbie-light-color-theme)
- [Color Highlight](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)
- [CSS Peek](https://marketplace.visualstudio.com/items?itemName=pranaygp.vscode-css-peek)
- [ERB Helper Tags](https://marketplace.visualstudio.com/items?itemName=rayhanw.erb-helpers)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)
- [IntelliSense for CSS class names in HTML](https://marketplace.visualstudio.com/items?itemName=Zignd.html-css-class-completion)
- [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
- [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass)
- [Pytho](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Ruby on Rails](https://marketplace.visualstudio.com/items?itemName=hridoy.rails-snippets)
- [Sass](https://marketplace.visualstudio.com/items?itemName=Syler.sass-indented)
- [Sublime Text Keymap and Settings Importer](https://marketplace.visualstudio.com/items?itemName=ms-vscode.sublime-keybindings)


Restart VS Code.

Press `Ctrl ,` to go to settings, click extensions and click "Live sass compiler". Look for `Live Sass Compile › Settings: Formats` and click 'edit in settings.json' and change the save path to `"savePath": "~/.."` This will save the css file outside of the sass folder, wherever you place it. 
We also want browser support, so Look for `Live Sass Compile › Settings: Autoprefix` and click 'edit in settings.json' and look for `liveSassCompile.settings.autoprefix` and change it to this:
```
"liveSassCompile.settings.autoprefix": [
    "defaults",
    "> 1%",
    "last 2 versions"
]
```
Save the file and close it.

Now when you open a scss or sass file, on the bottom of the VS Code window there will be a 'Watch Sass' button, whenever you are coding in sass/scss you can compile it live by clicking on that button.

If you have PHP installed on your stsrem, press `Ctrl ,` to go to settings, type 'php' in the search bar and look for `PHP › Validate: Executable Path` and click 'edit in settings.json'.
Add in the path to php.exe (mine is `C:/wamp64/bin/php/php7.4.9/php.exe`)

Press `Ctrl K` then `Ctrl T` and it will open a list of your installed themes. Cycle through them with the arrow keys and choose one that you like!

In VS Code if you click on 'new terminal', a powershell terminal will appear with the same styling that you set up. Cool feature right?


You are now ready to code! You can click on the leftmost icons to travel between 'files', 'search', 'source control' (this is git! you can view your changes here), 'run', and 'extensions'.
