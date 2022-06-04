### Shell Plug

#### 1.zsh-autosuggestions
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

```zshrc
plugins=(
    zsh-autosuggestions
)
```

#### 2.zsh-syntax-highlighting
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

```zshrc
plugins=(
    zsh-syntax-highlighting
)
```

#### 3.autojump
```bash
git clone https://github.com/wting/autojump.git

cd autojump
./install.py
```

#### 4.Oh-My-Zsh
```bash
sh -c "$(curl -fsSL https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh)"

# set ohmyzsh-themes
cd ~/.oh-my-zsh/themes && ls
```

```zshrc
ZSH_THEME="robbyrussell"
ZSH_THEME="ys"
ZSH_THEME="strug"
```

#### 5.translation
```bash
sudo apt install nodejs
sudo npm install fanyi -g
```
`nvim ~/.config/fanyi/.fanyirc`
```json
{
  "iciba": true,
  "youdao": true,
  "dictionaryapi": false,
  "say": false,
  "color": true
}
```

```zshrc
alias f = 'fanyi'
```

#### 6.http.server
```zshrc
alias server="python3 -m http.server -d /home/se7en/aSe7en"
```

port: `8000`

IP: `localhost:8000`

IP: `192.168.1.6:8000`

```bash
server
```

#### 7.fzf
```bash
git clone --depth=1 https://github.com/junegunn/fzf.git ~/.fzf

cd ~/.fzf
./install

sudo apt isntall fzf
```

#### 8.zshrc
```zshrc
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH=$HOME/.oh-my-zsh

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
# ZSH_THEME="robbyrussell"
# ZSH_THEME="crcandy"
ZSH_THEME="ys"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in $ZSH/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment one of the following lines to change the auto-update behavior
# zstyle ':omz:update' mode disabled  # disable automatic updates
# zstyle ':omz:update' mode auto      # update automatically without asking
# zstyle ':omz:update' mode reminder  # just remind me to update when it's time

# Uncomment the following line to change how often to auto-update (in days).
# zstyle ':omz:update' frequency 13

# Uncomment the following line if pasting URLs and other text is messed up.
# DISABLE_MAGIC_FUNCTIONS="true"

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# You can also set it to another string to have that shown instead of the default red dots.
# e.g. COMPLETION_WAITING_DOTS="%F{yellow}waiting...%f"
# Caution: this setting can cause issues with multiline prompts in zsh < 5.7.1 (see #5765)
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(
    git
    sudo
    zsh-syntax-highlighting
    zsh-autosuggestions
    z
    autojump
    # zsh_reload
    command-not-found
    tmux
)

# export EDITOR='nvim'
source $ZSH/oh-my-zsh.sh


# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"

function zle-keymap-select {
	if [[ ${KEYMAP} == vicmd ]] || [[ $1 = 'block' ]]; then
		echo -ne '\e[1 q'
	elif [[ ${KEYMAP} == main ]] || [[ ${KEYMAP} == viins ]] || [[ ${KEYMAP} = '' ]] || [[ $1 = 'beam' ]]; then
		echo -ne '\e[5 q'
  fi
}
zle -N zle-keymap-select

# Use beam shape cursor on startup
echo -ne '\e[5 q'

# Use beam shape cursor for each new prompt.
preexec() {
	echo -ne '\e[5 q'
}

_fix_cursor() {
	echo -ne '\e[5 q'
}
precmd_functions+=(_fix_cursor)

KEYTIMEOUT=1

# fzf
# export FZF_COMPLETenv_TRIGGER='\'

source ~/.config/zsh/aliases.zsh
source ~/.config/zsh/fzf.zsh




bindkey ',' autosuggest-accept
fpath+=${ZDOTDIR:-~}/.zsh_functions

[ -f ~/.fzf.zsh ] && source ~/.fzf.zsh

```

