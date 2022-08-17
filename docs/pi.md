# Raspberry Pi Commands

## Install VPN Server
~~~
curl -L https://install.pivpn.io | bash
~~~

## Add a user
~~~
sudo pivpn add
~~~

## Remove a user
~~~
sudo pivpn remove
~~~

## Show QR for scanning in Wireguard App
~~~
pivpn -qr myusername
~~~
