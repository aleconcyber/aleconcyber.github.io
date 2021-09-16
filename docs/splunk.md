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

## Eval commands
~~~
| eval MegaBytes = round(Bytes/1024/1024,2)
~~~
create a new field called MegaBytes which turned bytes into the values

~~~
eval discount = round(((sale_price - list_price) / list_price)*100)
~~~
another example of math done on an field value

### ToString
~~~
eval numerField = "$" + tostring(price_value,"commas")
~~~
make numbers into dollar values

~~~
eval if (condition, true, false)
~~~
A/B test in the condition, processing down in 2nd and 3rd arguments.

~~~
eval fieldName=case(status=200, "OK", status=404, "Not Found")
~~~
if an event doesn't fit any cases, no value will return. To fix this:

~~~
eval fieldName=case(status=200, "OK", status=404, "Not Found", true(), "Something Else")
~~~
Can also add ranges with AND

~~~
eval fieldName=case(status=>=199 AND status<=201, "OK", status=404, "Not Found", true(), "Something Else")
~~~
each case can have AND statements and there can be as many cases and desired.

eval can be used inside a transform eg. stats
~~~
| stats count(eval(status<300)) as "Success"
count(eval(status>=400 AND status<500)) as "Client Error",
count(eval(status>500)) as "Server Error"
~~~
Note the as is needed during the transform as well as the double-quotes

## Search commmand
~~~
| search Count > 1
~~~
locate all results with Count value higher than 1

## Where command
~~~
| where blah > blah
| where blah!="IgnoreThis"
~~~
filter results

~~~
| where isnotnull(INeedThisValue)
~~~
ignore missing values

~~~
| where isnull(IDontNeedThisValue)
~~~
only missing values

~~~
| fields - DropThis
~~~~
ignore fields 

~~~
| sort -Name
~~~
Sort (decending) by Name

~~~
| fillnull value="100"
~~~
fills nulls with 100, defaults to 0 without value field

Wildcards
~~~
| where blah like "Hell_"
~~~
Matches one ( Hello, Hellp )
~~~
| where blah like "Hell%"
~~~
Matches many ( Hello, Hellotopia )

## Fieldformat (Display-level alternative to eval)
~~~
fieldformat numerField = "$" + tostring(price_value,"commas")
~~~
Does not modify the underlying data, just modifies the displayed output (so sorting would still work)

## Chart commands
~~~
| chart count over rowfieldname_name by columnfieldname
~~~
over (x) (can be named)
by (y) (numeric)

~~~
addtotals
~~~
adds totals and creates a new field with totals

### Timechart
~~~
| timechart span=1d count as columnfieldname
~~~

### Add trends
~~~
|trendline sma2(failures) as trend
~~~
Simple Moving Average

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
~~~
makes weekly series

## Adding IP location information
~~~
| iplocation src_ip
~~~
Where src_ip is the field containing IP address

# Mapping
Choropleth maps require a geo-map eg.
~~~
| chart count by StateFieldName
| geom geo_us_states featureIdField=StateFieldName
~~~

Cluster Maps can use IP Geolocation
~~~
| iplocation ipFieldName
| geostats count by ipFieldName
~~~

# Visualisations
gauge with color ranges
~~~
| gauge FieldName 10 20 40 60 80 100
~~~

# Other Gotchas
field names are case sensitive, values are not

field values from a Lookup are case sensitive

boolean are  UPPER (AND OR)
