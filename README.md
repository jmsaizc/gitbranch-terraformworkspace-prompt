# Show git branch and terraform workspace in ubuntu bash prompt

Add git branch and terraform workspace in bash command prompt

Add this to your bash.rc:

```
function git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

function terraform_prompt()
{
    if [ -d .terraform ]; then
        workspace="$(command terraform workspace show 2>/dev/null)"
        echo " (${workspace})"
    fi
}

export PS1="\e[1;32m[\u@\h \[\033[01;32m\]\w\[\033[33m\]\$(git_branch)\$(terraform_prompt)\[\033[00m\] $ "
```
after run in terminal:
```
source .bashrc
```
