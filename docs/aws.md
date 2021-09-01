# Common AWS commands

## Login using saved credentials
~~~
eval $(aws ecr get-login --no-include-email | sed 's|https://||')
~~~

