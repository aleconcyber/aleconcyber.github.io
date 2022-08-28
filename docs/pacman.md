# Pacman Package Manager

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

## Repair keychain (fix error Keyring not writeable)
~~~
pacman-key --init
pacman-key --populate
pacman-key --refresh-keys
pacman -Sy archlinux-keyring
~~~

## Install a package
~~~
sudo pacman -Syy <keyword>
~~~
