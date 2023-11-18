# Git config

Setting up Git on the local machine:

User Setup

```sh
git config --global user.name "Fulano de Tal"
git config --global user.email fulanodetal@example.com
```

Color Setup

```sh
git config --global color.ui auto # or true
git config --global color.status auto
git config --global color.branch auto
git config --global color.interactive auto
git config --global color.diff auto
git config --global color.grep auto
```

VSCode Setup

```sh
git config --global core.editor "code --wait"
```

Diff Pager Setup

```sh
git config --global core.pager cat
```

Alias Setup

```sh
git config --global alias.co checkout
git config --global alias.st status
git config --global alias.br branch
git config --global alias.su "submodule update --init --recursive"
git config --global alias.clean-br '!f() { git branch | grep -v "*" | xargs git branch -D; }; f'
```

Update staging branch with the develop branch (remote)

```sh
git push -f origin develop:homolog
```

Delete a remote branch

```sh
git push origin –delete BRANCH
```

Generate a diff file

```sh
git diff > changes.patch
```

Load a diff file

```sh
git apply changes.patch
```

Remove cached files from gitignore

```sh
git rm --cached `git ls-files -i -c --exclude-from=.gitignore`
```
