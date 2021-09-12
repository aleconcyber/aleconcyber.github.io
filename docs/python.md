# Python

## Variables
~~~
variablename = 10
~~~
Declare and set value

~~~
type(variablename)
~~~
Output type (string, float, list, integer, boolean) 

## Write output
~~~
print "string"
print (variablename)
print "string" + str(variablename) + "another string"
~~~

## Mathematical operations
~~~
1 + 2
1 / 2
1 * 2
1 - 2
~~~
Standard algebra

~~~
5 % 3
~~~
Modulo: gives the remainder of 5 divided by 3 (2)

~~~
4 ** 3
~~~
Four to the power of 3 (64)

## Indexing and slicing
~~~
indexname = ['a', 'b', 'c', 'd']
~~~
Build and populate a list

~~~
del(indexname[1])
~~~
Remove the second list object (b)
 
~~~
print(indexname[1:3])
~~~
Output second and third index value ( b, c )

~~~
print(indexname[2:])
~~~
Output third to final index values ( c, d )

~~~
print(indexname[:1])
~~~
Output first values ( a )

~~~
listname[start:end]
~~~
Start is selected but end is not (only the entry prior)

###Other info
Lists can contain other lists and can be of mixed object types

## Joining multiple commands together
~~~
Command1; Command2
~~~
The semicolon acts as a new line separator
