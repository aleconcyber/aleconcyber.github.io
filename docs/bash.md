# Useful Bash commands

## Find text in files easily
~~~
grep * string
~~~

## Find a file containing specific text
~~~
grep -rnw '/path/to/somewhere/' -e 'pattern'
~~~

## Identify the Linux distribution
~~~
cat /proc/version
~~~
~~~
lsb_release -a
~~~

## ID the RAM
~~~
sudo dmidecode --type 17
~~~

## Set Timezone
~~~
sudo timedatectl set-timezone Australia/Sydney
~~~


# APT Commands

## Update list of packages (check for new versions)
~~~
sudo apt-get update
~~~

## Upgrade installed packages
~~~
sudo apt upgrade
~~~

## Perform major updates
~~~
sudo apt full-upgrade
~~~

## Remove unneeded or unused packages (in order to save disk space)
~~~
sudo apt --purge autoremove
~~~


# Pacman Commands

## Update all packages
~~~
sudo pacman -Syu
~~~

## Update specific package
~~~
sudo pacman -Syu <package-name>
~~~

## Search for package
~~~
sudo pacman -Ss <keyword>
~~~