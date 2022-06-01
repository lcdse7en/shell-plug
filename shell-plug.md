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


