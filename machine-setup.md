Swap caps lock and esc
    osx: PC Keyboard Hack (https://pqrs.org/macosx/keyremap4macbook/pckeyboardhack.html)
    nix: remap keys in whatever that config file is

osx: install homebrew (http://brew.sh/)
    TODO explain package managers for neophytes
    we use homebrew to install our own personal versions of software (git, vim, python).
    system software will still access system defaults in /usr/bin/, and the last thing we 
    should do is change permissions of system installed software.
    explain how some people prefer to (only) use virtualenv or vagrant to manage their software rather 
    than messying up their local env -- I find this ill suited for quick exploration.
    NOTE: /usr/local/bin/ by default comes after /usr/bin/ in $PATH. I fix this in my dotfiles described
    below. Before running any of the installed packages below, make sure to set /usr/local/bin/ to come 
    before /usr/bin/, which I do in my dotfiles.

python 2.7.x
    brew install python
        this gives you pip and setuptools

python 3.x
    brew install python3
        as of writing, the brew is python 3.3.5 including pip and setuptools, but soon will upgrade to 3.4
    info: https://github.com/Homebrew/homebrew/wiki/Homebrew-and-Python

good pip packages (pip install <package>)
    virtualenv, ipython, matplotlib, scipy, numpy, pandas
    link to homepages and good tutorials

vim
    brew install vim
    7.4 which allows python in .vimrc files and Im sure many other cool things.
    sys default is 7.3. may need to restart your shell after installing.

git
    brew install git
        the brand new version 1.9.0 as of writing this, instead of apples 1.8.5.2
    git email and username
        git config --global user.name "Jamis Johnson"
        git config --global user.email jamismanwaring@gmail.com
    git colors
        git config --global color.ui true
    git aliases
        git config --global alias.co checkout
        git config --global alias.st status
        git config --global alias.br branch
        git config --global alias.ci commit
    editor
        git config --global core.editor /usr/bin/vim
        something related to .vimrc is causing vim to close with a non-zero status and 
        therefore git commits fail.  to save ourselves potential future hassle of 
        potentiall rewriting our commit msg everytime we change our .vimrc, 
        lets have git use the systems def vim
    more: http://git-scm.com/book/en/Git-Basics-Tips-and-Tricks

dotfiles 
    terminal coloring (iTerm and 256 colors n shit)
        * base16: http://chriskempson.github.io/base16/ , https://github.com/chriskempson/base16
        * base16-iterm2: https://github.com/chriskempson/base16-iterm2 . Describe *why*; github repo describes steps.
        * base16-vim described in next section
        * change your iterm to be 256 colors (http://kevin.colyar.net/2011/01/pretty-vim-color-schemes-in-iterm2/?utm_source=rss&utm_medium=rss&utm_campaign=pretty-vim-color-schemes-in-iterm2)
        * test 256 colors with https://raw.github.com/incitat/eran-dotfiles/master/bin/terminalcolors.py. there may be a better test out there.
    vimrc
        * vimtutor if necessary
        * explain details of vimrc file
    vundle
        * vundle is a package manager for vim.
        * git clone and install vundle into ~/.vim/bundle (https://github.com/gmarik/Vundle.vim)
        * run :BundleInstall in vim if you have my dotfiles
        * copy base16-vim colors into ~/.vim/colors/
        * pick which one you want from base16 preview site, change that in your .vimrc file, and load the corresponding iterm2 preset
    bashrc
        * /usr/bin/local/ is set to come before /usr/bin/. changing in user config wont affect system calls
        * explain details of bashrc file
    profile
        * osx: explain source bashrc. required for iterm2 to find .bashrc file.
    tmux
        * what exactly is a terminal multiplexer Jamis? well let me tell you.
        * explain details of tmux file

TODO
    format this page to be readable as processed markdown (not just in vim)
    ruby, rvm & bropages
    dotfiles
        fix dotfiles install
            remove os and pip install / drastically simplify
        remove auto folding from .vimrc
        fix coloring. ensure works for os x (iterm2 and terminal) and ubuntus default terminal.
        fix tmux
    tmux
    vagrant
    virtualbox?
    ssh keys
        github
        vbox
    terminal coloring scheme
