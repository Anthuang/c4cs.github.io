---
---

alias
-------

`alias` is a command to create shortcut to commands and applications in the terminal.

~~~bash
$ alias l="ls"
$ l
Documents  Downloads  Music     Public     Videos
Desktop    Pictures   Templates
~~~

<!--more-->

### Useful Options / Examples

#### Usage
Things to note: when using alias, make sure that there is no space around the equal sign.
~~~bash
$ alias l = "ls"
alias l='ls -CF'
bash: alias: =: not found
~~~
Another thing to note is that aliases would overwrite existing commands. For example:
~~~bash
$ alias ls="git status"
$ ls
On branch master
Your branch is up-to-date with 'origin/master'.
~~~
Also, aliases are temporary to the current shell. To make the aliases permanent, please refer to the section below on making alises permanent.

#### Examples
The above examples do not make much sense, since they simplify a two character command. The following examples show how alias can save you a lot of time.

~~~bash
$ alias s="git status"
$ s
On branch master
Your branch is up-to-date with 'origin/master'.
~~~
This shows that you can alias commands with multiple words.

~~~bash
$ alias gdesk="cd ~/Desktop"
$ pwd
/home/user/Desktop
~~~
One thing to be careful about is if you alias the cd command without using the ~, your alias might not always work. For example:
~~~bash
$ alias gdesk="cd Desktop"
bash: cd: Desktop: No such file or directory
~~~

#### Making aliases permanent
If you just run the alias command from the shell, it would last for the duration of the shell (until the shell is closed). To make the aliases permanent, we can just tell the shell to run these commands when the shell starts.

For people who are relatively new to this, we can do this easily. Careful, for people with code already in the .bashrc file, you should instead use an editor to edit .bashrc. So, instead of "cat >" you should use "vim" or your editor of choice.
~~~bash
$ cat > ~/.bashrc
alias gits="git status"
(press control-D here)
$ cat ~/.bashrc
alias gits="git status"
$ source ~/.bashrc
~~~
The last line just tells the shell to source the file in the current session. The bashrc file is automatically sourced whenever the shell starts. Now, whenever you open a new shell, your aliases are ready for you.

For people who know how to work with .rc files (.bashrc), the best way to create permanent aliases is to create a .aliases file and then source it in your .rc file. For example, you should have this in your bashrc:
~~~bash
if [ -f ~/.aliases ]; then
    . ~/.aliases
fi
~~~
This would source your .aliases file if it exists. And in your .aliases file you should just write all your aliases.