#### 9.aliases.zsh
```zsh
alias ra=ranger
alias c=clear
alias e=exit
# alias zsh="nvim ~/.zshrc"
alias vim=nvim
alias sudo="sudo -E"
alias tmux="sudo tmux"
alias lg=lazygit
alias cdiff=colordiff
alias s=neofetch
alias f="fanyi"
alias zshrc="nvim ~/.zshrc"
alias push="cd ~/aSe7en/'github upload files'/master/ & git add \. & git status && git commit -m 'first' & git status & git push"
alias cpa="sudo rsync -rvu /home/se7en/aSe7en/cpa /media/se7en/'Sumsang SSD2'/se7en/aSe7en/"
alias work="sudo rsync -rvu /home/se7en/work/'make-account' /media/se7en/'Sumsang SSD2'/se7en/WORK/"
alias se="sudo rsync -rvu /home/se7en/aSe7en/ /media/se7en/'Sumsang SSD2'/se7en/aSe7en"
alias server="python3 -m http.server -d /home/se7en/aSe7en"
alias gitpush='gitpush(){ git add . ;git status; git commit -m "first"; git push;};gitpush'
alias da='da(){ date;pwd;who|wc -l;};da'

```

#### 10.fzf.zsh
```zsh
export FZF_DEFAULT_OPTS='--bind=ctrl-t:top,change:top --bind ctrl-j:down,ctrl-k:up'
#export FZF_DEFAULT_OPTS='--bind ctrl-e:down,ctrl-u:up --preview "[[ $(file --mime {}) =~ binary ]] && echo {} is a binary file || (ccat --color=always {} || highlight -O ansi -l {} || cat {}) 2> /dev/null | head -500"'
#export FZF_DEFAULT_COMMAND='ag --hidden --ignore .git -g ""'
export FZF_DEFAULT_COMMAND='fd'
export FZF_COMPLETION_TRIGGER='\'
export FZF_TMUX=1
export FZF_TMUX_HEIGHT='80%'
export fzf_preview_cmd='[[ $(file --mime {}) =~ binary ]] && echo {} is a binary file || (ccat --color=always {} || highlight -O ansi -l {} || cat {}) 2> /dev/null | head -500'


_fzf_fpath=${0:h}/fzf
fpath+=$_fzf_fpath
autoload -U $_fzf_fpath/*(.:t)
unset _fzf_fpath

fzf-redraw-prompt() {
	local precmd
	for precmd in $precmd_functions; do
		$precmd
	done
	zle reset-prompt
}
zle -N fzf-redraw-prompt

zle -N fzf-find-widget
bindkey '^p' fzf-find-widget

fzf-cd-widget() {
	local tokens=(${(z)LBUFFER})
	if (( $#tokens <= 1 )); then
		zle fzf-find-widget 'only_dir'
		if [[ -d $LBUFFER ]]; then
			cd $LBUFFER
			local ret=$?
			LBUFFER=
			zle fzf-redraw-prompt
			return $ret
		fi
	fi
}
zle -N fzf-cd-widget
bindkey '^t' fzf-cd-widget

fzf-history-widget() {
	local num=$(fhistory $LBUFFER)
	local ret=$?
	if [[ -n $num ]]; then
		zle vi-fetch-history -n $num
	fi
	zle reset-prompt
	return $ret
}
zle -N fzf-history-widget
bindkey '^R' fzf-history-widget

fif() {
  if [ ! "$#" -gt 0 ]; then echo "Need a string to search for!"; return 1; fi
  rg --files-with-matches --no-messages "$1" | fzf --preview "highlight -O ansi -l {} 2> /dev/null | rg --colors 'match:bg:yellow' --ignore-case --pretty --context 10 '$1' || rg --ignore-case --pretty --context 10 '$1' {}"
}

find-in-file() {
	grep --line-buffered --color=never -r "" * | fzf
}
zle -N find-in-file
bindkey '^f' find-in-file

```



