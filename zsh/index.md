# INstall ZSH

First of all, update your packages

```bash
sudo apt update && sudo apt upgrade
```

then install zsh

```bash
sudo apt install zsh

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

check your zsh installed version

```bash
zsh --version
```

make zsh the default shell

```bash
chsh -s $(which zsh)
```

## Install Powerlevel10k

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```

set theme to your `~/.zshrc`

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

reload zsh and configure powerlevel or type `p10k configure`

## Install autosuggestions

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

add plugin to your `~/.zshrc`

```bash
plugins=(... zsh-autosuggestions)
```

## Install syntax-highlighting

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

add plugin to your `~/.zshrc`

```bash
plugins=(... zsh-syntax-highlighting)
```
