# Pacman Package Manager

## Update all packages
~~~
sudo pacman -Syu
~~~

## Update specific package
~~~
sudo pacman -Syu <package-name>
~~~

## Check if a package is installed
~~~
pacman -Ss <packagename or string> | grep installed
~~~

## Search for package
~~~
sudo pacman -Ss <keyword>
~~~

## Repair PGP (fix is corrupted (invalid or corrupted package (PGP signature))
~~~
sudo pacman -S archlinux-keyring
~~~

## Repair keychain (fix error Keyring not writeable)
~~~
sudo pacman-key --init
sudo pacman-key --populate
sudo pacman-key --refresh-keys
sudo pacman -Sy archlinux-keyring
~~~

## Install a package
~~~
sudo pacman -Syy <keyword>
~~~
