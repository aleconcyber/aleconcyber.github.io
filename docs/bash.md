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
