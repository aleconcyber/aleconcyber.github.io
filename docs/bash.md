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

##List file attributes
~~~
lsattr filename
~~~

A = atime record not updated
S = synchronous changes to disk
a = append write mode only
i = immutable
J = journaled, info written to ext3 journal before file
t = tail-merge not allowed
d = dump, no more candidate for dump process
u = undeletion (data saved when removed)

##Show current working directory
~~~
cwd
~~~

##Benchmark mounted media (read & write on mmcblk0p1)
~~~
sync && dd if=/dev/zero of=/run/media/mmcblk0p1/testfile bs=1000M count=1 oflag=dsync && sync
sync && dd if=/run/media/mmcblk0p1/testfile of=/dev/null bs=1000M count=1 iflag=dsync && sync
~~~
