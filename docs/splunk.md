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
