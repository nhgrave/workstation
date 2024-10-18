# Bash

Past this code in `~/.bash_profile` or `~/.zprofile`

EACH - Method to execute a command for all folders. E.g.: each git pull

```sh
each () {
 for f in `ls`; do
   echo "--> $f"
   cd $f
   $*
   cd ..
 done
}
```
