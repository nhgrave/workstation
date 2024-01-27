# Install Node.js

You can install Node only, or you can install [NVM](./index.md#install-nvm) to manage Node versions on your machine.

## Install for Windows

Download and install the latest LTS version listed on the [Node.js download page](https://nodejs.org/en/download).

## Install for Linux

Install the Node.js package for Ubuntu:

```bash
sudo apt update
sudo apt install nodejs
node -v
sudo apt install npm
```

## Install NVM

Another way to install Node.js that is particularly flexible is to use NVM, the Node Version Manager. This piece of software allows you to install and maintain many different independent versions of Node.js and their associated Node packages simultaneously. You can find more information [here](https://github.com/nvm-sh/nvm).

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Append the NVM source string to your profile file (`.bash_profile`, `.bashrc`, `.profile`, `.zshrc`, or `.zlogin`) if it doesn't have it.

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Now you can install the latest Node LTS version using NVM:

```bash
nvm install --lts
```
