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
~~~
ignore fields 

~~~
| sort -Name
~~~
Sort (decending) by Name

~~~
| fillnull value="100"
~~~
fills nulls with 100, defaults to 0 without value field

##IN command

~~~
DomainName IN (google.com, microsoft.com)
~~~
will show only events where the field name DomainName matches one of the array

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

## Stats command

Use stats to see results of a calculation, or group events on a field value. Use transaction to see events correlated together, or grouped by start and end values.

~~~
| stats list(FieldName1), values(FieldName2) by FieldName3
~~~
Creates a table where events are grouped by FieldName3 and list all of FieldName1 values available

## Transaction command
~~~
| transaction src_ip
~~~
grouping items by a common factor
this creates new fields Durtion and Event Count

~~~
| transaction src_ip dest_ip session_id
~~~
multiple fields used to form correlations, note that transaction has a max of 1000 events for one transaction

~~~
| transaction src_ip maxspan=100 maxpause=10 startswith="login" endswith="logout"
~~~
extended transaction command with extra specificity
startswith and endswith can search for terms, field values or evalutations

## Field Extraction

Works with RegEx or Delimiters
Creates Knowledge Objects

## Knowledge Objects
Data Interpretation
Classification
Enrichment
Normalization
Search Time Mapping

Typical naming convention
Group-Type-Platform-Category-Time-Description

## Aliases and Calc Fields

Aliases:
Settings > Fields > Aliases
Set Name (doesnt' matter)
Apply to sourcetype, source or host
Existing on Left, New name on the right (new fieldname).

Calculated Fields
Same process as Aliases but inlcude and eval expressions

## Macros
Settings > Advances Search > Search Macros
definition is the eval string
~~~
| `macroname`
~~~
If defining and argument, surround with $ ( $argumentname$ ) in the eval string

~~~
| `macroname("argument1","argument2")
~~~

Macroname should include name(2) if two arguments are needed

Validation Expression:
$arg1$="one" OR $arg1$="two"

Validation Message:
Use one or two

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

## Usenull and Useother
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

# Visualisations
gauge with color ranges
~~~
| gauge FieldName 10 20 40 60 80 100
~~~

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

# Other Gotchas
field names are case sensitive, values are not

field values from a Lookup are case sensitive

boolean are  UPPER (AND OR)
