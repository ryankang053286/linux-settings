# Linux Settings
## 1.Settings Bash  

zsh is a powerful shell, install your zsh, and change your shell to zsh, please see zsh instructions. Install oh-my-zsh plugin is easier way to configure your zsh.  
[zsh](https://github.com/zsh-users/zsh.git)   
```
wget -O zsh.tar.xz https://sourceforge.net/projects/zsh/files/latest/download   
mkdir zsh && unxz zsh.tar.xz && tar -xvf zsh.tar -C zsh --strip-components 1   
cd zsh   
./configure --prefix=$HOME  
make  
make install  

```
[oh-my-zsh](git://github.com/robbyrussell/oh-my-zsh.git)  
```
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc  
source ~/.zshrc  
```
### 1.1 ZSH PLUGINS   
[autojump](git://github.com/wting/autojump.git)   
```
cd autojump  
./install.py or ./uninstall.py  
```
copy following in your .zshrc  
`
[[ -s /home/rykang/.autojump/etc/profile.d/autojump.sh ]] && source /home/rykang/.autojump/etc/profile.d/autojump.sh  
`

Under WSL system, there is some safty restrictions about the plugins installed by oh-my-zsh, to fix the problems, with the following command help:   
```
compaudit | xargs chmod g-w,o-w /home/rykang/.oh-my-zsh/plugins  

```
## 2.VIM settings 
Install neo vim or vim8.0 to have a better experience. See vim or neovim installation.  
### 2.1 VIM Plugin Settings
vbundle clone the plugin repo using git, might needs proxy to clone the repo using following  

```
git config --global http.proxy xxx.xxx.xxx.xxx:8080  
```

or   
```
export HTTPS_PROXY=xxx.xxx.xxx.xxx:xxxx   
export HTTP_PROXY=xxx.xxx.xxx.xxx:xxxx   
```
1. *vbundle* plugin is awesome plugin that manages your plugins. Plug is another option.  

[vbundle](https://github.com/VundleVim/Vundle.vim)   

2. *nerdtree* Nerdtree plugin is for files browser looks like a tree   
```
Plugin 'preservim/nerdtree'
```
3. *vim-airline* status bar awesome indicate command line    
```
Plugin 'https://github.com/bling/vim-airline'
```
4. *auto-pairs* Generate brackets automatically   
```
Plugin 'jiangmiao/auto-pairs'
```
5. *parentheses* Parenthese different colors   
```
Plugin 'kien/rainbow_parentheses.vim'

let g:rbpt_colorpairs = [  
\ ['brown',       'RoyalBlue3'],   
\ ['Darkblue',    'SeaGreen3'],   
\ ['darkgray',    'DarkOrchid3'],   
\ ['darkgreen',   'firebrick3'],   
\ ['darkcyan',    'RoyalBlue3'],  
\ ['darkred',     'SeaGreen3'],  
\ ['darkmagenta', 'DarkOrchid3'],  
\ ['brown',       'firebrick3'],  
\ ['gray',        'RoyalBlue3'],  
\ ['darkmagenta', 'DarkOrchid3'],  
\ ['Darkblue',    'firebrick3'],  
\ ['darkgreen',   'RoyalBlue3'],  
\ ['darkcyan',    'SeaGreen3'],  
\ ['darkred',     'DarkOrchid3'],  
\ ['red',         'firebrick3'],  
\]  
let g:rbpt_max = 16
let g:rbpt_loadcmd_toggle = 0
au VimEnter * RainbowParenthesesToggle
au Syntax * RainbowParenthesesLoadRound
au Syntax * RainbowParenthesesLoadSquare
au Syntax * RainbowParenthesesLoadBraces
```
## Linux Shell  
### Proxy Setting
``` proxy shell settings  

#!/bin/zsh
if test $1="set"
then
	export HTTP_PROXY=$proxy
	export HTTPS_PROXY=$proxy
else
	unset HTTP_PROXY
	unset HTTPS_PROXY
fi

```
## GIT SETTINGS
`
git config --global core.excludesfile ~/.gitignore    
`
```
gitignore file   
cscope.out  
cscope.in.out  
cscope.po.out  
tags  
```
## TMUX SETTINGS
`tmux list-key` to list all bind keys  
`tmux list-buffers` to list tmux buffers  
`tmux show-buffer`  
`tmux save-buffer test.txt` save buffer to test.txt   
```
bind P paste-buffer
bind-key -T copy-mode v send-keys -X begin-selection
bind-key -T copy-mode y send-keys -X copy-selection
bind-key -T copy-mode C-v send-keys -X recTangle-toggle
```
##MAKESELF
[makeself](https://github.com/megastep/makeself)

## VIM 
d% delete the content of between brackets.  

## ENV variable settings
`export PATH=/usr/local/bin:$PATH`  
