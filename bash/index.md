# Bash

## Beautiful terminal

Add the following to your `~/.bashrc` to show the current time, elapsed command duration, and Git branch in your prompt.

```bash
# Functions to calculate elapsed time
function timer_start {
  timer=${timer:-$SECONDS}
}

function timer_stop {
  timer_diff=$(($SECONDS - $timer))
  unset timer
}

# Trap to execute before and after each command
trap 'timer_start' DEBUG
PROMPT_COMMAND='timer_stop'

# Git branch function
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# PS1 configuration
# \t = Current time (HH:MM:SS)
# ${timer_diff}s = Elapsed time in seconds
export PS1="\[\e[90m\][\t - \${timer_diff}s] \[\e[94m\]\u@\h \[\e[32m\]\w\[\e[33m\]\$(parse_git_branch)\[\e[m\]\n$ "
```

## Commands

Add the following functions to `~/.bash_profile`, `~/.bashrc`, or `~/.zshrc`.

### each

Runs a command inside every subdirectory of the current folder. Useful for running the same Git command across multiple projects.

```bash
each () {
  for f in $(ls -d */); do
    echo "--> $f"
    cd "$f"
    "$@"
    cd ..
  done
}
```

Example usage:

```bash
each git pull
each git status
```
