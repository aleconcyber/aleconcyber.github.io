## MacOS ZSH Helpful commands

~~~
sw_vers
~~~
Show macOS version

~~~
chflags uchg /path/fileName
~~~
lock a file

~~~
chflags noschg /path/fileName
~~~
unlock a file

~~~
dscl . -ls /Users
~~~
list all users on the system including hidden ones

~~~
dscl . list /Groups
~~~
list all groups

~~~
who
~~~
display logged in user(s)

~~~
/Users/username/.zsh_history
~~~
bash history file for username

~~~
touch -a -m -t [[CC]YY]MMDDhhmm[.SS]
~~~
set timestamp for file (timestomp) (access, modified)

~~~
crontab -u username -l
~~~
list cron jobs for username

~~~
alias ls='ls -l -t'
~~~
set an alias for a command 

~~~
ls ~/Library/LaunchAgents
ls /Library/LaunchAgents
ls /Library/LaunchDaemons
ls /System/Library/LaunchAgents
ls /System/Library/LaunchDaemons
~~~
show all
User Agents
Global Agents/Daemons
System Agents/Daemons

~~~
diskutil list
~~~
list disks

~~~
df -h
~~~
show free disk space

~~~
mount
~~~
show mount points
