Quick and relatively painless guide for programmer neophytes of all shapes and sizes to help 
setup a solid dev machine an OS X.

### TODO
- [x] format this doc to actual markdown
- [ ] don't just keep doing an outline, actually write shit.
- [ ] haskell and ghci. aw yeah.
- [ ] iTerm2
- [ ] ruby, rvm & bropages
- dotfiles
  - fix dotfiles install
    - [ ] remove os and pip install / drastically simplify
  - [x] remove auto folding from .vimrc
  - [x] fix coloring. ensure works for os x (iterm2 and terminal) and ubuntus default terminal.
  - [x] fix tmux
- [ ] tmux
- [ ] vagrant
- [ ] virtualbox?
- [ ] ssh keys
  - [ ] github
  - [ ] vbox
- [ ] terminal coloring scheme
- [ ]find better 256-color terminal test?
- [ ]add ubuntu

### Swap caps lock and esc
osx: PC Keyboard Hack (https://pqrs.org/macosx/keyremap4macbook/pckeyboardhack.html) 
linux: remap keys in whatever that config file is. maybe I should wait to describe a ubuntu/linux setup.

### osx: install homebrew (http://brew.sh/)
- TODO explain package managers
- we use homebrew to install our own personal versions of software (git, vim, python).
system software will still access system defaults in /usr/bin/, and the last thing we 
should do is change permissions of system installed software.  explain how some people 
prefer to (only) use virtualenv or vagrant to manage their software rather 
than messying up their local env -- I find this ill suited for quick exploration.
- NOTE: /usr/local/bin/ by default comes after /usr/bin/ in $PATH. I fix this in my dotfiles described
below. Before running any of the installed packages below, make sure to set /usr/local/bin/ to come 
before /usr/bin/, which I do in my dotfiles.

### :boom Software :boom
#### python 2.7.x
`brew install python`
this also installs pip and setuptools and/or virtualenv

#### python 3.x
`brew install python3`
As of writing, the brew is python 3.3.5 including pip and setuptools/virtualenv, but 
[soon will it will be 3.4](https://github.com/Homebrew/homebrew/wiki/Homebrew-and-Python) 
which has pip and virtualenv built in.
TODO comment on --user and how pip is installed as user, not as superuser.

#### Good Pip Packages (`pip install <package>`)
virtualenv, ipython, matplotlib, scipy, numpy, pandas
link to homepages and good tutorials

#### vim
`brew install vim`
downloads vim 7.4 which allows python in .vimrc files and I'm sure many other cool things 
that I don't know about.
OS X default is 7.3. You'll need to restart or open a new shell after installing.

#### git
`brew install git`
As of writing downloads version 1.9.0, instead of Apple's 1.8.5.2
Configure git.
- Email and username. Especially important for committing to Github.
```git
git config --global user.name "Jamis Johnson"
git config --global user.email jamismanwaring@gmail.com
```
- Colors
```git
git config --global color.ui true
```
- Aliases
```git
git config --global alias.co checkout
git config --global alias.st status
git config --global alias.br branch
git config --global alias.ci commit
```
- Default Editor
```git
git config --global core.editor /usr/bin/vim
```
Something related to .vimrc + brew's vim7.4 is causing vim to close with a non-zero 
status and therefore git commits fail. To save ourselves from the future hassle 
of rewriting our commit messages everytime we change our .vimrc, let's have git 
use the system's default vim
[Git Tips & Tricks](http://git-scm.com/book/en/Git-Basics-Tips-and-Tricks)

### dotfiles 
#### iTerm (iTerm and 256 colors n shit)
- [base16 github](https://github.com/chriskempson/base16)
- [live preview](http://chriskempson.github.io/base16/)
- [base16-iterm2](https://github.com/chriskempson/base16-iterm2). Describe why we need these *and* vim colors.
- base16-vim described in next section
- [Change your iTerm to be 256 colors](http://kevin.colyar.net/2011/01/pretty-vim-color-schemes-in-iterm2/?utm_source=rss&utm_medium=rss&utm_campaign=pretty-vim-color-schemes-in-iterm2)
- Ensure that 256 colors are working. Download [this file](https://raw.github.com/incitat/eran-dotfiles/master/bin/terminalcolors.py)
and run `python terminalcolors.py`. If you see colors all the way down then your terminal is configured for 256 colors.

#### vimrc
- vimtutor if necessary
- explain details of vimrc file
#### vundle
- vundle is a package manager for vim.
- git clone and install vundle into ~/.vim/bundle (https://github.com/gmarik/Vundle.vim)
- run :BundleInstall in vim if you have my dotfiles
- copy base16-vim colors into ~/.vim/colors/
- pick which one you want from base16 preview site, change that in your .vimrc file, and load the corresponding iterm2 preset
#### bashrc
- /usr/bin/local/ is set to come before /usr/bin/. changing in user config wont affect system calls
- explain details of bashrc file
#### profile
- osx: explain source bashrc. required for iterm2 to find .bashrc file.
#### tmux
- what exactly is a terminal multiplexer Jamis? well let me tell you.
- explain details of tmux file

