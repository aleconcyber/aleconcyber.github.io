# Splunk

# Commands
~~~
dedup
~~~
Removes duplicates

## Stats functions
~~~
count
sum
avg
~~~

## Chart commands
~~~
| chart count over rowfieldname_name by columnfieldname
~~~
over (x) (can be named)
by (y) (numeric)

## Usenull & Useother
~~~
usenull=f 
~~~
removes the NULL values from a chart
but better to imply blah=* to remove blanks earlier
~~~
useother=f  
~~~
removes the OTHER values from a chart
limit=10 is default/max limit=0 is all 

## Clustering chart timelines
~~~
span=12h
~~~
clusters the normal 24hr to 12hr

~~~
timewrap=7d
~~~~
makes weekly series

# Other Gotchas
field names are case sensitive, values are not
field values from a Lookup are case sensitive
boolean are  UPPER (AND OR)
